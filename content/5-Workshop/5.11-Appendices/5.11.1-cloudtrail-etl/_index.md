---
title : "CloudTrail ETL Code"
date: "2000-01-01"
weight : 01
chapter : false
pre : " <b> 5.11.1. </b> "
---

```python

import json
import boto3
import gzip
import base64
import os
from datetime import datetime

firehose = boto3.client('firehose')
s3 = boto3.client('s3')

FIREHOSE_STREAM_NAME = os.environ['FIREHOSE_STREAM_NAME']

def lambda_handler(event, context):
    """
    Processes CloudTrail logs from S3, extracts and enriches events,
    and sends them to Kinesis Firehose for delivery to S3.
    """
    
    for record in event['Records']:
        bucket = record['s3']['bucket']['name']
        key = record['s3']['object']['key']
        
        print(f"Processing CloudTrail log: s3://{bucket}/{key}")
        
        try:
            # Download and decompress CloudTrail log file
            response = s3.get_object(Bucket=bucket, Key=key)
            
            if key.endswith('.gz'):
                content = gzip.decompress(response['Body'].read())
            else:
                content = response['Body'].read()
            
            cloudtrail_data = json.loads(content)
            
            # Process each CloudTrail record
            processed_records = []
            for ct_record in cloudtrail_data.get('Records', []):
                processed_record = process_cloudtrail_record(ct_record)
                processed_records.append(processed_record)
            
            # Send to Firehose in batches
            send_to_firehose(processed_records)
            
            print(f"Successfully processed {len(processed_records)} CloudTrail events")
            
        except Exception as e:
            print(f"Error processing {key}: {str(e)}")
            raise

    return {
        'statusCode': 200,
        'body': json.dumps('CloudTrail ETL completed successfully')
    }

def process_cloudtrail_record(record):
    """
    Extracts and enriches CloudTrail event data.
    """
    
    user_identity = record.get('userIdentity', {})
    
    # Extract user information
    user_type = user_identity.get('type', '')
    username = extract_username(user_identity)
    
    # Determine event characteristics
    is_console_login = record.get('eventName') == 'ConsoleLogin'
    is_failed_login = is_console_login and record.get('errorMessage') is not None
    is_root_user = user_type == 'Root'
    is_assumed_role = user_type == 'AssumedRole'
    
    # Identify high-risk events
    high_risk_events = [
        'DeleteTrail', 'StopLogging', 'DeleteFlowLogs',
        'DisableLogging', 'PutBucketPolicy', 'DeleteBucketPolicy',
        'CreateAccessKey', 'DeleteAccessKey', 'UpdateAccessKey'
    ]
    is_high_risk_event = record.get('eventName') in high_risk_events
    
    # Identify privileged actions
    privileged_actions = [
        'CreateUser', 'DeleteUser', 'AttachUserPolicy', 'DetachUserPolicy',
        'CreateRole', 'DeleteRole', 'AttachRolePolicy', 'DetachRolePolicy',
        'PutUserPolicy', 'PutRolePolicy', 'DeleteUserPolicy', 'DeleteRolePolicy'
    ]
    is_privileged_action = record.get('eventName') in privileged_actions
    
    # Identify data access events
    data_access_events = ['GetObject', 'PutObject', 'DeleteObject']
    is_data_access = record.get('eventName') in data_access_events
    
    # Extract target resources from request parameters
    request_params = record.get('requestParameters', {})
    target_bucket = request_params.get('bucketName', '')
    target_key = request_params.get('key', '')
    target_username = request_params.get('userName', '')
    target_rolename = request_params.get('roleName', '')
    target_policyname = request_params.get('policyName', '')
    
    # Extract new resources from response elements
    response_elements = record.get('responseElements', {})
    new_access_key = ''
    new_instance_id = ''
    target_group_id = ''
    
    if isinstance(response_elements, dict):
        if 'accessKey' in response_elements:
            new_access_key = response_elements['accessKey'].get('accessKeyId', '')
        if 'instancesSet' in response_elements:
            instances = response_elements['instancesSet'].get('items', [])
            if instances:
                new_instance_id = instances[0].get('instanceId', '')
        if 'groupId' in response_elements:
            target_group_id = response_elements.get('groupId', '')
    
    # Build processed record
    processed = {
        'eventtime': record.get('eventTime', ''),
        'eventname': record.get('eventName', ''),
        'eventsource': record.get('eventSource', ''),
        'awsregion': record.get('awsRegion', ''),
        'sourceipaddress': record.get('sourceIPAddress', ''),
        'useragent': record.get('userAgent', ''),
        'useridentity': user_identity,
        'requestparameters': json.dumps(request_params) if request_params else '',
        'responseelements': json.dumps(response_elements) if response_elements else '',
        'resources': record.get('resources', []),
        'recipientaccountid': record.get('recipientAccountId', ''),
        'serviceeventdetails': json.dumps(record.get('serviceEventDetails', {})),
        'errorcode': record.get('errorCode', ''),
        'errormessage': record.get('errorMessage', ''),
        'hour': datetime.fromisoformat(record.get('eventTime', '').replace('Z', '+00:00')).strftime('%Y-%m-%d-%H') if record.get('eventTime') else '',
        'usertype': user_type,
        'username': username,
        'isconsolelogin': is_console_login,
        'isfailedlogin': is_failed_login,
        'isrootuser': is_root_user,
        'isassumedrole': is_assumed_role,
        'ishighriskevent': is_high_risk_event,
        'isprivilegedaction': is_privileged_action,
        'isdataaccess': is_data_access,
        'target_bucket': target_bucket,
        'target_key': target_key,
        'target_username': target_username,
        'target_rolename': target_rolename,
        'target_policyname': target_policyname,
        'new_access_key': new_access_key,
        'new_instance_id': new_instance_id,
        'target_group_id': target_group_id,
        'identity_principalid': user_identity.get('principalId', '')
    }
    
    return processed

def extract_username(user_identity):
    """
    Extracts username from userIdentity object.
    """
    user_type = user_identity.get('type', '')
    
    if user_type == 'Root':
        return 'ROOT'
    elif user_type == 'IAMUser':
        return user_identity.get('userName', '')
    elif user_type == 'AssumedRole':
        arn = user_identity.get('arn', '')
        if '/' in arn:
            return arn.split('/')[-1]
        return user_identity.get('principalId', '')
    elif user_type == 'FederatedUser':
        return user_identity.get('principalId', '')
    else:
        return user_identity.get('principalId', '')

def send_to_firehose(records):
    """
    Sends processed records to Kinesis Firehose in batches.
    """
    batch_size = 500
    
    for i in range(0, len(records), batch_size):
        batch = records[i:i + batch_size]
        
        firehose_records = [
            {
                'Data': json.dumps(record) + '
'
            }
            for record in batch
        ]
        
        try:
            response = firehose.put_record_batch(
                DeliveryStreamName=FIREHOSE_STREAM_NAME,
                Records=firehose_records
            )
            
            failed_count = response['FailedPutCount']
            if failed_count > 0:
                print(f"Warning: {failed_count} records failed to send to Firehose")
                
        except Exception as e:
            print(f"Error sending batch to Firehose: {str(e)}")
            raise
```

---
title : "GuardDuty ETL Code"
date: "2000-01-01"
weight : 02
chapter : false
pre : " <b> 5.11.2. </b> "
---

```python

import json
import boto3
import gzip
import os
from datetime import datetime

s3 = boto3.client('s3')
glue = boto3.client('glue')

DESTINATION_BUCKET = os.environ['DESTINATION_BUCKET']
S3_LOCATION_GUARDDUTY = os.environ['S3_LOCATION_GUARDDUTY']
DATABASE_NAME = os.environ['DATABASE_NAME']
TABLE_NAME_GUARDDUTY = os.environ['TABLE_NAME_GUARDDUTY']

def lambda_handler(event, context):
    """
    Processes GuardDuty findings from S3, extracts key fields,
    and stores them in partitioned S3 location with Glue catalog updates.
    """
    
    for record in event['Records']:
        bucket = record['s3']['bucket']['name']
        key = record['s3']['object']['key']
        
        print(f"Processing GuardDuty finding: s3://{bucket}/{key}")
        
        try:
            # Download and decompress GuardDuty finding
            response = s3.get_object(Bucket=bucket, Key=key)
            
            if key.endswith('.gz'):
                content = gzip.decompress(response['Body'].read())
            else:
                content = response['Body'].read()
            
            finding = json.loads(content)
            
            # Process the finding
            processed_finding = process_guardduty_finding(finding)
            
            # Determine partition path
            partition_path = get_partition_path(processed_finding)
            
            # Write to S3
            write_to_s3(processed_finding, partition_path)
            
            # Update Glue partition
            update_glue_partition(partition_path)
            
            print(f"Successfully processed GuardDuty finding: {processed_finding['finding_id']}")
            
        except Exception as e:
            print(f"Error processing {key}: {str(e)}")
            raise

    return {
        'statusCode': 200,
        'body': json.dumps('GuardDuty ETL completed successfully')
    }

def process_guardduty_finding(finding):
    """
    Extracts and flattens GuardDuty finding data.
    """
    
    service = finding.get('service', {})
    resource = finding.get('resource', {})
    
    # Extract network connection details
    action = service.get('action', {})
    network_connection = action.get('networkConnectionAction', {})
    port_probe = action.get('portProbeAction', {})
    dns_request = action.get('dnsRequestAction', {})
    aws_api_call = action.get('awsApiCallAction', {})
    
    # Extract resource details
    instance_details = resource.get('instanceDetails', {})
    access_key_details = resource.get('accessKeyDetails', {})
    s3_bucket_details = resource.get('s3BucketDetails', [])
    
    # Build processed finding
    processed = {
        'finding_id': finding.get('id', ''),
        'finding_type': finding.get('type', ''),
        'title': finding.get('title', ''),
        'severity': finding.get('severity', 0),
        'account_id': finding.get('accountId', ''),
        'region': finding.get('region', ''),
        'created_at': finding.get('createdAt', ''),
        'event_last_seen': service.get('eventLastSeen', ''),
        
        # Network connection details
        'remote_ip': network_connection.get('remoteIpDetails', {}).get('ipAddressV4', ''),
        'remote_port': network_connection.get('remotePortDetails', {}).get('port', 0),
        'connection_direction': network_connection.get('connectionDirection', ''),
        'protocol': network_connection.get('protocol', ''),
        
        # DNS request details
        'dns_domain': dns_request.get('domain', ''),
        'dns_protocol': dns_request.get('protocol', ''),
        
        # Port probe details
        'scanned_ip': port_probe.get('portProbeDetails', [{}])[0].get('remoteIpDetails', {}).get('ipAddressV4', '') if port_probe.get('portProbeDetails') else '',
        'scanned_port': port_probe.get('portProbeDetails', [{}])[0].get('localPortDetails', {}).get('port', 0) if port_probe.get('portProbeDetails') else 0,
        
        # AWS API call details
        'aws_api_service': aws_api_call.get('serviceName', ''),
        'aws_api_name': aws_api_call.get('api', ''),
        'aws_api_caller_type': aws_api_call.get('callerType', ''),
        'aws_api_error': aws_api_call.get('errorCode', ''),
        'aws_api_remote_ip': aws_api_call.get('remoteIpDetails', {}).get('ipAddressV4', ''),
        
        # Resource details
        'target_resource_arn': resource.get('resourceType', ''),
        'instance_id': instance_details.get('instanceId', ''),
        'instance_type': instance_details.get('instanceType', ''),
        'image_id': instance_details.get('imageId', ''),
        'instance_tags': json.dumps(instance_details.get('tags', [])),
        'resource_region': resource.get('region', ''),
        
        # Access key details
        'access_key_id': access_key_details.get('accessKeyId', ''),
        'principal_id': access_key_details.get('principalId', ''),
        'user_name': access_key_details.get('userName', ''),
        
        # S3 bucket details
        's3_bucket_name': s3_bucket_details[0].get('name', '') if s3_bucket_details else '',
        
        # Date for partitioning
        'date': finding.get('createdAt', '')[:10] if finding.get('createdAt') else '',
        
        # Raw JSON for reference
        'service_raw': json.dumps(service),
        'resource_raw': json.dumps(resource),
        'metadata_raw': json.dumps(finding)
    }
    
    return processed

def get_partition_path(finding):
    """
    Determines the S3 partition path based on finding type and date.
    """
    finding_type = finding['finding_type'].replace('/', '_').replace(':', '_')
    created_at = finding['created_at']
    
    if created_at:
        dt = datetime.fromisoformat(created_at.replace('Z', '+00:00'))
        year = dt.strftime('%Y')
        month = dt.strftime('%m')
        day = dt.strftime('%d')
    else:
        year = '0000'
        month = '00'
        day = '00'
    
    return f"type={finding_type}/year={year}/month={month}/day={day}"

def write_to_s3(finding, partition_path):
    """
    Writes the processed finding to S3 in the partitioned location.
    """
    finding_id = finding['finding_id'].replace('/', '_')
    s3_key = f"processed-guardduty/{partition_path}/{finding_id}.json.gz"
    
    # Compress and upload
    compressed_data = gzip.compress(json.dumps(finding).encode('utf-8'))
    
    s3.put_object(
        Bucket=DESTINATION_BUCKET,
        Key=s3_key,
        Body=compressed_data,
        ContentType='application/json',
        ContentEncoding='gzip'
    )
    
    print(f"Written to s3://{DESTINATION_BUCKET}/{s3_key}")

def update_glue_partition(partition_path):
    """
    Creates or updates the Glue partition for the finding.
    """
    parts = partition_path.split('/')
    partition_values = [part.split('=')[1] for part in parts]
    
    partition_location = f"{S3_LOCATION_GUARDDUTY}{partition_path}/"
    
    try:
        # Try to get existing partition
        glue.get_partition(
            DatabaseName=DATABASE_NAME,
            TableName=TABLE_NAME_GUARDDUTY,
            PartitionValues=partition_values
        )
        print(f"Partition already exists: {partition_path}")
        
    except glue.exceptions.EntityNotFoundException:
        # Create new partition
        glue.create_partition(
            DatabaseName=DATABASE_NAME,
            TableName=TABLE_NAME_GUARDDUTY,
            PartitionInput={
                'Values': partition_values,
                'StorageDescriptor': {
                    'Location': partition_location,
                    'InputFormat': 'org.apache.hadoop.mapred.TextInputFormat',
                    'OutputFormat': 'org.apache.hadoop.hive.ql.io.HiveIgnoreKeyTextOutputFormat',
                    'SerdeInfo': {
                        'SerializationLibrary': 'org.openx.data.jsonserde.JsonSerDe'
                    }
                }
            }
        )
        print(f"Created partition: {partition_path}")
```

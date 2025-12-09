---
title : "CloudWatch ETL Code"
date: "2000-01-01"
weight : 03
chapter : false
pre : " <b> 5.11.3. </b> "
---

```python
import json
import boto3
import gzip
import base64
import os

firehose = boto3.client('firehose')
s3 = boto3.client('s3')

FIREHOSE_STREAM_NAME = os.environ['FIREHOSE_STREAM_NAME']

def lambda_handler(event, context):
    """
    Processes VPC DNS query logs from S3 and sends them to Kinesis Firehose.
    """
    
    for record in event['Records']:
        bucket = record['s3']['bucket']['name']
        key = record['s3']['object']['key']
        
        print(f"Processing VPC DNS log: s3://{bucket}/{key}")
        
        try:
            # Download and decompress log file
            response = s3.get_object(Bucket=bucket, Key=key)
            
            if key.endswith('.gz'):
                content = gzip.decompress(response['Body'].read())
            else:
                content = response['Body'].read()
            
            # Process each log line
            processed_records = []
            for line in content.decode('utf-8').split('
'):
                if line.strip():
                    try:
                        log_entry = json.loads(line)
                        processed_record = process_dns_log(log_entry)
                        processed_records.append(processed_record)
                    except json.JSONDecodeError:
                        print(f"Skipping invalid JSON line: {line[:100]}")
                        continue
            
            # Send to Firehose
            if processed_records:
                send_to_firehose(processed_records)
                print(f"Successfully processed {len(processed_records)} DNS log entries")
            
        except Exception as e:
            print(f"Error processing {key}: {str(e)}")
            raise

    return {
        'statusCode': 200,
        'body': json.dumps('VPC DNS ETL completed successfully')
    }

def process_dns_log(log_entry):
    """
    Processes a single DNS query log entry.
    """
    return {
        'version': log_entry.get('version', ''),
        'account_id': log_entry.get('account_id', ''),
        'region': log_entry.get('region', ''),
        'vpc_id': log_entry.get('vpc_id', ''),
        'query_timestamp': log_entry.get('query_timestamp', ''),
        'query_name': log_entry.get('query_name', ''),
        'query_type': log_entry.get('query_type', ''),
        'query_class': log_entry.get('query_class', ''),
        'rcode': log_entry.get('rcode', ''),
        'answers': json.dumps(log_entry.get('answers', [])),
        'srcaddr': log_entry.get('srcaddr', ''),
        'srcport': log_entry.get('srcport', 0),
        'transport': log_entry.get('transport', ''),
        'srcids_instance': log_entry.get('srcids', {}).get('instance', ''),
        'timestamp': log_entry.get('query_timestamp', '')
    }

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
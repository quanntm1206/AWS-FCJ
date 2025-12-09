---
title : "CloudWatch ENI ETL Code"
date: "2000-01-01"
weight : 04
chapter : false
pre : " <b> 5.11.4. </b> "
---

```python

import json
import boto3
import gzip
import os
from datetime import datetime

firehose = boto3.client('firehose')
s3 = boto3.client('s3')

FIREHOSE_STREAM_NAME = os.environ['FIREHOSE_STREAM_NAME']

def lambda_handler(event, context):
    """
    Processes VPC Flow Logs from S3 and sends them to Kinesis Firehose.
    """
    
    for record in event['Records']:
        bucket = record['s3']['bucket']['name']
        key = record['s3']['object']['key']
        
        print(f"Processing VPC Flow log: s3://{bucket}/{key}")
        
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
                if line.strip() and not line.startswith('version'):
                    processed_record = process_flow_log(line)
                    if processed_record:
                        processed_records.append(processed_record)
            
            # Send to Firehose
            if processed_records:
                send_to_firehose(processed_records)
                print(f"Successfully processed {len(processed_records)} flow log entries")
            
        except Exception as e:
            print(f"Error processing {key}: {str(e)}")
            raise

    return {
        'statusCode': 200,
        'body': json.dumps('VPC Flow ETL completed successfully')
    }

def process_flow_log(log_line):
    """
    Processes a single VPC Flow Log entry.
    Format: version account-id interface-id srcaddr dstaddr srcport dstport protocol packets bytes start end action log-status
    """
    try:
        fields = log_line.split()
        
        if len(fields) < 14:
            return None
        
        start_time = int(fields[10])
        timestamp_str = datetime.fromtimestamp(start_time).isoformat()
        
        return {
            'version': int(fields[0]),
            'account_id': fields[1],
            'interface_id': fields[2],
            'srcaddr': fields[3],
            'dstaddr': fields[4],
            'srcport': int(fields[5]),
            'dstport': int(fields[6]),
            'protocol': int(fields[7]),
            'packets': int(fields[8]),
            'bytes': int(fields[9]),
            'start_time': start_time,
            'end_time': int(fields[11]),
            'action': fields[12],
            'log_status': fields[13],
            'timestamp_str': timestamp_str
        }
    except (ValueError, IndexError) as e:
        print(f"Error parsing flow log line: {log_line[:100]} - {str(e)}")
        return None

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

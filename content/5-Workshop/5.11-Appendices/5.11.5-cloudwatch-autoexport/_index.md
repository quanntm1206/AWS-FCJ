---
title : "CloudWatch Autoexport Code"
date: "2000-01-01"
weight : 05
chapter : false
pre : " <b> 5.11.5. </b> "
---

```python

import json
import boto3
import os
from datetime import datetime, timedelta

logs = boto3.client('logs')

DESTINATION_BUCKET = os.environ['DESTINATION_BUCKET']

def lambda_handler(event, context):
    """
    Automatically exports CloudWatch log groups to S3.
    Triggered by CloudWatch Logs subscription filter.
    """
    
    log_group = event.get('logGroup', '/aws/incident-response/centralized-logs')
    
    print(f"Exporting log group: {log_group}")
    
    try:
        # Calculate time range (last hour)
        end_time = datetime.utcnow()
        start_time = end_time - timedelta(hours=1)
        
        # Convert to milliseconds since epoch
        from_time = int(start_time.timestamp() * 1000)
        to_time = int(end_time.timestamp() * 1000)
        
        # Determine export prefix based on log type
        if 'vpc-flow-logs' in log_group or 'flow' in log_group.lower():
            prefix = 'exportedlogs/vpc-flow-logs/'
        elif 'dns' in log_group.lower():
            prefix = 'exportedlogs/vpc-dns-logs/'
        else:
            prefix = 'exportedlogs/other/'
        
        # Create export task
        response = logs.create_export_task(
            logGroupName=log_group,
            fromTime=from_time,
            to=to_time,
            destination=DESTINATION_BUCKET,
            destinationPrefix=prefix
        )
        
        task_id = response['taskId']
        print(f"Created export task: {task_id}")
        
        return {
            'statusCode': 200,
            'body': json.dumps({
                'message': 'Export task created successfully',
                'taskId': task_id
            })
        }
        
    except Exception as e:
        print(f"Error creating export task: {str(e)}")
        raise

```

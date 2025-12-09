---
title : "Isolate EC2 Code"
date: "2000-01-01"
weight : 07
chapter : false
pre : " <b> 5.11.7. </b> "
---

```python

import json
import boto3
import os

ec2 = boto3.client('ec2')

ISOLATION_SG_ID = os.environ['ISOLATION_SG_ID']

def lambda_handler(event, context):
    """
    Isolates a compromised EC2 instance by changing its security group
    to a deny-all security group.
    """
    
    instance_id = event.get('InstanceId', '')
    region = event.get('Region', 'us-east-1')
    
    print(f"Isolating EC2 instance: {instance_id} in region {region}")
    
    if not instance_id:
        raise ValueError("InstanceId is required")
    
    try:
        # Get current instance details
        response = ec2.describe_instances(InstanceIds=[instance_id])
        
        if not response['Reservations']:
            raise ValueError(f"Instance {instance_id} not found")
        
        instance = response['Reservations'][0]['Instances'][0]
        current_sgs = [sg['GroupId'] for sg in instance.get('SecurityGroups', [])]
        
        print(f"Current security groups: {current_sgs}")
        
        # Check if already isolated
        if ISOLATION_SG_ID in current_sgs and len(current_sgs) == 1:
            print(f"Instance {instance_id} is already isolated")
            return {
                'statusCode': 200,
                'InstanceId': instance_id,
                'IsolationSG': None,
                'Message': 'Instance already isolated'
            }
        
        # Change security group to isolation SG
        ec2.modify_instance_attribute(
            InstanceId=instance_id,
            Groups=[ISOLATION_SG_ID]
        )
        
        print(f"Successfully isolated instance {instance_id} with SG {ISOLATION_SG_ID}")
        
        return {
            'statusCode': 200,
            'InstanceId': instance_id,
            'IsolationSG': ISOLATION_SG_ID,
            'PreviousSGs': current_sgs,
            'Message': 'Instance successfully isolated'
        }
        
    except Exception as e:
        print(f"Error isolating instance {instance_id}: {str(e)}")
        raise

```
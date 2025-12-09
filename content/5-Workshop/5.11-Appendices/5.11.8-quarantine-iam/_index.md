---
title : "Quarantine IAM Code"
date: "2000-01-01"
weight : 08
chapter : false
pre : " <b> 5.11.8. </b> "
---
```python

import json
import boto3
import os

iam = boto3.client('iam')

QUARANTINE_POLICY_ARN = os.environ['QUARANTINE_POLICY_ARN']

def lambda_handler(event, context):
    """
    Quarantines a compromised IAM user by attaching a deny-all policy.
    """
    
    print(f"Quarantining IAM user from event: {json.dumps(event)}")
    
    try:
        # Extract user information from GuardDuty finding
        detail = event.get('detail', {})
        resource = detail.get('resource', {})
        access_key_details = resource.get('accessKeyDetails', {})
        
        user_name = access_key_details.get('userName', '')
        
        if not user_name:
            print("No IAM user found in finding")
            return {
                'statusCode': 200,
                'Message': 'No IAM user to quarantine'
            }
        
        print(f"Quarantining IAM user: {user_name}")
        
        # Check if policy is already attached
        response = iam.list_attached_user_policies(UserName=user_name)
        attached_policies = [p['PolicyArn'] for p in response['AttachedPolicies']]
        
        if QUARANTINE_POLICY_ARN in attached_policies:
            print(f"User {user_name} is already quarantined")
            return {
                'statusCode': 200,
                'UserName': user_name,
                'Message': 'User already quarantined'
            }
        
        # Attach quarantine policy
        iam.attach_user_policy(
            UserName=user_name,
            PolicyArn=QUARANTINE_POLICY_ARN
        )
        
        print(f"Successfully quarantined user {user_name}")
        
        return {
            'statusCode': 200,
            'UserName': user_name,
            'QuarantinePolicyArn': QUARANTINE_POLICY_ARN,
            'Message': 'User successfully quarantined'
        }
        
    except Exception as e:
        print(f"Error quarantining IAM user: {str(e)}")
        raise
```
---
title : "Parse Findings Code"
date: "2000-01-01"
weight : 06
chapter : false
pre : " <b> 5.11.6. </b> "
---

```python

import json

def lambda_handler(event, context):
    """
    Parses GuardDuty findings to extract instance IDs and regions
    for incident response actions.
    """
    
    print(f"Parsing GuardDuty finding: {json.dumps(event)}")
    
    try:
        # Extract finding details
        detail = event.get('detail', {})
        resource = detail.get('resource', {})
        resource_type = resource.get('resourceType', '')
        
        # Extract instance information
        instance_details = resource.get('instanceDetails', {})
        instance_ids = []
        
        if resource_type == 'Instance' and instance_details:
            instance_id = instance_details.get('instanceId', '')
            if instance_id:
                instance_ids.append(instance_id)
        
        # Extract region
        region = detail.get('region', 'us-east-1')
        
        # Build response
        response = {
            'InstanceIds': instance_ids,
            'Region': region,
            'FindingType': detail.get('type', ''),
            'Severity': detail.get('severity', 0),
            'ResourceType': resource_type
        }
        
        print(f"Parsed finding: {json.dumps(response)}")
        
        return response
        
    except Exception as e:
        print(f"Error parsing finding: {str(e)}")
        raise

```

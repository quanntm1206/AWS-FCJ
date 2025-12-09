---
title : "Alert Dispatch Code"
date: "2000-01-01"
weight : 01
chapter : false
pre : " <b> 5.11.1. </b> "
---

```python

import json
import boto3
import os
import urllib3

ses = boto3.client('ses')
http = urllib3.PoolManager()

SENDER_EMAIL = os.environ.get('SENDER_EMAIL', '')
RECIPIENT_EMAIL = os.environ.get('RECIPIENT_EMAIL', '')
SLACK_WEBHOOK_URL = os.environ.get('SLACK_WEBHOOK_URL', '')

def lambda_handler(event, context):
    """
    Dispatches security alerts via email (SES) and Slack.
    Triggered by SNS topic when GuardDuty findings are detected.
    """
    
    print(f"Processing alert: {json.dumps(event)}")
    
    try:
        # Parse SNS message
        for record in event['Records']:
            if record['EventSource'] == 'aws:sns':
                message = json.loads(record['Sns']['Message'])
                
                # Extract finding details
                finding_type = message.get('type', 'Unknown')
                severity = message.get('severity', 0)
                title = message.get('title', 'Security Finding')
                description = message.get('description', '')
                region = message.get('region', '')
                account_id = message.get('accountId', '')
                
                # Build alert message
                alert_subject = f"🚨 GuardDuty Alert: {title}"
                alert_body = build_alert_message(message)
                
                # Send email alert
                if SENDER_EMAIL and RECIPIENT_EMAIL:
                    send_email_alert(alert_subject, alert_body)
                
                # Send Slack alert
                if SLACK_WEBHOOK_URL:
                    send_slack_alert(alert_subject, alert_body, severity)
        
        return {
            'statusCode': 200,
            'body': json.dumps('Alerts dispatched successfully')
        }
        
    except Exception as e:
        print(f"Error dispatching alerts: {str(e)}")
        raise

def build_alert_message(finding):
    """
    Builds a formatted alert message from GuardDuty finding.
    """
    finding_type = finding.get('type', 'Unknown')
    severity = finding.get('severity', 0)
    title = finding.get('title', 'Security Finding')
    description = finding.get('description', '')
    region = finding.get('region', '')
    account_id = finding.get('accountId', '')
    created_at = finding.get('createdAt', '')
    
    # Extract resource information
    resource = finding.get('resource', {})
    resource_type = resource.get('resourceType', '')
    instance_details = resource.get('instanceDetails', {})
    instance_id = instance_details.get('instanceId', 'N/A')
    
    # Build message
    message = f"""
GUARDDUTY SECURITY ALERT

Finding Type: {finding_type}
Severity: {severity}
Title: {title}

Description:
{description}

Resource Information:
- Resource Type: {resource_type}
- Instance ID: {instance_id}
- Region: {region}
- Account ID: {account_id}

Timestamp: {created_at}

Action Required:
Please investigate this security finding immediately. The incident response workflow has been automatically triggered.

---
This is an automated alert from the AWS Auto Incident Response System.
"""
    
    return message

def send_email_alert(subject, body):
    """
    Sends email alert via Amazon SES.
    """
    try:
        recipients = [email.strip() for email in RECIPIENT_EMAIL.split(',')]
        
        response = ses.send_email(
            Source=SENDER_EMAIL,
            Destination={
                'ToAddresses': recipients
            },
            Message={
                'Subject': {
                    'Data': subject,
                    'Charset': 'UTF-8'
                },
                'Body': {
                    'Text': {
                        'Data': body,
                        'Charset': 'UTF-8'
                    }
                }
            }
        )
        
        print(f"Email sent successfully: {response['MessageId']}")
        
    except Exception as e:
        print(f"Error sending email: {str(e)}")
        raise

def send_slack_alert(subject, body, severity):
    """
    Sends alert to Slack via webhook.
    """
    try:
        # Determine color based on severity
        if severity >= 7:
            color = '#FF0000'  # Red for high severity
        elif severity >= 4:
            color = '#FFA500'  # Orange for medium severity
        else:
            color = '#FFFF00'  # Yellow for low severity
        
        # Build Slack message
        slack_message = {
            'attachments': [
                {
                    'color': color,
                    'title': subject,
                    'text': body,
                    'footer': 'AWS Auto Incident Response System'
                }
            ]
        }
        
        # Send to Slack
        encoded_data = json.dumps(slack_message).encode('utf-8')
        response = http.request(
            'POST',
            SLACK_WEBHOOK_URL,
            body=encoded_data,
            headers={'Content-Type': 'application/json'}
        )
        
        if response.status == 200:
            print("Slack alert sent successfully")
        else:
            print(f"Slack alert failed with status {response.status}: {response.data}")
        
    except Exception as e:
        print(f"Error sending Slack alert: {str(e)}")
        # Don't raise - email is primary notification method
```
---
title : "Create Lambda Execution Roles"
date: "2000-01-01"
weight : 01
chapter : false
pre : " <b> 5.3.3.1. </b> "
---


#### Create CloudTrailETLLambdaServiceRole

1.  **Open the IAM Console**:

      - Navigate to https://console.aws.amazon.com/iam/
      - Or: AWS Management Console → Search for "IAM" → Click "IAM"

    > [Screenshot: IAM Console Dashboard]

2.  **Navigate to Roles**:

      - In the left sidebar, click **"Roles"**

    > [Screenshot: IAM Console with Roles menu item]

3.  **Click "Create role"**

    > [Screenshot: IAM Roles page with Create role button]

4.  **Select trusted entity**:

      - **Trusted entity type**: Select **"AWS service"**
      - **Use case**: Select **"Lambda"**
      - Click **"Next"**

    > [Screenshot: IAM Create role - Select trusted entity]

5.  **Add permissions**:

      - In the search box, type `AWSLambdaBasicExecutionRole`
      - Check the box next to **"AWSLambdaBasicExecutionRole"**
      - Click **"Next"**

    > [Screenshot: IAM Create role - Add permissions]

6.  **Name, review, and create**:

      - **Role name**: Enter `CloudTrailETLLambdaServiceRole`
      - **Description**: Enter `Execution role for CloudTrail ETL Lambda function`
      - Click **"Create role"**

    > [Screenshot: IAM Create role - Name and review]

7.  **Add inline policy**:

      - After creation, you'll be on the role details page
      - Click on the **"Permissions"** tab
      - Click **"Add permissions"** → **"Create inline policy"**

    > [Screenshot: IAM Role permissions tab with Add permissions button]

8.  **Create inline policy**:

      - Click on the **"JSON"** tab
      - Paste the following policy (replace `ACCOUNT_ID` and `REGION`):

<!-- end list -->

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::incident-response-log-list-bucket-ACCOUNT_ID-REGION/*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "firehose:PutRecord",
        "firehose:PutRecordBatch"
      ],
      "Resource": "arn:aws:firehose:REGION:ACCOUNT_ID:deliverystream/cloudtrail-firehose-stream"
    }
  ]
}
```

> [Screenshot: IAM Create policy - JSON editor]

9.  **Click "Next"**

10. **Policy name**:

      - **Policy name**: Enter `CloudTrailETLPolicy`
      - Click **"Create policy"**

    > [Screenshot: IAM Create policy - Review and create]

11. **Verify role creation**:

      - You should see the role with both managed and inline policies attached

    > [Screenshot: IAM Role showing AWSLambdaBasicExecutionRole and CloudTrailETLPolicy]

#### Create Remaining Lambda Roles

**Follow the same process for each role below** (steps 3-11):

**GuardDutyETLLambdaServiceRole**

  - Role name: `GuardDutyETLLambdaServiceRole`
  - Description: `Execution role for GuardDuty ETL Lambda function`
  - Managed policy: AWSLambdaBasicExecutionRole
  - Inline policy name: `GuardDutyETLPolicy`
  - Inline policy JSON:

<!-- end list -->

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": [
        "arn:aws:s3:::incident-response-log-list-bucket-ACCOUNT_ID-REGION/*",
        "arn:aws:s3:::processed-guardduty-findings-ACCOUNT_ID-REGION/*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": "kms:Decrypt",
      "Resource": "arn:aws:kms:REGION:ACCOUNT_ID:key/*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "glue:CreatePartition",
        "glue:GetPartition"
      ],
      "Resource": [
        "arn:aws:glue:REGION:ACCOUNT_ID:catalog",
        "arn:aws:glue:REGION:ACCOUNT_ID:database/security_logs",
        "arn:aws:glue:REGION:ACCOUNT_ID:table/security_logs/processed_guardduty"
      ]
    }
  ]
}
```

**CloudWatchETLLambdaServiceRole**

  - Role name: `CloudWatchETLLambdaServiceRole`
  - Description: `Execution role for VPC DNS logs ETL Lambda`
  - Managed policy: AWSLambdaBasicExecutionRole
  - Inline policy name: `CloudWatchETLPolicy`
  - Inline policy JSON:

<!-- end list -->

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::incident-response-log-list-bucket-ACCOUNT_ID-REGION/*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "firehose:PutRecord",
        "firehose:PutRecordBatch"
      ],
      "Resource": "arn:aws:firehose:REGION:ACCOUNT_ID:deliverystream/vpc-dns-firehose-stream"
    }
  ]
}
```

**CloudWatchENIETLLambdaServiceRole**

  - Role name: `CloudWatchENIETLLambdaServiceRole`
  - Description: `Execution role for VPC Flow logs ETL Lambda`
  - Managed policy: AWSLambdaBasicExecutionRole
  - Inline policy name: `CloudWatchENIETLPolicy`
  - Inline policy JSON:

<!-- end list -->

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::incident-response-log-list-bucket-ACCOUNT_ID-REGION/*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "firehose:PutRecord",
        "firehose:PutRecordBatch"
      ],
      "Resource": "arn:aws:firehose:REGION:ACCOUNT_ID:deliverystream/vpc-flow-firehose-stream"
    }
  ]
}
```

**CloudWatchExportLambdaServiceRole**

  - Role name: `CloudWatchExportLambdaServiceRole`
  - Description: `Execution role for CloudWatch log export Lambda`
  - Managed policy: AWSLambdaBasicExecutionRole
  - Inline policy name: `CloudWatchExportPolicy`
  - Inline policy JSON:

<!-- end list -->

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "logs:CreateExportTask",
        "logs:DescribeExportTasks",
        "s3:PutObject"
      ],
      "Resource": [
        "arn:aws:logs:REGION:ACCOUNT_ID:log-group:*",
        "arn:aws:s3:::incident-response-log-list-bucket-ACCOUNT_ID-REGION/*"
      ]
    }
  ]
}
```

**ParseFindingsLambdaServiceRole**

  - Role name: `ParseFindingsLambdaServiceRole`
  - Description: `Execution role for parsing GuardDuty findings`
  - Managed policy: AWSLambdaBasicExecutionRole
  - **No inline policy needed**

**IsolateEC2LambdaServiceRole**

  - Role name: `IsolateEC2LambdaServiceRole`
  - Description: `Execution role for isolating compromised EC2 instances`
  - Managed policy: AWSLambdaBasicExecutionRole
  - Inline policy name: `IsolateEC2Policy`
  - Inline policy JSON:

<!-- end list -->

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeInstances",
        "ec2:ModifyInstanceAttribute"
      ],
      "Resource": "*"
    }
  ]
}
```

**QuarantineIAMLambdaServiceRole**

  - Role name: `QuarantineIAMLambdaServiceRole`
  - Description: `Execution role for quarantining compromised IAM users`
  - Managed policy: AWSLambdaBasicExecutionRole
  - Inline policy name: `QuarantineIAMPolicy`
  - Inline policy JSON:

<!-- end list -->

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:AttachUserPolicy",
        "iam:ListAttachedUserPolicies"
      ],
      "Resource": [
        "arn:aws:iam::ACCOUNT_ID:user/*",
        "arn:aws:iam::ACCOUNT_ID:policy/IrQuarantineIAMPolicy"
      ]
    }
  ]
}
```

**AlertDispatchLambdaServiceRole**

  - Role name: `AlertDispatchLambdaServiceRole`
  - Description: `Execution role for dispatching alerts via SNS/SES/Slack`
  - Managed policy: AWSLambdaBasicExecutionRole
  - Inline policy name: `AlertDispatchPolicy`
  - Inline policy JSON:

<!-- end list -->

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "sns:Publish",
      "Resource": "arn:aws:sns:REGION:ACCOUNT_ID:IncidentResponseAlerts"
    },
    {
      "Effect": "Allow",
      "Action": [
        "ses:SendEmail",
        "ses:SendRawEmail"
      ],
      "Resource": "*"
    }
  ]
}
```

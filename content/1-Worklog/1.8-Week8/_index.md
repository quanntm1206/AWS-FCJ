---
title: "Week 8 Worklog"
date: "2000-01-01"
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Week 8 Objectives:

* **Advanced Security:** Implementing layered security with encryption (KMS, ACM) and edge protection (WAF, Shield).
* **Serverless Data Lake:** Structuring a serverless analytics architecture using Amazon S3 for storage and Amazon Athena for querying.
* **Global Networking:** Optimizing content delivery and latency using Route 53, Global Accelerator, and CloudFront.
* **Cost Governance:** Mastering cost analysis tools (Cost Explorer, Budgets) and multi-account management strategies.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (27/10) | **Advanced Security Services** <br> - **Review:** Comprehensive consolidation of core AWS services (EC2, VPC, IAM, S3, RDS). <br> - **Data Encryption:** Configured **AWS KMS** (Key Management Service) for encryption at rest and **AWS ACM** for SSL/TLS certificates. | 20/10/2025 | 20/10/2025 | [EC2 User Guide](https://docs.aws.amazon.com/pdfs/AWSEC2/latest/UserGuide/ec2-ug.pdf) <br> [VPC User Guide](https://docs.aws.amazon.com/pdfs/vpc/latest/userguide/vpc-ug.pdf) <br> [IAM User Guide](https://docs.aws.amazon.com/pdfs/IAM/latest/UserGuide/iam-ug.pdf) <br> [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) <br> [RDS User Guide](https://docs.aws.amazon.com/pdfs/AmazonRDS/latest/UserGuide/rds-ug.pdf)<br> [KMS Developer Guide](https://docs.aws.amazon.com/pdfs/kms/latest/developerguide/kms-dg.pdf) <br> [ACM User Guide](https://docs.aws.amazon.com/pdfs/acm/latest/userguide/acm-ug.pdf) |
| Tue (28/10) | **Edge Protection:** Deployed **AWS WAF** and **AWS Shield** to mitigate DDoS/Web exploits. <br> - **Threat Detection:** Analyzed **Amazon GuardDuty** findings and integrated **AWS Secrets Manager** for credential rotation. **Project R&D: Serverless Data Analysis** <br> - **Storage Layer:** Structured **Amazon S3** buckets as a Data Lake for log aggregation. <br> - **Query Engine:** Utilized **Amazon Athena** to run standard SQL queries directly on S3 data without provisioning servers. <br> - **Observability:** Configured **CloudWatch** for monitoring metrics and logs. | 21/10/2025 | 21/10/2025 |[WAF Developer Guide](https://docs.aws.amazon.com/pdfs/waf/latest/developerguide/waf-dg.pdf) <br> [AMS User Guide (GuardDuty)](https://docs.aws.amazon.com/pdfs/managedservices/latest/userguide/ams-ug.pdf) <br> [RDS Guide (Secrets Manager)](https://docs.aws.amazon.com/pdfs/AmazonRDS/latest/UserGuide/rds-ug.pdf)<br> [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) <br> [S3 API Reference](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/API/s3-api.pdf) |
| Wed (29/10) | **Networking & Compute Scaling** <br> - **Global Traffic:** Configured **Amazon Route 53** (DNS Failover) and **AWS Global Accelerator** for low-latency user access. <br> - **CDN:** Optimized content delivery with **Amazon CloudFront**. <br> - **Serverless Compute:** Deployed functions on **AWS Lambda** and containers on **AWS Fargate**. <br> - **Storage Performance:** Compared **EBS Provisioned IOPS** vs **Amazon EFS** throughput modes. | 22/10/2025 | 22/10/2025 |[Route 53 Guide](https://docs.aws.amazon.com/pdfs/Route53/latest/DeveloperGuide/route53-dg.pdf) <br> [Global Accelerator Guide](https://docs.aws.amazon.com/pdfs/global-accelerator/latest/dg/global-accelerator-guide.pdf) <br> [CloudFront Guide](
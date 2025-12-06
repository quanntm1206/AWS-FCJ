---
title: "Week 8 Worklog"
date: "2000-01-01"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (27/10) | **Advanced Security Services** <br> - **Review:** Comprehensive consolidation of core AWS services (EC2, VPC, IAM, S3, RDS). <br> - **Data Encryption:** Configured **AWS KMS** (Key Management Service) for encryption at rest and **AWS ACM** for SSL/TLS certificates.   | 20/10/2025 | 20/10/2025 | [EC2 User Guide](https://docs.aws.amazon.com/pdfs/AWSEC2/latest/UserGuide/ec2-ug.pdf) <br> [VPC User Guide](https://docs.aws.amazon.com/pdfs/vpc/latest/userguide/vpc-ug.pdf) <br> [IAM User Guide](https://docs.aws.amazon.com/pdfs/IAM/latest/UserGuide/iam-ug.pdf) <br> [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) <br> [RDS User Guide](https://docs.aws.amazon.com/pdfs/AmazonRDS/latest/UserGuide/rds-ug.pdf)<br> [KMS Developer Guide](https://docs.aws.amazon.com/pdfs/kms/latest/developerguide/kms-dg.pdf) <br> [ACM User Guide](https://docs.aws.amazon.com/pdfs/acm/latest/userguide/acm-ug.pdf)  |
| Tue (28/10) | **Edge Protection:** Deployed **AWS WAF** and **AWS Shield** to mitigate DDoS/Web exploits. <br> - **Threat Detection:** Analyzed **Amazon GuardDuty** findings and integrated **AWS Secrets Manager** for credential rotation. **Project R&D: Serverless Data Analysis** <br> - **Storage Layer:** Structured **Amazon S3** buckets as a Data Lake for log aggregation. <br> - **Query Engine:** Utilized **Amazon Athena** to run standard SQL queries directly on S3 data without provisioning servers. <br> - **Observability:** Configured **CloudWatch** for monitoring metrics and logs. | 21/10/2025 | 21/10/2025 |[WAF Developer Guide](https://docs.aws.amazon.com/pdfs/waf/latest/developerguide/waf-dg.pdf) <br> [AMS User Guide (GuardDuty)](https://docs.aws.amazon.com/pdfs/managedservices/latest/userguide/ams-ug.pdf) <br> [RDS Guide (Secrets Manager)](https://docs.aws.amazon.com/pdfs/AmazonRDS/latest/UserGuide/rds-ug.pdf)<br> [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) <br> [S3 API Reference](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/API/s3-api.pdf) |
| Wed (29/10) | **Networking & Compute Scaling** <br> - **Global Traffic:** Configured **Amazon Route 53** (DNS Failover) and **AWS Global Accelerator** for low-latency user access. <br> - **CDN:** Optimized content delivery with **Amazon CloudFront**. <br> - **Serverless Compute:** Deployed functions on **AWS Lambda** and containers on **AWS Fargate**. <br> - **Storage Performance:** Compared **EBS Provisioned IOPS** vs **Amazon EFS** throughput modes. | 22/10/2025 | 22/10/2025 |[Route 53 Guide](https://docs.aws.amazon.com/pdfs/Route53/latest/DeveloperGuide/route53-dg.pdf) <br> [Global Accelerator Guide](https://docs.aws.amazon.com/pdfs/global-accelerator/latest/dg/global-accelerator-guide.pdf) <br> [CloudFront Guide](https://docs.aws.amazon.com/pdfs/AmazonCloudFront/latest/DeveloperGuide/AmazonCloudFront_DevGuide.pdf) <br> [Lambda Developer Guide](https://docs.aws.amazon.com/pdfs/lambda/latest/dg/lambda-dg.pdf) <br> [ECS Guide (Fargate)](https://docs.aws.amazon.com/pdfs/AmazonECS/latest/developerguide/ecs-dg.pdf) |
| Thu (30/10) | **Cost Optimization & Governance** <br> - **Analysis:** Visualized spending trends using **AWS Cost Explorer** and set alerts via **AWS Budgets**. <br> - **Pricing Strategy:** Evaluated **Savings Plans** vs **Reserved Instances** vs **Spot Instances**. <br> - **Multi-Account:** Managed policies using **AWS Organizations**. <br> **Interactive Review: AWS Card Clash** <br> - **Activity:** Utilized "AWS Card Clash 3D" game to simulate architectural decision-making. <br> - **Benefit:** Reinforced service selection logic and understanding of service interactions in a gamified environment. | 23/10/2025 | 23/10/2025 | [Cost Management Guide](https://docs.aws.amazon.com/pdfs/cost-management/latest/userguide/cost-management-guide.pdf) <br> [Savings Plans Guide](https://docs.aws.amazon.com/pdfs/savingsplans/latest/userguide/savingsplans.pdf) <br> [EC2 Purchasing Options](https://docs.aws.amazon.com/pdfs/AWSEC2/latest/UserGuide/ec2-ug.pdf) <br> [Organizations Guide](https://docs.aws.amazon.com/pdfs/organizations/latest/userguide/organizations-userguide.pdf) <br> [AWS Card Clash](https://arcade.cardclash.training.aws.dev/) |
| Fri (31/10) | **Final Assessment Day** <br> - **Milestone:** Successfully participated in the Final Examination. <br> - **Outcome:** Demonstrated competency in AWS Cloud Architecture and Service implementation. | 31/10/2025 | 31/10/2025 |  |


### Week 8 Achievements:

* **Advanced Security Competency:**
    * Moved beyond basic firewalls to implementing layered security with **AWS WAF** (Application Layer 7) and **AWS Shield** (DDoS protection).
    * Secured sensitive data at rest using **KMS Customer Master Keys (CMKs)**.

* **Serverless Architecture Mastery:**
    * Designed a highly scalable, zero-maintenance analytics stack using **S3 + Athena**, eliminating the need for traditional ETL servers.
    * Understood the trade-offs between **Lambda** (Event-driven) and **Fargate** (Long-running containers).

* **Strategic Cost Management:**
    * Differentiated between the flexibility of **Savings Plans** versus the rigidity of Reserved Instances to optimize long-term compute costs.
    * Utilized **Cost Explorer** to identify and eliminate resource wastage.
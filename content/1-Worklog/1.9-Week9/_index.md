---
title: "Week 9 Worklog"
date: "2000-01-01"
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
### Week 9 Objectives:

* **Project Architecture:** Designing a Serverless Log Analytics pipeline using AWS managed services.
* **Data Ingestion:** Automating log extraction from Amazon CloudWatch to Amazon S3 using AWS Lambda.
* **ETL Automation:** Implementing Extract-Transform-Load (ETL) logic to normalize raw JSON logs.
* **Data Analytics:** Enabling interactive SQL queries on S3 data using Amazon Athena.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| :--- | :--- | :--- | :--- | :--- |
| **Mon (3/11)** | **Project R&D: Log Analytics Architecture**<br>- **Requirement Analysis:** Defined the flow for collecting and analyzing application logs.<br>- **Architecture Design:** Designed a pipeline: **CloudWatch Logs** (Source) $\to$ **AWS Lambda** (Collector) $\to$ **Amazon S3** (Data Lake) $\to$ **Amazon Athena** (Query Engine).<br>- **Format Strategy:** Decided on JSON format for raw logs to ensure schema flexibility. | 03/11/2025 | 03/11/2025 | [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf)<br>[Module 04-02 - S3 Concepts](https://youtu.be/_yunukwcAwc?si=eFjVimOndHJO2_x1)<br>[CloudWatch Metrics](https://docs.aws.amazon.com/pdfs/AWSEC2/latest/UserGuide/ec2-ug.pdf) |
| **Tue (4/11)** | **Data Ingestion Implementation (Part 1)**<br>- **Lambda Dev:** Developed a Python/Node.js Lambda function to interface with CloudWatch Logs API.<br>- **Logic:** Implemented logic to "crawl" (fetch) log streams and aggregate them.<br>- **Storage:** Configured S3 Bucket policy to allow Lambda write access. | 04/11/2025 | 04/11/2025 | [S3 API Reference](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/API/s3-api.pdf)<br>[CloudWatch for VPC](https://docs.aws.amazon.com/pdfs/vpc/latest/userguide/vpc-ug.pdf) |
| **Wed (5/11)** | **Data Ingestion Implementation (Part 2)**<br>- **Formatting:** Structured the fetched logs into valid JSON objects.<br>- **Persistence:** Successfully stored raw log files into the S3 bucket (Raw Zone).<br>- **Testing:** Verified log integrity by manually inspecting S3 objects. | 05/11/2025 | 05/11/2025 | [S3 User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf) |
| **Thu (6/11)** | **ETL Processing Development (Part 1)**<br>- **Lambda ETL:** Started developing a second Lambda function triggered by S3 Event Notifications (ObjectCreate).<br>- **Transformation:** Implemented logic to parse raw JSON files, clean data, and flatten nested structures. | 06/11/2025 | 06/11/2025 | [Athena User Guide](https://docs.aws.amazon.com/pdfs/AmazonS3/latest/userguide/s3-userguide.pdf)|
| **Fri (7/11)** | **ETL Processing & Athena Integration (Part 2)**<br>- **Loading:** Configured the Lambda to output processed data to a target S3 bucket (Clean Zone).<br>- **Athena Integration:** Defined the Table Schema (DDL) in Athena to map to the processed JSON data.<br>- **Validation:** Executed SQL queries in Athena to verify data accuracy and structure. | 07/11/2025 | 07/11/2025 | [VPC Flow Logs & Athena](https://docs.aws.amazon.com/pdfs/vpc/latest/userguide/vpc-ug.pdf)<br>[Athena Solutions](https://docs.aws.amazon.com/pdfs/solutions/latest/amazon-marketing-cloud-insights-on-aws/amazon-marketing-cloud-insights-on-aws.pdf) |

### Week 9 Achievements:

* **Built a Serverless ETL Pipeline:**
    * Successfully automated the flow of data from operational logs (CloudWatch) to an analytical data lake (S3) without provisioning any servers (using **AWS Lambda**).
    * Implemented **ETL (Extract, Transform, Load)** processes to convert unstructured raw logs into structured, queryable JSON datasets.

* **Mastered Data Analytics on AWS:**
    * Configured **Amazon Athena** to treat files in S3 as a relational database, enabling SQL-based analysis on log data.
    * Applied **S3 Best Practices** by organizing data into "Raw" and "Processed" zones to maintain data lake hygiene.

* **CloudWatch Integration:**
    * Deepened understanding of programmatic access to CloudWatch Logs beyond the Console UI.
---
title: "Week 11 Worklog"
date: "2000-01-01"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
### Week 11 Objectives:

* **ETL Automation:** Enhancing the "CloudWatch ETL Lambda" to support automated schema evolution (Auto-Create Table) and Event-driven execution.
* **Pipeline R&D:** Investigating methods to automate CloudWatch Log Exports (Batch Ingestion) vs Streaming.
* **Architectural Trade-offs:** Evaluating EventBridge Scheduler vs Subscription Filters for data ingestion.
* **Incident Analysis:** Troubleshooting compatibility issues between Real-time Streaming (Subscription Filters) and Batch Processing formats.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| :--- | :--- | :--- | :--- | :--- |
| **Mon (17/11)** | **Event: “AWS Cloud Mastery Series #2 - DevOps on AWS”**<br>- Introduce AWS DevOps Services. – CI/CD Pipeline.<br>- Introduce Infrastructure as Code (IaC) and related tools.<br>- Introduce Container Services on AWS. <br> - Ensure Monitoring and Observability capability using AWS Services | 17/11/2025 | 17/11/2025 | |
| **Tue (18/11)** | **ETL Pipeline Upgrade (Event-Driven Architecture)**<br>- **Feature:** Upgraded **CloudWatch ETL Lambda** code to automatically detect schema and execute DDL (Create Table) if the Athena table is missing.<br>- **Automation:** Configured **S3 Event Notifications** to trigger this Lambda immediately upon object creation (`s3:ObjectCreated:*`), removing the need for manual invocation. | 18/11/2025 | 18/11/2025 |  |
| **Wed (19/11)** | **Ingestion Gap Analysis (Auto-Export Research)**<br>- **Gap:** Identified that CloudWatch Logs requires manual initiation for S3 exports.<br>- **Research:** Investigated **Amazon EventBridge Scheduler** to trigger the `create_export_task` API periodically.<br>- **Status:** Proof of Concept (PoC) phase. | 19/11/2025 | 19/11/2025 |  |
| **Thu (20/11)** | **Architectural Pivot & Failure Analysis**<br>- **Pivot:** Attempted to use **CloudWatch Subscription Filters** as a simpler alternative to EventBridge.<br>- **Failure:** The pipeline broke because Subscription Filters stream data (base64 encoded real-time stream), whereas the current ETL Lambda expects batch log files (.gz).<br>- **Decision:** Reverted to the Batch Export strategy. | 20/11/2025 | 20/11/2025 | [Subscription Filters](https://youtu.be/KRwDInHmgQY?si=4VrwITz_bgjgk_uN) |
| **Fri (21/11)** | **Ingestion Remediation (EventBridge Retry)**<br>- **Action:** Resumed testing with EventBridge Scheduler to trigger Log Exports.<br>- **Challenge:** Encountered IAM permission and Lambda timeout issues during the export trigger execution.<br>- **Outcome:** Solution is currently **unstable/pending resolution**. Continued debugging over the weekend. | 21/11/2025 | 22/11/2025 |  |

### Week 11 Achievements:

* **Advanced Lambda & Automation:**
    * Successfully transformed the ETL process into a fully **Event-Driven** workflow. Now, data is processed instantly as soon as it arrives in the Data Lake (S3), reducing data latency.
    * Implemented **Automated Schema Management** within Lambda (Auto-Create Athena Table), reducing operational overhead when deploying to new environments.

* **Architectural Deep Dive (Streaming vs Batch):**
    * Gained a profound understanding of the difference between **Log Streaming** (Subscription Filters - Kinesis/Lambda) and **Log Export** (S3 Batch).
    * Validated that "Streaming" requires a completely different processing logic (Stream decoding) compared to "Batching" (File parsing), leading to informed architectural decisions.
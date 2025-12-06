---
title: "Week 10 Worklog"
date: "2000-01-01"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
### Week 10 Objectives:

* **Cost Optimization:** Refactoring the Data Pipeline from Athena ETL to AWS Lambda to reduce operational costs.
* **ChatOps Implementation:** Integrating AWS GuardDuty with Slack for real-time threat monitoring.
* **Operational Excellence:** Customizing notification payloads for better visibility and handling "Alert Fatigue" incidents.
* **Data Engineering:** resolving schema mismatch issues by standardizing data format to JSONL.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| :--- | :--- | :--- | :--- | :--- |
| **Mon (10/11)** | **Pipeline Refactoring (Cost Optimization)**<br>- **Decision:** Migrated from Athena ETL to **AWS Lambda** for log processing to minimize costs.<br>- **Issue:** Encountered **Schema Mismatch** (field mix-up) where raw logs could not be correctly parsed into the target structure.<br>- **Status:** Investigation in progress. | 10/11/2025 | 10/11/2025 | [Lambda Pricing](https://aws.amazon.com/lambda/pricing/)<br>[Athena Pricing](https://aws.amazon.com/athena/pricing/) |
| **Tue (11/11)** | **ChatOps Integration & Incident Handling**<br>- **Setup:** Configured **AWS Chatbot** to integrate SNS with Slack Channel.<br>- **Incident:** Triggered "Alert Storm" (1000+ emails) due to teammate activating all **GuardDuty Sample Findings** simultaneously.<br>- **Response:** Tuned SNS subscription filters to manage noise. | 11/11/2025 | 11/11/2025 | [GuardDuty Findings](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_findings.html) |
| **Wed (12/11)** | **Notification Payload Optimization (Lambda)**<br>- **UX Audit:** Noticed default Slack notifications lacked critical context (Severity Level) in the preview/collapsed view.<br>- **Coding:** Updated **Lambda logic** to parse raw findings and construct a **Custom Message Payload**.<br>- **Result:** Important fields (Severity, Region, Type) are now visible immediately without opening the app. | 12/11/2025 | 12/11/2025 | |
| **Thu (13/11)** | **Data Pipeline Remediation (Part 1)**<br>- **Debugging:** Analyzed the "field mix-up" error from Monday.<br>- **Root Cause:** Standard JSON arrays were causing ingestion issues with Athena's SerDe.<br>- **Solution Strategy:** Decided to convert the data stream format to **JSONL (Newline Delimited JSON)**. | 13/11/2025 | 13/11/2025 | |
| **Fri (14/11)** | **Data Pipeline Remediation (Part 2)**<br>- **Implementation:** Updated Lambda logic to serialize processed logs as `.jsonl` files.<br>- **Validation:** Successfully pushed cleaned data to S3 and manually queried via Athena without schema errors.<br>- **Outcome:** Pipeline is now functional and cost-effective. | 14/11/2025 | 14/11/2025 |  |
| **Sat (15/11)** | **Event: “AWS Cloud Mastery Series #1 - AI/ML/GenAI on AWS”**<br>- Introducing AI/ML/GenAI on AWS. | 15/11/2025 | 15/11/2025 | |

### Week 10 Achievements:

* **Engineered a Cost-Effective Data Pipeline:**
    * Successfully replaced the expensive Athena ETL approach with a lightweight **Lambda-based** solution.
    * Solved the complex **JSON Parsing/Schema Mismatch** issue by implementing **JSONL serialization**, ensuring seamless data ingestion into the Data Lake.

* **Established Robust ChatOps:**
    * Built a real-time threat notification system: **GuardDuty $\to$ EventBridge $\to$ SNS $\to$ AWS Chatbot $\to$ Slack**.
    * **UX Optimization:** Custom-formatted notifications to display **Severity** immediately, significantly reducing the "Mean Time To Know" (MTTK) for security alerts.

* **Incident Management Experience:**
    * Learned a valuable lesson on **Alert Fatigue** when handling 1000+ sample findings, reinforcing the importance of proper SNS filtering and testing protocols.
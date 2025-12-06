---
title: "Week 4 Worklog"
date: "2000-01-01"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* **Observability & Monitoring:** Master the "Three Pillars of Observability" on AWS: Logs (CloudTrail), Metrics (CloudWatch), and Traces/Traffic (VPC Flow Logs).
* **Incident Response Automation:** Understand how to link CloudWatch Alarms with SNS to trigger automated alerts.
* **Security Analytics:** Learn to query audit logs using Amazon Athena and detect threats with GuardDuty.
* **Serverless Basics:** Introduction to AWS Lambda and Systems Manager.
* **Project Initiation:** Begin researching project architecture and translating technical engineering blogs.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (29/9) | **Incident Response Essentials:** <br> - **CloudTrail:** Configured trails for auditing user activity and API calls. <br> - **CloudWatch:** Setup Metrics and Alarms (CPU/Network thresholds). <br> - **VPC Flow Logs:** Captured IP traffic for network troubleshooting. <br> - **SNS:** Setup notification topics for alarm triggers. | 29/09/2025 | 29/09/2025 | [CloudWatch Metrics](https://youtu.be/Yxl7e88cTAQ) <br> [VPC Flow Logs](https://youtu.be/_qM6ilKz3C8) <br> [CloudWatch Alarms](https://youtu.be/3v_X53RmYf0) <br> [SNS Setup](https://youtu.be/j5Xp51eUyXE) <br> [CloudTrail Basics](https://youtu.be/CXbdsp9ThvM) |
| Tue (30/9) | **Advanced Analytics & Serverless:** <br> - **Athena:** Queried CloudTrail logs in S3 using SQL to investigate specific events. <br> - **GuardDuty:** Explored intelligent threat detection mechanisms. <br> - **Compute:** Introduction to AWS Lambda (Serverless) and Systems Manager (Ops automation). | 30/09/2025 | 30/09/2025 | [AWS Lambda Intro](https://youtu.be/eOBq__h4OJ4) <br> [Systems Manager](https://youtu.be/pSVK-ingvfc) <br> [GuardDuty Deep Dive](https://www.youtube.com/watch?v=Wkpl66NaqEA) <br> [CloudTrail with Athena](https://youtu.be/I4vYkrHq5hs) |
| Wed (1/10) | **Self-study & Review:** <br> - Consolidate knowledge on Monitoring tools. <br> - Prepare environment for upcoming Project. | 01/10/2025 | 01/10/2025 ||
| Thu (2/10) | **Project Architecture & Translation:** <br> - **Project:** Research and analyze the proposed architecture for the internship project. <br> - **Blog 1:** Translated "Democratizing quantum resources: University of Michigan and AWS collaborate on a remote access quantum testbed". | 02/10/2025 | 02/10/2025 | [Original Blog](https://aws.amazon.com/vi/blogs/publicsector/democratizing-quantum-resources-university-of-michigan-and-aws-collaborate-on-a-remote-access-quantum-testbed/) <br> [My Translation](https://docs.google.com/document/d/1SAgaxbJU1wQMvoegtjcIjG0iNRnHMAaOlaZg5VzcaXk/edit?tab=t.0) |
| Fri (3/10) | **Event: AI-Driven Development Life Cycle: Reimagining Software Engineering** <br> - Generative AI is turning developers into editors, shifting the main job from writing code to just reviewing it. <br> - AI-DLC is where AI executes the coding and testing phases, shifting the human role from writing syntax to defining business intent and validating the AI's output. <br> Kiro and Amazon Q Developer showcase. | 03/10/2025 | 03/10/2025 | |
| Sat (4/10) | **Advanced Data Streaming (Blog 2):** <br> - **Topic:** Apache Kafka Disaster Recovery & Migration. <br> - **Task:** Translated Blog "Amazon MSK Replicator and MirrorMaker2". <br> - **Key Learnings:** Replication strategies, Active-Active vs Active-Passive setups. | 04/10/2025 | 04/10/2025 | [Original Blog](https://aws.amazon.com/vi/blogs/big-data/amazon-msk-replicator-and-mirrormaker2-choosing-the-right-replication-strategy-for-apache-kafka-disaster-recovery-and-migrations/) <br> [My Translation](https://docs.google.com/document/d/11JuanGg4j-wQ8khxs8xU23GkNEaO-xmhJlYNLc4Q6H8/edit?tab=t.0) |


### Week 4 Achievements:

* **Mastered AWS Observability Suite:**
    * Differentiated the distinct roles of **CloudTrail** (Auditing/Who did what?) vs **CloudWatch** (Performance/How is it running?).
    * Understood the cost/retention limitations of CloudTrail (90 days default) and the necessity of S3 export for long-term compliance.

* **Security & Forensic Analysis:**
    * Learned to use **Amazon Athena** to run SQL queries directly on log data in S3, significantly reducing the time needed to investigate security incidents.
    * Configured **SNS** to decouple monitoring from alerting, allowing multiple subscribers (Email, Lambda, SMS) to react to a single alarm.

* **Technical Translation & Research:**
    * Deepened technical vocabulary through translating complex topics (Quantum Computing & Kafka Replication).
    * Gained insights into hybrid architectures (MSK Replicator) and academic cloud collaborations.
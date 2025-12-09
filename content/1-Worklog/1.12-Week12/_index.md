---
title: "Week 12 Worklog"
date: "2025-11-25"
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:

* **Pipeline Re-architecture:** Finalizing the transition from Batch Export to Real-time Log Streaming (Subscription Filters).
* **Network Security:** Configuring Lambda networking (ENI) to ensure secure data ingestion within VPC.
* **Advanced R&D (NLP):** Deep diving into Natural Language Processing (Vector Spaces & Probabilistic Models) for semantic log analysis.
* **Industry Engagement:** Updating knowledge on AWS DevOps, IaC, and Container services via technical workshops.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| :--- | :--- | :--- | :--- | :--- |
| **Mon (25/11)** | **Architectural Pivot (Batch to Streaming)**<br>- **Failure Analysis:** Abandoned the *CloudWatch to S3 to Lambda* (Batch) approach due to API limits and high latency.<br>- **Success:** Implemented **CloudWatch Subscription Filters** to trigger Lambda directly (*CloudWatch to Lambda to S3*).<br>- **Benefit:** Achieved near real-time data ingestion latency. | 25/11/2025 | 25/11/2025 | [Subscription Filters](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/SubscriptionFilters.html)<br>[Real-time Log Processing](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/SubscriptionFilters.html#LambdaFunctionExample) |
| **Tue (26/11)** | **Stream Processing Logic (Lambda)**<br>- **Data Handling:** Updated Lambda code to handle the streaming payload (Base64 encoded & Gzip compressed) from CloudWatch.<br>- **Transformation:** Parsed raw log events and formatted them into JSON lines before buffering. | 26/11/2025 | 26/11/2025 | [Decompressing Log Data](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/SubscriptionFilters.html) |
| **Wed (27/11)** | **Network Optimization & NLP Part 1**<br>- **Infrastructure:** Configured **Lambda ENI** to securely access S3 buckets within the VPC (using Gateway Endpoints).<br>- **Coursework:** Completed **NLP: Classification and Vector Spaces**. Studied how to represent text logs as vectors for machine learning models. | 27/11/2025 | 27/11/2025 | [Lambda VPC Access](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html)<br>[NLP Course 1](https://www.coursera.org/programs/fptu-fall-2025-zmahp/learn/classification-vector-spaces-in-nlp) |
| **Thu (28/11)** | **Advanced Analytics R&D (NLP Part 2)**<br>- **Coursework:** Advanced to **NLP: Probabilistic Models**. Investigated Auto-correct and N-gram language models to detect anomalies in log sequences.<br>- **Application:** Evaluated potential integration of probabilistic models for predicting system failures based on log patterns. | 28/11/2025 | 28/11/2025 | [NLP Course 2](https://www.coursera.org/programs/fptu-fall-2025-zmahp/learn/probabilistic-models-in-nlp) |
| **Fri (29/11)** | **Workshop & Capstone Planning**<br>- **Event:** Attended **"AWS Cloud Mastery Series #3 - Security Pillar Workshop"**.<br>- **Key Topics:** CI/CD Pipeline, Infrastructure as Code (IaC), Container Services, and Observability.<br>- **Capstone:** Researched technical proposal structures and started drafting the **Final Project Proposal**. | 29/11/2025 | 29/11/2025 |  |

### Week 12 Achievements:

* **Successfully Architected a Real-time Pipeline:**
    * Validated that the **Streaming Pattern** (Subscription Filter) is superior to the **Batch Pattern** (Export Task) for this specific use case.
    * Reduced data ingestion latency from minutes/hours to **milliseconds**.

* **Advanced Skill Acquisition (AI/ML):**
    * Laid a strong academic foundation in **Natural Language Processing** (Vector Spaces, Probabilistic Models), preparing for the implementation of "Smart Log Analysis" features.

* **Broadened Cloud Competency:**
    * Gained comprehensive insights into the **DevOps ecosystem** on AWS (CI/CD, IaC, Containers) through the Cloud Mastery workshop, supporting the operational strategy for the final project.
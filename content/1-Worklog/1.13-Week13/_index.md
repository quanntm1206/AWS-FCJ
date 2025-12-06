---
title: "Week 13 Worklog"
date: "2025-12-01"
weight: 13
chapter: false
pre: " <b> 1.13. </b> "
---

### Week 13 Objectives:

* **Advanced Analytics Optimization:** Implementing **Athena Partition Projection** to automate partition management and improve query performance.
* **Pipeline Refinement:** Migrating from SQS polling to **Amazon Kinesis Data Firehose** to resolve high-concurrency invocation issues.
* **AI/ML Deep Dive:** Mastering Sequence Models and Attention Mechanisms in NLP; exploring Agentic AI with Amazon Bedrock.
* **Capstone Preparation:** Finalizing presentation materials for the internship defense.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| :--- | :--- | :--- | :--- | :--- |
| **Mon (01/12)** | **Project Management & NLP Study (Part 3)**<br>- **Milestone:** Submitted Final Project Proposal to the team for peer review.<br>- **Coursework:** Advanced to **NLP: Sequence Models**. Studied RNNs (Recurrent Neural Networks) for processing sequential log data. | 01/12/2025 | 01/12/2025 | [NLP Course 3](https://www.coursera.org/programs/fptu-fall-2025-zmahp/learn/sequence-models-in-nlp) |
| **Tue (02/12)** | **Operational Enablement & Lambda Refactoring**<br>- **Knowledge Sharing:** Produced a Video Tutorial on creating Slack Webhooks for ChatOps.<br>- **Code Update:** Reconfigured **Lambda ENI** logic to align output format with the new Athena schema requirements. | 02/12/2025 | 02/12/2025 | N/A |
| **Wed (03/12)** | **Pipeline Optimization (Firehose & Athena)**<br>- **Problem:** SQS-triggered Lambda incurred excessive GET requests/invocations.<br>- **Solution:** Pivoted to **Kinesis Data Firehose** for batching and buffering data before S3 ingestion.<br>- **Athena Optimization:** Implemented **Partition Projection** for VPC Logs to automate partition management without `MSCK REPAIR TABLE`. | 03/12/2025 | 03/12/2025 | [Athena Partition Projection](https://docs.aws.amazon.com/athena/latest/ug/partition-projection.html) |
| **Thu (04/12)** | **Workshop Content Development**<br>- **Task:** Drafted the "Data Module" for the team's internal workshop.<br>- **Content:** Detailed the end-to-end flow of log data from ingestion (Firehose) to analysis (Athena). | 04/12/2025 | 04/12/2025 | N/A |
| **Fri (05/12)** | **Industry Engagement: GenAI & Agentic AI**<br>- **Event:** Attended **"BUILDING AGENTIC AI - Context Optimization with Amazon Bedrock"**.<br>- **Key Takeaway:** Learned about RAG (Retrieval-Augmented Generation) and context management for AI Agents.<br>- **Action:** Continued developing workshop materials. | 05/12/2025 | 05/12/2025 | [Amazon Bedrock](https://aws.amazon.com/bedrock/) |
| **Sat (06/12)** | **Advanced AI Research & Final Prep**<br>- **Coursework:** Progressed to **NLP: Attention Models** (Transformers/Self-Attention).<br>- **Presentation:** Designed the **Final Defense Slides**, visualizing the architectural evolution (Batch $\to$ Streaming) and key technical achievements. | 06/12/2025 | 06/12/2025 | [NLP Course 4](https://www.coursera.org/programs/fptu-fall-2025-zmahp/learn/attention-models-in-nlp) |

### Week 13 Achievements:

* **Solved High-Scale Data Ingestion Issues:**
    * Diagnosed the bottleneck with SQS polling (High GET requests) and successfully re-architected the pipeline using **Kinesis Data Firehose**, reducing API costs and improving throughput.

* **Mastered Athena Advanced Features:**
    * Successfully implemented **Partition Projection** (via DDL `TBLPROPERTIES`), eliminating the operational overhead of manually adding partitions. This ensures queries on `vpc-logs` are always up-to-date and performant.

* **Project Completion Readiness:**
    * Bridged the gap between traditional NLP and modern Generative AI, while simultaneously finalizing the documentation and presentation materials for the project defense.
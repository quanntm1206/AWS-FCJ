---
title: "Week 6 Worklog"
date: "2000-01-01"
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Week 6 Objectives:

* **Database Fundamentals:** Reviewing core concepts like Normalization, Indexing, and ACID vs. BASE models.
* **Managed Relational Databases:** Mastering Amazon RDS and Aurora architecture.
* **Static Web Hosting:** Deploying static websites on S3 and securing them with Public Access Block configurations.
* **Content Delivery Network (CDN):** Analyzing architectural constraints when integrating CloudFront with S3 Website Endpoints.
* **Incident Management:** Documenting infrastructure dependencies and resolving configuration conflicts.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (13/10) | **Module 6 Theory: AWS Database Services** <br> - **Core Concepts:** RDBMS vs. NoSQL, PK/FK, Indexing, Partitioning. <br> - **RDS & Aurora:** Automated backups, Multi-AZ for HA, Read Replicas. <br> - **Redshift & ElastiCache:** Data Warehousing and In-memory caching strategies. | 13/10/2025 | 13/10/2025 | [Module 06-01](https://youtu.be/OOD2RwWuLRw?si=zjAdvLgGv-_4N0Py) <br> [Module 06-02](https://youtu.be/qbrobQZrokY?si=HGRY-XhKWkr83Fod) <br> [Module 06-03](https://youtu.be/UvdiRW34aNI?si=vc11G0NB6erHFvRQ) |
| Tue (14/10) | **Lab 43: Planned Execution & Incident Report** <br> - **Activity:** Scheduled execution of Lab 43. <br> - **Incident:** Documentation portal service unavailable (HTTP 5xx/Timeout). <br> - **Action:** Flagged as "External Dependency Failure". Documented the outage and pivoted to self-study on related AWS concepts pending resolution. | 14/10/2025 | 14/10/2025 | https://000043.awsstudygroup.com/ |
| Wed (15/10) | **Lab 57: S3 Static Website & CloudFront Integration** <br> - **Part 1 (Success):** Completed S3 setup, enabled Static Website Hosting, configured Bucket Policy for public read access (Steps 1-6). <br> - **Part 2 (Critical Issue):** Attempted to accelerate site with CloudFront (Step 7.2). <br> - **Root Cause Analysis:** Identified architectural conflict: The tutorial instructed using **OAI/OAC** with an **S3 Website Endpoint**, which is unsupported by AWS. <br> - **Resolution Strategy:** Determined that S3 Website Endpoints must be treated as "Custom Origins" (without OAC), or switch to standard S3 Origin to use OAC. | 15/10/2025 | 15/10/2025 | https://000057.awsstudygroup.com/ |
| Thu (16/10) | **Documentation Refinement** <br> - **Task:** Refactored weekly worklogs to align with professional reporting standards (Markdown/Hugo). <br> - **Goal:** Improved readability, structure, and consistency across all previous reports. | 16/10/2025 | 16/10/2025 |  |
| Fri (17/10) | **Family matters**  | 17/10/2025 | 18/10/2025 |  |


### Week 6 Achievements:

* **Deep Dive into CloudFront Architectures:**
    * Successfully deployed a Static Website on Amazon S3 with public read permissions.
    * **Crucial Learning:** Discovered that **Origin Access Control (OAC)** is NOT compatible with **S3 Website Endpoints**.
    * Analyzed the difference between **S3 REST API Endpoints** (supports OAC/OAI for security) vs **S3 Website Endpoints** (requires Custom Origin config).

* **Incident & Risk Management:**
    * Demonstrated adaptability by handling external documentation failures (Lab 43) without halting progress.
    * Validated lab instructions against official AWS Documentation to identify critical configuration errors before deployment.

* **Professional Documentation:**
    * Standardized the entire internship worklog, ensuring a clean, maintainable, and professional presentation format using Markdown.
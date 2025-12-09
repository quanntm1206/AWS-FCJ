---
title: "Week 5 Worklog"
date: "2000-01-01"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* **Cloud Compliance:** Understanding financial security standards (OSPAR) and AWS compliance scope.
* **Identity & Access Management (IAM):** Troubleshooting Trust Relationships and mastering Permission Boundaries.
* **Advanced Access Control:** Implementing Attribute-Based Access Control (ABAC) and Context-Aware Security (IP/Time conditions).
* **Data Security:** Encrypting data at rest with AWS KMS and auditing access via CloudTrail & Athena.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (6/10) | **Compliance Research (Blog 3):** <br> - **Topic:** OSPAR 2025 Report & AWS Services Scope. <br> - **Task:** Translated Blog "OSPAR 2025 report now available with 170 services...". <br> - **Key Learnings:** Understanding security guidelines for financial institutions using cloud services. | 06/10/2025 | 06/10/2025 | [Original Blog](https://aws.amazon.com/vi/blogs/security/ospar-2025-report-now-available-with-170-services-in-scope-based-on-the-newly-enhanced-ospar-v2-0-guidelines/) <br> [My Translation](https://docs.google.com/document/d/13-kZadS-z_8CVrHl8gdwBpnqOZeLTsWN71rHNkkYto4/edit?tab=t.0#heading=h.klgwyn9uayj) |
| Tue (7/10) | **Module 5 Theory:** <br> - Study IAM core concepts: Users, Groups, Roles, Policies. <br> - Analyze Shared Responsibility Model & Policy Structure (Effect, Action, Resource, Condition). <br> - Research "Principle of Least Privilege" best practices. | 07/10/2025 | 07/10/2025 | [Module 05-01](https://youtu.be/tsobAlSg19g) <br> [Module 05-02](https://youtu.be/N_vlJGAqZxo) <br> [Module 05-03](https://youtu.be/pZ2fgEFK3Vs) <br> [Module 05-04](https://youtu.be/5oQY8Rogz9Y) <br> [Module 05-05](https://youtu.be/NW1xrMkNMjU?si=W15z-7egjukm0Wih) <br> [Module 05-06](https://www.youtube.com/watch?v=GMihNQojhZc&t=1s) <br> [Module 05-07](https://youtu.be/clj2E0rNBEs?si=sOugbG2fLHk1XI7R) <br> [Module 05-08](https://youtu.be/0SdpD2GPYz4?si=UB09iE84xU7BSVky) |
| Wed (8/10) | **Lab 18 & Lab 22: Security Hub & IAM Troubleshooting** <br> - **Lab 18:** Enabled AWS Security Hub to automate security checks. <br> - **Lab 22:** Fixed Role assumption failure by modifying the **Trust Policy** to allow the correct Principal. | 08/10/2025 | 09/10/2025 | https://000018.awsstudygroup.com/ <br> https://000022.awsstudygroup.com/ |
| Fri (10/10) | **Lab 27 & 28: Resource Tagging & Access Control** <br> - **Lab 27:** Organized EC2 instances using Tags and created Resource Groups for efficient filtering. <br> - **Lab 28 (ABAC):** Configured IAM Policies to restrict EC2 actions based on Tags. <br>&emsp; + *Test:* Verified user access rights across Regions (Tokyo vs N. Virginia) based on Tag matching. | 10/10/2025 | 10/10/2025 | https://000027.awsstudygroup.com/ <br> https://000028.awsstudygroup.com/ |
| Sat (11/10) | **Lab 30, 33 & 44: Advanced Governance & Context Security** <br> - **Lab 30:** Implemented **IAM Permission Boundaries** to strictly limit maximum user privileges. <br> - **Lab 33:** Encrypted S3 data using AWS KMS and audited decryption events via Athena. <br> - **Lab 44:** Configured **IAM Roles with Conditions** to restrict access based on specific Source IPs and Time windows (e.g., Office hours only). | 11/10/2025 | 12/10/2025 | https://000030.awsstudygroup.com/ <br> https://000033.awsstudygroup.com/ <br> https://000044.awsstudygroup.com/ |


### Week 5 Achievements:

* **Implemented Context-Aware Security:**
    * Moved beyond standard permissions by applying **IAM Conditions** (Lab 44), successfully restricting Admin Roles to be assumable only from specific trusted IP addresses and within designated timeframes.

* **Strengthened Security Governance:**
    * Applied **IAM Permission Boundaries** (Lab 30) to create a "ceiling" for permissions, preventing delegated administrators from escalating their own privileges.
    * Implemented **Attribute-Based Access Control (ABAC)** (Lab 28) using Resource Tags for dynamic permission management.

* **Data Encryption & Auditing:**
    * Secured sensitive data in S3 using **AWS KMS** (Lab 33) for encryption at rest.
    * Integrated **CloudTrail** and **Athena** to perform forensic analysis, tracking exactly who accessed the encrypted data and when.
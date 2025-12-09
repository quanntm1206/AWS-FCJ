---
title: "Week 3 Worklog"
date: "2000-01-01"
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* **Security Best Practices:** Transitioning from long-term Access Keys to IAM Roles (IMDSv2) for EC2 security.
* **Hybrid Storage & Migration:** Implementing Hybrid Cloud solutions using Storage Gateway and VM Import/Export.
* **Data Protection Strategy:** Automating centralized backups with AWS Backup and mastering Disaster Recovery (RTO/RPO).
* **Advanced Storage:** Mastering S3 Storage Classes, Lifecycle Management, and the Snow Family.
* **Incident Management:** Real-world experience in troubleshooting account suspension and working with AWS Support.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (22/9) | **Lab 48: Granting authorization for an application to access AWS services with an IAM role.** <br> - **Scenario 1:** Configure AWS CLI using Access Key/Secret Key (Simulating legacy method). <br> - **Scenario 2 (Best Practice):** Create IAM Role with S3 Policy and attach to EC2 to leverage Instance Metadata (IMDSv2). <br> - **Audit:** Review CloudTrail for credential usage. | 22/09/2025 | 22/09/2025 | https://000048.awsstudygroup.com/ |
| Tue (23/9) | **Lab 24: Using File Storage Gateway** <br> - Deploy File Gateway Appliance on EC2. <br> - Configure NFS/SMB file shares mapping directly to an S3 Bucket. <br> - **Verification:** Mount file shares on a client machine and test read/write latency. | 23/09/2025 | 23/09/2025 | https://000024.awsstudygroup.com/ |
| Wed (24/9) | **Lab 25: Amazon FSx for Windows File Server** <br> - **Lab 25:** Troubleshoot and fix CloudFormation templates for stack deployment. <br> - **Incident:** AWS Account suspended unexpectedly. <br> - **Action:** Submitted Support Ticket #1 regarding account status and billing verification. | 24/09/2025 | 24/09/2025 | https://000025.awsstudygroup.com/ |
| Thu (25/9) | **Module 4: S3 Core Concepts & Hybrid Storage** <br> - **Architecture:** S3 Buckets, Objects, and 11-nines Durability (Multi-AZ). <br> - **Storage Classes:** Analyze cost/performance trade-offs: Standard, Intelligent-Tiering, Standard-IA, One Zone-IA, and Glacier/Deep Archive. <br> - **Snow Family & Gateway:** Study offline data migration tools (Snowball Edge) and Storage Gateway Types (File/Volume/Tape). <br> - **Disaster Recovery:** Define RTO/RPO and compare DR strategies (Pilot Light vs Warm Standby). | 25/09/2025 | 25/09/2025 | [Module 04-01](https://youtu.be/hsCfP0IxoaM?si=MUhp_BIJabumvMNc) <br> [Module 04-02](https://youtu.be/_yunukwcAwc?si=eFjVimOndHJO2_x1) <br> [Module 04-03](https://youtu.be/mPBjB6Ltl_Q?si=5kiObguWl9zNLOUJ) <br> [Module 04-04](https://youtu.be/YXn8Q_Hpsu4?si=ZGjYozwcw6693G8i) |
| Fri (26/9) | **Lab 13: Deploy AWS Backup to the System** <br> - **Automation:** Create a centralized Backup Plan for EBS, RDS, and EFS resources. <br> - **Notifications:** Configure SNS topics to alert administrators on backup status. <br> - **Validation:** Perform a "Test Restore" to verify data integrity and RTO capabilities. | 26/09/2025 | 26/09/2025 | https://000013.awsstudygroup.com/ |
| Sat (27/9) | **Lab 14: VM Import/Export** <br> - **Preparation:** Setup VMWare Workstation and AWS CLI environment. <br> - **Migration:** Export local VM image and upload to S3 Bucket. <br> - **Deployment:** Import VM image as an AMI and launch a new EC2 instance (Simulating "Lift and Shift" migration). | 27/09/2025 | 27/09/2025 | https://000014.awsstudygroup.com/ |


### Week 3 Achievements:

* **Implemented Least Privilege Security Model:**
    * Successfully migrated an application from using hard-coded **Access Keys** to using **IAM Roles**.
    * Verified that using IAM Roles eliminates the risk of credential leakage and simplifies key rotation.

* **Hybrid Cloud & Migration Competency:**
    * Configured **Storage Gateway** to extend on-premise storage to S3 seamlessly.
    * Successfully executed a **Lift-and-Shift Migration** (Lab 14) by importing a local Virtual Machine into AWS EC2, validating the path for migrating legacy workloads.

* **Automated Data Protection & Resilience:**
    * Deployed a centralized **AWS Backup** strategy (Lab 13) covering multiple resource types (EBS, RDS).
    * Validated Disaster Recovery readiness by performing successful restore tests and setting up **SNS Notifications** for proactive monitoring.

* **Incident Management Experience:**
    * Gained practical experience in dealing with critical **Account Suspension** issues.
    * Learned the procedure to effectively communicate with AWS Support, providing necessary logs and verification documents to restore service.
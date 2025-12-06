---
title: "Week 2 Worklog"
date: "2000-01-01"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* **Compute & Storage Mastery:** Deep dive into EC2 families, Pricing models, and Storage solutions (EBS, EFS, FSx).
* **Database & Migration:** Understanding RDS integration and Lift-and-Shift migration tools (MGN).
* **Advanced Lab 5:** Deploying a 2-tier application (Node.js + RDS) on Amazon Linux 2023 with strict troubleshooting.
* **Cost & Security:** Implementing IAM policies for cost control and resource restriction.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (15/9) | **Module 3: EC2 Deep Dive, Storage & Migration** <br> - Analyze Instance families (Intel/AMD vs Graviton/ARM) and Nitro Hypervisor benefits. <br> - Compare Pricing Models: On-Demand, Reserved, Savings Plans, and Spot Instances (Auto Scaling integration). <br> - **Storage:** Differentiate EBS (Persistent) vs Instance Store (Ephemeral/NVMe). Learn use cases for EFS (Linux shared) vs FSx (Windows/HPC). <br> - **Migration:** Study AWS MGN (Application Migration Service) for continuous replication and cutover. | 15/09/2025 | 16/09/2025 | [Module 03-01](https://youtu.be/-t5h4N6vfBs?si=3XX1N0oZI8bndOxK) <br> [Module 03-01-01](https://youtu.be/e7XeKdOVq40?si=6mI_xS_XKjEhwLax) <br> [Module 03-01-02](https://youtu.be/yAR6QRT3N1k?si=ZDgGBWoLCkIoJEvi) <br> [Module 03-01-03](https://youtu.be/hKr_TfGP7NY?si=tuFUwHJ5wdKJGs0X) <br> [Module 03-01-04](https://youtu.be/6IHNDJ85aoQ?si=BlBvt0hONt5SKsTD) <br> [Module 03-01-05](https://youtu.be/_v_43Wi7zjo?si=6skGCPHSBU2xeJRV) <br> [Module 03-01-06](https://youtu.be/Ew3QRaKJQSA?si=yjHJyTCDH9cK_iXq) <br> [Module 03-01-07](https://youtu.be/bbLcPitXJSY?si=ATvs418bGA-SFuAl) <br> [Module 03-02](https://youtu.be/hFVYG8WqfU0?si=bP8gy4OhylbDx6u1) |
| Wed (17/9) | **EC2 Management & Security:** <br> - **Practice:** Create Custom AMI, EBS Snapshots, and test Instance Recovery. <br> - **Cost Control:** Configure IAM Policies to restrict Regions, Instance Types, and enforce IP/Time-based rules. | 17/09/2025 | 17/09/2025 | |
| Thu (18/9) | **Lab 5: Amazon Relational Database Service (Amazon RDS)** <br> - Design VPC network and Security Groups (EC2 & RDS communication). <br> - Provision RDS (MySQL) and Amazon Linux 2023 instance (switched to `t3.micro` due to `t2.micro` unavailability). <br> - Troubleshoot Customer Gateway timeouts during SSH setup. <br> - **App Deployment:** Setup Node.js User Management App. <br> - **Troubleshooting:** <br>&emsp; + Fix `npm start` error (updated `package.json`). <br>&emsp; + Resolve MySQL installation failure on AL2023 by connecting directly to RDS endpoint. <br>&emsp; + Create DB Users and grant permissions via SQL commands. <br> - Explore Amazon Lightsail for simplified virtual server needs. <br> - Review deployment procedures for both Windows Server 2022 and Linux. <br> - Cleanup resources to prevent billing leakage. | 18/09/2025 | 20/09/2025 | https://000005.awsstudygroup.com/ |


### Week 2 Achievements:

* **Successfully Completed Lab 5 (2-Tier Architecture):**
    * Deployed a fully functional Node.js application connected to an RDS MySQL database.
    * Verified full application functionality (Register/Login/Data Retrieval) after resolving connectivity issues.

* **Solved Compatibility Issues on Amazon Linux 2023:**
    * Adapted to infrastructure constraints by upgrading from `t2.micro` to `t3.micro`.
    * Identified that `mysql-community-server` and `mariadb105` were unstable/missing on AL2023.
    * Re-architected the database connection to point directly to the **RDS Endpoint**, bypassing local proxy issues.

* **Advanced EC2 & Database Management:**
    * Mastered the creation of **Custom AMIs** and **EBS Snapshots** for backup/recovery.
    * Successfully managed RDS Database users: Created specific app users (`appuser`) and granted granular privileges (`GRANT ALL`) for security.
    * Applied strict **IAM Policies** to limit resource creation (Region/Type restrictions), ensuring zero accidental costs.
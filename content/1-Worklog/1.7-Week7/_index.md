---
title: "Week 7 Worklog"
date: "2000-01-01"
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Week 7 Objectives:

* **Advanced Networking:** Mastering VPC connectivity (Peering vs. Transit Gateway) and Hybrid DNS resolution.
* **Security Best Practices:** Implementing IAM Roles for EC2 to enforce "Least Privilege" access.
* **Hybrid Storage:** Deploying storage solutions for Windows workloads (FSx) and extending on-premise storage to cloud (Storage Gateway).
* **Data Protection & Migration:** Automating centralized backups and executing "Lift-and-Shift" VM migrations.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon (20/10) | **Networking Basics & Security** <br> - **Lab 19 (VPC Peering):** Established direct network connection between two VPCs, configured Route Tables, and enabled Cross-Peer DNS Resolution. <br> - **Lab 48 (IAM Roles):** Replaced hard-coded Access Keys with IAM Roles attached to EC2 instances to secure application access to S3. | 22/09/2025 | 22/09/2025 | https://000019.awsstudygroup.com/ <br> https://000048.awsstudygroup.com/ |
| Tue (21/10) | **Lab 20: Advanced Networking with Transit Gateway** <br> - **Architecture:** Implemented a Hub-and-Spoke topology connecting 4 VPCs using a single Transit Gateway (TGW). <br> - **Routing:** Configured TGW Route Tables to centralize traffic management, replacing complex mesh peering connections. | 23/09/2025 | 23/09/2025 | https://000020.awsstudygroup.com/ |
| Wed (22/10) | **Lab 10: Hybrid Connectivity with Route 53 Resolver** <br> - **Hybrid DNS:** Configured Inbound and Outbound Endpoints to resolve domain names between AWS VPCs and On-premise networks. <br> - **Integration:** Deployed Microsoft Active Directory to simulate on-premise DNS resolution. | 24/09/2025 | 24/09/2025 | https://000010.awsstudygroup.com/ |
| Thu (23/10) | **Lab 25: Amazon FSx for Windows File Server** <br> - **Deployment:** Created a fully managed Native Windows File System integrated with Microsoft Active Directory. <br> - **Features:** Mapped SMB file shares to Windows instances and enabled Data Deduplication/Shadow Copies for storage efficiency. | 25/09/2025 | 25/09/2025 | https://000025.awsstudygroup.com/ |
| Fri (24/10) | **Hybrid Storage & Backup Automation** <br> - **Lab 24 (Storage Gateway):** Deployed File Gateway to map local NFS/SMB shares directly to S3 buckets for limitless cloud storage extension. <br> - **Lab 13 (AWS Backup):** Created a centralized Backup Plan to automate protection for EBS, RDS, and EFS resources with SNS notifications. | 26/09/2025 | 26/09/2025 | https://000024.awsstudygroup.com/ <br> https://000013.awsstudygroup.com/ |
| Sat (25/10) | **Lab 14: Migration Strategy (Lift & Shift)** <br> - **VM Import/Export:** Exported a local Virtual Machine (VMware), uploaded image to S3, and converted it into an Amazon Machine Image (AMI). <br> - **Validation:** Launched a new EC2 instance from the imported AMI, verifying the workload migration capability. | 27/09/2025 | 27/09/2025 | https://000014.awsstudygroup.com/ |


### Week 3 Achievements:

* **Designed Scalable Network Architectures:**
    * Transitioned from simple **VPC Peering** (Lab 19) to scalable **Transit Gateway** architectures (Lab 20), significantly reducing routing complexity for multi-VPC environments.
    * Solved the **Hybrid DNS** challenge using **Route 53 Resolver**, enabling seamless service discovery between Cloud and On-premise.

* **Mastered Storage & Data Protection:**
    * Implemented specialized storage for Windows workloads using **Amazon FSx** and extended on-prem capacity using **Storage Gateway**.
    * Established a robust Disaster Recovery foundation by automating backups via **AWS Backup**.

* **Executed Cloud Migration:**
    * Successfully performed a **"Lift and Shift" migration** (Lab 14), validating the technical path for moving legacy virtual machines to AWS EC2 without re-architecting.
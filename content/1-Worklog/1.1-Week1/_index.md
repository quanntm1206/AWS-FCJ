---
title: "Week 1 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

* **Cloud Fundamentals:** Understand AWS Global Infrastructure, Pricing, Support Plans, and basic security (IAM).
* **Networking Core:** Master VPC architecture (Subnets, Routing, Security Groups/NACLs) and Load Balancing.
* **Hands-on Labs:** Account setup, Cost management, VPC construction, and troubleshooting VPN connections.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Tue (9/9) | **Module 1 & Labs 1, 7, 9:** <br> - **Theory:** Cloud Computing concepts, Regions/AZs, Cost Optimization (Budgets), Support Plans. <br> - **Practice:** <br>&emsp; + Create & Secure AWS Account (MFA, IAM User). <br>&emsp; + Configure AWS Budgets (Cost, Usage, RI). <br>&emsp; + Open Support Cases. | 09/09/2025 | 09/09/2025 | https://youtu.be/HxYZAK1coOI?si=4xf1yZmepR82emMd <br> https://youtu.be/IK59Zdd1poE?si=X5Qao9OxMLUvpBYg <br> https://youtu.be/HSzrWGqo3ME?si=r478_UihmyCTKcQ3 <br> https://youtu.be/pjr5a-HYAjI?si=_QqGDOBJy_1c6WUe <br> https://youtu.be/2PQYqH_HkXw?si=DKIEZLPrSbzEtRvh <br> https://youtu.be/IY61YlmXQe8?si=taziN3scWc-corP6 <br> https://youtu.be/Hku7exDBURo?si=715J5Yl4OjkLVEfj <br> https://000001.awsstudygroup.com/ <br> https://000007.awsstudygroup.com/ <br> https://000009.awsstudygroup.com/|
| Thu (11/9) | **Module 2 & Lab 3:** <br> - **Theory:** VPC, Subnets, Route Tables, IGW/NGW, Security (SG vs NACL), ELB (ALB/NLB/GLB). <br> - **Practice:** <br>&emsp; + Build a VPC network from scratch. <br>&emsp; + Launch EC2 (Amazon Linux 2023). <br>&emsp; + Successfully resolved connectivity issues. | 09/11/2025 | 09/11/2025 | https://youtu.be/O9Ac_vGHquM?si=1bFj633qq7EvfLhi <br> https://youtu.be/BPuD1l2hEQ4?si=LrrKAww4vVeK74eE <br> https://youtu.be/CXU8D3kyxIc?si=ju2OidhffNpSfWZ6 <br> https://000003.awsstudygroup.com/ |
| Sat (13/9) | **Lab 4: VPN Site-to-Site Setup** <br> - Configure Customer Gateway & VPN Tunnel. <br> - **Troubleshooting:** <br>&emsp; + Install `libreswan` for Amazon Linux 2023. <br>&emsp; + Adapt commands: use `systemctl` instead of `service`. <br>&emsp; + Note: Identified mismatch between guide and Console. | 09/13/2025 | 09/13/2025 | https://000004.awsstudygroup.com/ |


### Week 1 Achievements:

* **Mastered Cloud Fundamentals & Security:**
    * Understood the "Pay-as-you-go" model and AWS Global Infrastructure (Region, AZ, Edge Locations).
    * Secured the Root account with MFA and established IAM users for daily tasks.
    * Categorized Support Plans (Basic to Enterprise) and utilized AWS Budgets for cost control.

* **Deep Dived into Networking (VPC):**
    * Designed logically isolated networks using VPC, Subnets (Public/Private), and Route Tables.
    * Differentiated between Security Groups (Stateful) and NACLs (Stateless).
    * Understood connectivity options: IGW (Internet), NGW (Outbound only), and VPC Peering/Transit Gateway.

* **Practical Troubleshooting Experience:**
    * Successfully adapted to **Amazon Linux 2023** environment (switching from Amazon Linux 2).
    * Resolved service management differences (using `systemd-networkd` / `systemctl`).
    * Gained experience in configuring Site-to-Site VPN components (Customer Gateway).
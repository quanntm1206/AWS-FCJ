---
title: "Event 4"
date: "2025-11-29"
weight: 04
chapter: false
pre: " <b> 4.4</b> "
---

# Summary Report: “AWS Cloud Mastery Series #3: AWS Well-Architected – Security Pillar Workshop”

### Event Objectives

- Introduction to AWS Cloud Club
- Pillar 1: Identity and Access Management (IAM)
- Pillar 2: Detection and Continuous Monitoring
- Pillar 3: Infrastructure Protection
- Pillar 4: Data Protection
- Pillar 5: Incident Response

### Speakers

- **Le Vu Xuan An** - AWS Cloud Club Captain HCMUTE
- **Tran Duc Anh** - AWS Cloud Club Captain SGU
- **Tran Doan Cong Ly** - AWS Cloud Club Captain PTIT
- **Danh Hoang Hieu Nghi** - AWS Cloud Club Captain HUFLIT

- **Huynh Hoang Long** - AWS Community Builder
- **Dinh Le Hoang Anh** - AWS Community Builder

- **Nguyen Tuan Thinh** - Cloud Engineer Trainee
- **Nguyen Do Thanh Dat** - Cloud Engineer Trainee

- **Van Hoang Kha** - Cloud Security Engineer, AWS Community Builder

- **Thinh Lam** - FCJ Member
- **Viet Nguyen** - FCJ Member

- **Mendel Grabski (Long)** - Ex-Head of Security & DevOps, Cloud Security Solution Architect
- **Tinh Truong** - Platform Engineer at TymeX, AWS Community Builder 

### Key Highlights

### AWS Cloud Club
The session began with an introduction to the AWS Cloud Club, which is designed to:
- Facilitate the exploration and growth of cloud computing skills.
- Foster technical leadership.
- Build meaningful global connections.

The club provides hands-on AWS experiences, mentorship from AWS professionals, and long-term career support. The AWS Cloud Clubs associated with FCJA include:
- AWS Cloud Club HCMUTE
- AWS Cloud Club SGU
- AWS Cloud Club PTIT
- AWS Cloud Club HUFLIT

**Benefits:** Opportunities to build skills, engage with the community, and access career advancement.

### Identity & Access Management (IAM)
IAM is a fundamental AWS service responsible for controlling secure access. It manages Users, Groups, Roles, and Permissions, ensuring robust authentication and authorization.

- **Best Practices:**

    + **Least Privilege Principle:** Granting only the permissions necessary to perform a task.

    + **Root Access:** Deleting root access keys immediately after creation.

    + **Policy Precision:** Avoiding the use of wildcards ("*") in Actions or Resources.

    + **Single Sign-On (SSO):** Utilizing SSO for multi-account integration and centralized access management.

- **Service Control Policies (SCPs):** These are organization-level policies that define the maximum available permissions for all accounts within an organization. It is important to note that SCPs act as filters; they do not grant permissions.

- **Permission Boundaries:** These set the maximum permissions that an identity-based policy can grant to a specific User or Role within an account.

- **MFA:**
| TOTP (Time-based One-Time Password) | FIDO2 (Fast Identity Online 2) |
| :--- | :--- |
| **Shared secret** | **Public-key cryptography** |
| Requires manually typing a 6-digit code | Requires a simple touch or biometric scan |
| Free | Variable cost |
| Flexible backups and recovery | Strict backups and zero recovery |

- **Credential Rotation with AWS Secrets Manager:**
    + The Credential Updater utilizes Secrets Manager functions in a cycle: Create Secret, Set Secret (e.g., every 7 days), Test Secret, and Finish Secret.
    + Rotation events can be triggered via an EventBridge Schedule for precise timing control.
    + The process concludes by deprecating the previous secret.


### Detection and Continuous Monitoring
- **Multi-Layer Security Visibility:**
    + **Management Events:** Monitors API calls and console actions across all organization accounts.
    + **Data Events:** Tracks S3 object access and Lambda executions at scale.
    + **Network Activity Events:** Integrates VPC Flow Logs for network-level monitoring.
    + **Organization Coverage:** Ensures unified logging across all member accounts and regions.

- **Alerting & Automation with EventBridge:**

    + **Real-time Events:** CloudTrail events flow directly to EventBridge for immediate processing. This forms the foundation of Event-Driven Architecture (EDA), allowing systems to react instantaneously to changes.

    + **Automated Alerting:** Detects suspicious activities across all organization accounts.

    + **Cross-account Event Routing:** Facilitates centralized event processing and automated response. EventBridge seamlessly routes events based on rules to targets across different accounts or regions.

    + **Integration & Workflows:** Supports integration with Lambda, SNS, and SQS for automated security workflows.

- **Detection-as-Code:**
    
    + **CloudTrail Lake Queries:** Involves creating and using SQL-based detection rules for advanced threat hunting.

    + **Version-Controlled Logic:** Detection rules and logic are tracked and managed via code repositories.

    + **Automated Deployment:** Trails and detection rules are automatically deployed across all relevant organization accounts, ensuring uniform security coverage.

    + **Infrastructure-as-Code (IaC):** Utilizes IaC tools for the automated setup and configuration of the organization's logging and event trails.
### Guard Duty
- GuardDuty is an always-on, intelligent threat detection solution.

- **How GuardDuty Works:** It relies on continuous analysis of the **Three Pillars of Detection**:

| Data Source | What It Monitors | Real-World Example |
| :--- | :--- | :--- |
| **CloudTrail Events** | IAM actions, permission changes, API calls | Attacker disables logging to cover tracks. |
| **VPC Flow Logs** | Network traffic to/from your resources | EC2 sending data to a botnet C2 server. |
| **DNS Logs** | DNS queries from your infrastructure | Malware-infected queries to cryptomining sites. |

- **Advanced Protection Plans:** GuardDuty offers specialized detection add-ons for comprehensive coverage:

    + **S3 Protection:** Detects abnormal S3 access patterns and scans for malware in S3 objects upon upload.

    + **EKS Protection:** Monitors Kubernetes audit logs for unauthorized access and correlates findings with S3 to map the full attack path.

    + **Malware Protection:** Automatically scans EBS volumes of EC2 instances when a compromise is suspected.

    + **RDS Protection:** Analyzes login activity logs for databases (Aurora/RDS) to detect brute-force attacks (e.g., multiple failed login attempts from a single IP).

    + **Lambda Protection:** Monitors network logs from Lambda function invocations and detects if a compromised function is sending data to malicious IPs.

    + **Runtime Monitoring – Deep Inside Your OS:** Achieved using a GuardDuty Agent installed on EC2/EKS/ECS Fargate. It monitors running processes, file access patterns, system calls, and attempts at privilege escalation or reverse shells.

- **Compliance Standards:**

    + **AWS Foundational Security Best Practices:** Developed by AWS, covering a wide range of services.

    + **CIS AWS Foundations Benchmark:** Developed by AWS and industry professionals, focusing on Identity (IAM), Logging & Monitoring, and Networking.

- **Compliance Enforcement with Detection-as-Code:**

    + **IaC Tool:** AWS CloudFormation is used to deploy configurations.

    + **Compliance Engine:** AWS CloudFormation pushes configuration checks to AWS Security Hub CSPM.

    + **Compliance Standards Applied:** Security Hub performs checks against listed standards (AWS Foundational Security Best Practices, CIS AWS Foundations Benchmark, PCI DSS, NIST).

    + **Resources Covered:** Amazon S3, Amazon EC2, and Amazon RDS.

### Network Security Controls

- **Attack Vectors:** Threats are categorized into Ingress Attacks (e.g., DDoS, SQL injection), Egress Attacks (e.g., data exfiltration, DNS tunneling), and Inside Attacks (e.g., lateral movement).

- **Security Groups (SG):** Act as stateful firewalls at the instance/interface level. They only support allow rules and include an implicit "deny all."

- **Network ACLs (NACLs):** Operate at the subnet level. They are stateless and use numbered rules to explicitly ALLOW or DENY traffic.

- **AWS TGW Security Group Referencing:** Allows Transit Gateway (TGW) VPCs to define inbound rules using only SG references.

- **Route 53 Resolver:** Routes DNS queries to Private DNS (private hosted zones), VPC DNS, or Public DNS.

- **AWS Network Firewall:**

    + **Use Cases:** Egress filtering (blocking bad domains, malicious protocols), environment segmentation (VPC to VPC), and intrusion prevention (IDS/IPS rules).

    + **Active Defense:** Can automatically block malicious traffic using Amazon Threat Intelligence, where GuardDuty findings are marked for automated blocking.

### Data Protection & Governance

- **Encryption (KMS):** Data is encrypted using a Data Key, which is protected by a Customer Master Key (CMK). KMS policies enforce a second layer of security with Condition keys to define *when* encryption/decryption is allowed.

- **Certificate Management (ACM):** Provides free public certificates and automatically renews them 60 days before expiration. DNS Validation is the recommended method.

- **Secrets Manager:** Addresses the issue of hardcoded credentials. It uses a 4-step Lambda logic (createSecret, setSecret, testSecret, finishSecret) for automatic credential rotation without downtime.

- **API Service Security (S3 & DynamoDB):** S3 requires TLS 1.2+ and bucket policies with `aws:SecureTransport` for enforcement. DynamoDB is secure by default with mandatory HTTPS.

- **Database Service Security (RDS):** Requires client-side trust in the AWS Root CA Bundle to verify server identity, and server-side enforcement (e.g., `rds.force_ssl=1` for PostgreSQL).

### Incident Response & Prevention

- **Prevention Best Practices:** Key steps include using temporary credentials, never exposing S3 buckets directly, placing sensitive services within private subnets, managing all resources through Infrastructure as Code, and utilizing double-gate verification for high-risk changes (PR approval, pipeline deployment).

- **Incident Response Process:** A structured 5-step approach: Preparation, Detection & Analysis, Containment (isolate, revoke credentials), Eradication & Recovery, and Post-Incident (lessons learned).


### Event Experience

- This event was extremely useful for our team, aligning directly with our project on Automated Incident Response and Forensics.

- **Q:** Our team's project is an Automated Incident Response and Forensics tool with GuardDuty as the main focus for incident response. However, our testing indicates that GuardDuty can take up to 5 minutes to generate a finding when an incident occurs. Are there any solutions to reduce this latency?

- **A:** The 5-minute delay for GuardDuty to generate findings is inherent to its configuration, as it must process a large volume of security data to accurately determine threats. To reduce latency, you might consider integrating 3rd-party security services such as Open Clarity Free for near real-time findings. Additionally, CloudTrail can be used to detect anomalies and unusual user behavior more rapidly.

- Mr. Mendel Grabski was very keen to offer his support when we discussed our project after the event.

#### Some event photos

![All Attendee Picture](/images/4-Event/Event6AttendeePic.jpg)
_Picture of all Attendees_

![Group Picture With Speaker Mendel Grabski and Speaker Van Hoang Kha](/images/4-Event/Event6PicturewithSpeakers.jpg)
_Group Picture With Speaker Mendel Grabski and Speaker Van Hoang Kha_
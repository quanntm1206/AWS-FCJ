---
title: "Event 4"
date: "2025-11-29"
weight: 4
chapter: false
pre: " <b> 4.4.</b> "
---

# Summary Report: “AWS Cloud Mastery Series #3: AWS Well-Architected – Security Pillar Workshop”

## Event Objectives

- **Introduction to AWS Cloud Club:** Establishing the community's mission and scope.
- **Pillar 1: Identity and Access Management (IAM):** Mastering access control and authorization.
- **Pillar 2: Detection and Continuous Monitoring:** Implementing observability and automated alerting.
- **Pillar 3: Infrastructure Protection:** Securing network boundaries and compute resources.
- **Pillar 4: Data Protection:** Ensuring data confidentiality and integrity through encryption and governance.
- **Pillar 5: Incident Response:** Establishing protocols for preparing, responding to, and recovering from security incidents.

## Speakers

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

## Key Highlights

### AWS Cloud Club

The session commenced with an introduction to the AWS Cloud Club, an initiative designed to:
- Facilitate the exploration and cultivation of cloud computing skills.
- Foster technical leadership within the student community.
- Build meaningful, global professional connections.

The club provides members with hands-on AWS experiences, mentorship from seasoned AWS professionals, and long-term career support. The AWS Cloud Clubs associated with FCJA include chapters at HCMUTE, SGU, PTIT, and HUFLIT.

**Benefits:** Members gain significant opportunities to build practical skills, engage deeply with the community, and access pathways for career advancement.

### Identity & Access Management (IAM)

IAM serves as the fundamental AWS service responsible for controlling secure access. It manages Users, Groups, Roles, and Permissions, ensuring robust authentication and authorization mechanisms across the environment.



- **Best Practices:**
    + **Least Privilege Principle:** Granting only the specific permissions necessary to perform a task.
    + **Root Access:** Deleting root access keys immediately following account creation to prevent compromise.
    + **Policy Precision:** Avoiding the use of wildcards ("*") in Actions or Resources to minimize the attack surface.
    + **Single Sign-On (SSO):** Utilizing SSO for seamless multi-account integration and centralized access management.

- **Service Control Policies (SCPs):** These are organization-level policies that define the maximum available permissions for all accounts within an organization. It is crucial to note that SCPs act strictly as filters; they do not grant permissions themselves.

- **Permission Boundaries:** These allow administrators to set the maximum permissions that an identity-based policy can grant to a specific User or Role, providing a safety net against privilege escalation.

- **Multi-Factor Authentication (MFA):**

| Feature | TOTP (Time-based One-Time Password) | FIDO2 (Fast Identity Online 2) |
| :--- | :--- | :--- |
| **Mechanism** | **Shared secret** | **Public-key cryptography** |
| **User Interaction** | Requires manually typing a 6-digit code | Requires a simple touch or biometric scan |
| **Cost** | Free (Software-based) | Variable cost (Hardware-key) |
| **Recovery** | Flexible backups and recovery options | Strict backups and typically zero recovery if lost |

- **Credential Rotation with AWS Secrets Manager:**
    + The Credential Updater utilizes Secrets Manager functions in a cycle: *Create Secret* -> *Set Secret* (e.g., every 7 days) -> *Test Secret* -> *Finish Secret*.
    + Rotation events can be precisely triggered via an EventBridge Schedule.
    + The process concludes by deprecating the previous secret, ensuring invalidation of old credentials.

### Detection and Continuous Monitoring



- **Multi-Layer Security Visibility:**
    + **Management Events:** Monitors API calls and console actions across all organizational accounts.
    + **Data Events:** Tracks S3 object access and Lambda executions at scale.
    + **Network Activity Events:** Integrates VPC Flow Logs for granular network-level monitoring.
    + **Organization Coverage:** Ensures unified logging ingestion across all member accounts and regions.

- **Alerting & Automation with EventBridge:**
    + **Real-time Events:** CloudTrail events flow directly into EventBridge for immediate processing. This forms the foundation of Event-Driven Architecture (EDA), allowing systems to react instantaneously to state changes.
    + **Automated Alerting:** Detects and notifies on suspicious activities across the entire organization.
    + **Cross-account Event Routing:** Facilitates centralized event processing and automated response by routing events based on rules to targets in different accounts or regions.
    + **Integration & Workflows:** Supports seamless integration with Lambda, SNS, and SQS to trigger automated security workflows.

- **Detection-as-Code:**
    + **CloudTrail Lake Queries:** Involves creating and executing SQL-based detection rules for advanced threat hunting.
    + **Version-Controlled Logic:** Detection rules and logic are tracked, versioned, and managed via code repositories.
    + **Automated Deployment:** Trails and detection rules are automatically deployed across all relevant organization accounts via CI/CD pipelines.
    + **Infrastructure-as-Code (IaC):** Utilizes tools like CloudFormation or Terraform to automate the setup of the organization's logging and event trails.

### GuardDuty

GuardDuty is an always-on, intelligent threat detection solution that continuously monitors for malicious activity and unauthorized behavior.



- **How GuardDuty Works:** It relies on the continuous analysis of the **Three Pillars of Detection**:

| Data Source | What It Monitors | Real-World Example |
| :--- | :--- | :--- |
| **CloudTrail Events** | IAM actions, permission changes, API calls | An attacker disables logging to conceal their tracks. |
| **VPC Flow Logs** | Network traffic to/from your resources | An EC2 instance sending data to a known botnet C2 server. |
| **DNS Logs** | DNS queries from your infrastructure | Malware-infected queries attempting to resolve cryptomining sites. |

- **Advanced Protection Plans:** GuardDuty offers specialized detection add-ons for comprehensive coverage:
    + **S3 Protection:** Detects abnormal S3 access patterns and scans for malware in S3 objects upon upload.
    + **EKS Protection:** Monitors Kubernetes audit logs for unauthorized access and correlates findings with S3 to map the full attack path.
    + **Malware Protection:** Automatically scans EBS volumes of EC2 instances when a compromise is suspected.
    + **RDS Protection:** Analyzes login activity logs for databases (Aurora/RDS) to detect brute-force attacks.
    + **Lambda Protection:** Monitors network logs from Lambda function invocations to detect if a compromised function is communicating with malicious IPs.
    + **Runtime Monitoring:** Achieved using a GuardDuty Agent installed on EC2/EKS/ECS Fargate to monitor running processes, file access patterns, and system calls.

- **Compliance Standards:**
    + **AWS Foundational Security Best Practices:** A standard developed by AWS, covering a wide range of services.
    + **CIS AWS Foundations Benchmark:** A consensus-based guide developed by AWS and industry professionals, focusing on Identity (IAM), Logging & Monitoring, and Networking.

- **Compliance Enforcement with Detection-as-Code:**
    + **IaC Tool:** AWS CloudFormation is used to deploy configurations.
    + **Compliance Engine:** AWS CloudFormation pushes configuration checks to AWS Security Hub CSPM.
    + **Compliance Standards Applied:** Security Hub performs checks against listed standards (AWS Foundational, CIS, PCI DSS, NIST).
    + **Resources Covered:** Primarily Amazon S3, Amazon EC2, and Amazon RDS.

### Network Security Controls



- **Attack Vectors:** Threats are categorized into **Ingress Attacks** (e.g., DDoS, SQL injection), **Egress Attacks** (e.g., data exfiltration, DNS tunneling), and **Inside Attacks** (e.g., lateral movement).

- **Security Groups (SG):** Act as stateful firewalls at the instance/interface level. They only support "allow" rules and include an implicit "deny all" default.

- **Network ACLs (NACLs):** Operate at the subnet level as an additional layer of defense. They are stateless and use numbered rules to explicitly ALLOW or DENY traffic.

- **AWS TGW Security Group Referencing:** Allows Transit Gateway (TGW) VPCs to define inbound rules using only SG references, simplifying management in complex topologies.

- **Route 53 Resolver:** Routes DNS queries to Private DNS (private hosted zones), VPC DNS, or Public DNS based on rules.

- **AWS Network Firewall:**
    + **Use Cases:** Egress filtering (blocking malicious domains/protocols), environment segmentation (VPC to VPC), and intrusion prevention (IDS/IPS rules).
    + **Active Defense:** Can automatically block malicious traffic using Amazon Threat Intelligence, where GuardDuty findings are marked for automated blocking actions.

### Data Protection & Governance

- **Encryption (KMS):** Data is encrypted using a Data Key, which is in turn protected by a Customer Master Key (CMK) (Envelope Encryption). KMS policies enforce a second layer of security with Condition keys to define precisely *when* encryption/decryption is permitted.



- **Certificate Management (ACM):** Provides free public certificates and automatically renews them 60 days before expiration. DNS Validation is the recommended method for ownership verification.

- **Secrets Manager:** Addresses the security risk of hardcoded credentials. It uses a 4-step Lambda logic to perform automatic credential rotation without inducing downtime.

- **API Service Security (S3 & DynamoDB):** S3 requires TLS 1.2+ and bucket policies with `aws:SecureTransport` for enforcement. DynamoDB is secure by default, mandating HTTPS.

- **Database Service Security (RDS):** Requires client-side trust in the AWS Root CA Bundle to verify server identity, and server-side enforcement (e.g., setting `rds.force_ssl=1` for PostgreSQL).

### Incident Response & Prevention

- **Prevention Best Practices:** Key preventative measures include using temporary credentials, ensuring S3 buckets are never directly exposed to the internet, placing sensitive services within private subnets, managing all resources through Infrastructure as Code, and utilizing double-gate verification for high-risk changes (PR approval, pipeline deployment).

- **Incident Response Process:** A structured 5-step approach:
    1.  Preparation
    2.  Detection & Analysis
    3.  Containment (isolate resources, revoke credentials)
    4.  Eradication & Recovery
    5.  Post-Incident Activity (lessons learned and documentation).

## Event Experience

This workshop was highly pertinent to our team, as the content aligned directly with our ongoing project focused on Automated Incident Response and Forensics.

The speakers addressed several critical questions from our team:

- **Q:** Our team's project is an Automated Incident Response and Forensics tool utilizing GuardDuty as the primary trigger. However, our testing indicates that GuardDuty can take up to 5 minutes to generate a finding after an incident occurs. Are there solutions to mitigate this latency?
- **A:** The 5-minute delay for GuardDuty to generate findings is largely inherent to its configuration, as it must ingest and process a massive volume of security data to accurately determine threats. To reduce latency, you might consider integrating third-party security services, such as Open Clarity Free, for near real-time findings. Additionally, leveraging CloudTrail directly can help detect specific anomalies and unusual user behavior more rapidly than waiting for the aggregated GuardDuty finding.

Furthermore, Mr. Mendel Grabski graciously offered his support and mentorship when we discussed the specifics of our project following the event.

#### Some event photos

![All Attendee Picture](/images/4-Event/Event6AttendeePic.jpg)
_Picture of all Attendees_

![Group Picture With Speaker Mendel Grabski and Speaker Van Hoang Kha](/images/4-Event/Event6PicturewithSpeakers.jpg)
_Group Picture With Speaker Mendel Grabski and Speaker Van Hoang Kha_
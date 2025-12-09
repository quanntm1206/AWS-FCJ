---
title: "Event 3"
date: "2025-11-17"
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# Summary Report: “AWS Cloud Mastery Series #2 - DevOps on AWS”

## Event Objectives

- To introduce AWS DevOps Services, with a specific focus on CI/CD Pipelines.
- To provide a comprehensive overview of Infrastructure as Code (IaC) and its associated tools.
- To explore the various Container Services available within the AWS ecosystem.
- To ensure robust Monitoring and Observability capabilities using AWS Services.

## Speakers

- **Truong Quang Tinh** – AWS Community Builder, Platform Engineer - TymeX
- **Bao Huynh** – AWS Community Builder
- **Nguyen Khanh Phuc Thinh** – AWS Community Builder
- **Tran Dai Vi** – AWS Community Builder
- **Huynh Hoang Long** – AWS Community Builder
- **Pham Hoang Quy** – AWS Community Builder
- **Nghiem Le** – AWS Community Builder
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud AI Journey

## Key Highlights

### DevOps Mindset

**- Culture:** This concept encompasses collaboration, automation, continuous learning, and consistent measurement.
**- DevOps Roles:** Key positions include DevOps Engineer, Cloud Engineer, Platform Engineer, and Site Reliability Engineer (SRE).
**- Success Metrics:**
    + Ensuring deployment health.
    + Enhancing agility.
    + Maintaining system stability.
    + Optimizing the customer experience.
    + Justifying technology investments.

| DO | DON'T |
| :--- | :--- |
| Start with Fundamentals | Stay in "Tutorial Hell" |
| Learn by Building Real Projects | Copy-paste blindly |
| Document Everything | Compare Your Progress to Others |
| Master one thing at a time | Give Up After Failures |
| Soft Skills Enhancement | |

**- Continuous Integration:** A practice wherein team members frequently integrate their work, aiming to facilitate efficient Continuous Delivery and Deployment.

### Infrastructure as Code (IaC)

**- Benefits:** This approach offers automation, scalability, reproducibility, and significantly improved collaboration.

#### AWS CloudFormation

This constitutes AWS's native IaC solution. It utilizes templates written in YAML or JSON to automatically provision every component of the AWS infrastructure.

**- Stack:** A collection of AWS resources defined within a template, which CloudFormation allows users to create, update, or delete as a single unit.

**- CloudFormation Template:** A YAML or JSON file that acts as a blueprint for configuring and deploying resources, effectively defining the AWS infrastructure.

**- Workflow:** Create a template -> Store it in an S3 Bucket or local storage -> Use CloudFormation to create Stacks based on the template -> CloudFormation provisions the resources.

**- Drift Detection:** This feature identifies discrepancies between the actual infrastructure and the Stack configuration. It allows administrators to update the Stack or revert changes, which is essential for maintaining version control.

#### AWS Cloud Development Kit (CDK)

An open-source software development framework that supports IaC using standard programming languages, including Python, Java, C#.Net, TypeScript/JavaScript, and Go.

**- Construct:** These are the basic building blocks, comprised of components representing AWS resources and their configurations. There are three construct levels:
    + **L1 Construct:** Low-level resources that map directly to a single AWS CloudFormation resource.
    + **L2 Construct:** Provides a higher-level abstraction through an intuitive, intent-based API, encapsulating best practices and security defaults.
    + **L3 Construct:** Represents complete architectural patterns involving multiple resources, offering opinionated implementations for rapid deployment.

#### AWS Amplify

An AWS platform designed to facilitate the building, deploying, and scaling of web and mobile applications. It utilizes CloudFormation under the hood, deploying Stacks to build infrastructure programmatically.

#### Terraform

An IaC tool wherein infrastructure is defined through Terraform code. Users plan and subsequently apply the infrastructure across multiple cloud platforms, such as Azure, AWS, and Google Cloud.

**- Strength:** Its primary advantage lies in multi-cloud support and state tracking using a unified configuration.

#### How to Choose IaC Tools?
**- Criteria:**
    + Are you planning to utilize a single cloud provider or a multi-cloud strategy?
    + Is your primary role that of a Developer or Operations?
    + Does the specific cloud ecosystem fully support the tool?

### Container Services on AWS

#### Dockerfile

A Dockerfile delineates the procedure for building a container image. It describes the environment, dependencies, build steps, and final runtime configuration, ensuring that the application runs consistently across any system supporting Docker.

**- Images:** A packaged blueprint of an application, built from a Dockerfile using a layered file system. These are utilized to instantiate containers consistently across diverse environments.

**- Workflow:** A Dockerfile is employed to build a Docker Image, which can then run a Container and be pushed to ECR or Docker Hub.

#### Amazon ECR

A fully managed container registry that simplifies the storage, management, and secure sharing of Docker container images. It serves as AWS's proprietary, secure, and scalable private container registry.

**- Features:**
    + Image Scanning
    + Immutable Tags
    + Lifecycle Policies
    + Encryption & IAM

**- Orchestration:** This involves managing numerous container processes, including restarting containers, automatically scaling up under high load, efficiently distributing traffic, and managing where containers are placed and executed.

#### Kubernetes

An open-source system that automates deployment, scaling, healing, and load balancing.
**- Components:**
    + **Master Node:** The Control Plane that manages worker nodes and pods.
    + **Worker Node:** Runs application workloads inside pods.
    + **Pod:** The smallest deployable unit, which can contain one or more containers.
    + **Service**

**Comparison: ECS vs EKS**

| Feature | Amazon ECS (Elastic Container Service) | Amazon EKS (Elastic Kubernetes Service) |
| :--- | :--- | :--- |
| **Core Technology** | AWS-native container orchestration | Kubernetes-based (open-source standard) |
| **Complexity** | Simpler, easier to operate | Highly flexible but more **complex** |
| **Knowledge Required** | **No Kubernetes knowledge needed** | Requires **Kubernetes knowledge** (pods, deployments, etc.) |
| **AWS Integration** | Deep AWS integration (ALB, IAM, CloudWatch, etc.) | Standard Kubernetes integration |
| **Use Case/Benefits** | Great for **fast deployments** & **lower ops overhead** | **Multi-cluster**, **multi-cloud portability** |
| **Ecosystem/Community** | AWS-native tools and community | **Larger ecosystem** & community tools |
| **Summary** | ECS = easier, faster to run, **lower operational overhead** | EKS = more flexibility, more control, **more complexity** |

#### App Runner

This service is suitable for the rapid deployment of web applications and REST APIs, making it ideal for small to medium production workloads.

### Monitoring & Observability

#### CloudWatch
- Monitors AWS resources and applications running on AWS in real-time.
- Provides comprehensive observability.
- Enables alarms and automated responses.
- Offers dashboards to assist with operational and cost optimization.

**- CloudWatch metrics:** Performance data collected from systems on AWS or on-premise (via CloudWatch Agent), integrating seamlessly with EventBridge, Auto Scaling, and DevOps workflows.

#### AWS X-Ray
**- Distributed Tracing:** Tracks requests end-to-end and maps paths between visited services. It necessitates adding an SDK to the code to generate trace IDs.

**- Performance Insight:** Facilitates root cause analysis for latency and errors by deducing insights from traces and providing Real User Monitoring.

## Event Experience

This event proved pivotal for our project, as it directly addressed our plan to implement IaC using CDK, replacing our current "ClickOps" approach to enhance maintainability and reproducibility. Additionally, the insights regarding CloudWatch significantly bolstered our data monitoring strategy.

The speakers addressed several key questions from our team:

- **Q:** To date, our project has been built entirely using ClickOps, and we plan to transition to CDK. Is there a tool available that can scan and convert our existing infrastructure into CDK or CloudFormation templates, avoiding the need to rebuild from scratch?
- **A:** Regrettably, there is currently no tool capable of fully automating this conversion. Consequently, the team will need to reconstruct the infrastructure from scratch. However, should you discover a tool that assists with this, please share it with the community.

- **Q:** We noticed that AWS X-Ray, when used with CloudWatch, appears similar to CloudTrail in its tracing method. Could you explain the key differences?
- **A:** X-Ray is integrated with CloudWatch and is specifically used to trace the path through resources and services that the system interacts with. In contrast, CloudTrail is primarily utilized to log and audit actions taken by AWS users (API calls).

- **Q:** Our project relies on GuardDuty Findings. Do you have any experience with reliably triggering Findings for demo scenarios?
- **A:** In my experience, GuardDuty Findings can be triggered by port scanning activities, although other methods certainly exist.
- **A:** GuardDuty can also be configured with a threat list containing custom rules to trigger findings upon activities related to specific malicious domains or IPs.

This event also marked the debut presentation for some of the speakers:
- The DevOps and IaC sections were delivered with high proficiency.
- The Monitoring & Observability section was slightly less polished, and the speaker's nervousness was perceptible; however, they still delivered significant value.

#### Some event photos
![Group picture during the event taken by speaker Tran Dai Vi](/images/4-Event/CM2GroupPic.jpg)
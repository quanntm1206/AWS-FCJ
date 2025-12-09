---
title: "Blog 2"
date: "2025-09-16"
weight: 02
chapter: false
pre: " <b> 3.2. </b> "
---

# Amazon MSK Replicator and MirrorMaker2: Choosing the right replication strategy

Customers need to replicate data from their Apache Kafka clusters for a variety of reasons, such as compliance requirements, cluster migrations, and disaster recovery (DR) implementations. However, the right replication strategy can vary depending on the application context.

In this post, we walk through the different considerations for using **Amazon MSK Replicator** over **Apache Kafka’s MirrorMaker 2**, and help you choose the right replication solution for your use case.

---

## Challenges with choosing DR strategies

Customers create business continuity plans and DR strategies to maximize resiliency for their applications, because downtime or data loss can result in losing revenue or halting operations. For customers using Kafka, planning for DR is essential to meeting **Recovery Time Objective (RTO)** and **Recovery Point Objective (RPO)** goals.

### Amazon MSK Availability Features
* **Multi-AZ:** Amazon MSK provides high availability by distributing brokers across multiple Availability Zones.
* **Intra-cluster replication:** A replication factor of 3 and `min-ISR` of 2, combined with `acks=all`, provides robust protection against single broker or single-AZ failures.
* **Express brokers:** These offer pay-as-you-go storage and faster recovery times, increasing resilience.

However, if an issue impacts an entire Region, a multi-Region architecture is required.

### S3 Backups vs. Multi-Region Replication
For companies that can withstand a longer RTO but require a lower RPO, backing up data to **Amazon S3** (using Amazon MSK Connect) is a valid DR plan. However, this approach has challenges:
* Restoration can take a long time depending on data volume.
* Handling consumer group offsets is complex.

Therefore, most streaming use cases rely on setting up MSK clusters in multiple Regions and configuring data replication between clusters to provide the required business resilience.

---

## Choosing the right replication solution: MSK Replicator vs MirrorMaker 2

AWS recommends two primary solutions for cross-Region Kafka replication. Understanding when to use each is crucial.

### 1. MSK Replicator: For most MSK cluster replications in the same account
MSK Replicator is a fully managed, serverless Kafka replication service. It is the recommended solution for replicating data within the same AWS account.

**Benefits:**
* **Replication between MSK clusters:** Supports active-active or active-passive DR architectures.
* **No infrastructure management:** Fully serverless with automatic scaling.
* **Built-in monitoring:** Integrated with Amazon CloudWatch metrics and logs.
* **Built-in high availability:** Offers fault tolerance across Availability Zones.

### 2. MirrorMaker 2: For migrations and complex/hybrid scenarios
MirrorMaker 2 (MM2) is a utility bundled with Kafka that uses the Kafka Connect framework. It remains the preferred solution for specific use cases requiring flexibility.

**Recommended for:**
* **Cross-account replication:** Replicating between MSK clusters in different AWS accounts.
* **Migrations to Amazon MSK:** Moving from on-premises, other clouds, or self-managed EC2.
* **Cross-cloud or hybrid cloud scenarios:** For DR or analytics across different environments.
* **Using mTLS or SASL/SCRAM authentication:** When IAM authentication cannot be enabled.
* **Custom replication policies:** Advanced topic naming or transformation requirements.

---

## MSK Replicator solution overview

The following diagram illustrates the architecture for using MSK Replicator for Disaster Recovery.



We create two MSK clusters—one in the primary Region and a standby cluster in the secondary Region. MSK Replicator is deployed in the secondary region to replicate topics, ACLs, data, and consumer group offsets.
* **Scenario:** Single-direction replication for active-passive DR (can be extended to active-active).
* **Failover:** Kafka clients connect to the primary cluster and switch to the secondary upon failover.

---

## MirrorMaker2 solution overview

The following diagram illustrates the architecture for using MirrorMaker 2 for Migration.



We create an MSK cluster in the primary Region alongside an existing on-premises Kafka cluster (or self-managed/other cloud).
* **Scenario:** Single-direction replication for cluster migration.
* **Process:** Clients interact with the on-premises cluster and are migrated to run on AWS interacting with the MSK cluster.

**Automated Deployment:**
Rather than manual configuration, AWS recommends using automated deployment resources (Terraform, Docker images optimized for AWS) to deploy MirrorMaker 2 on **Amazon ECS with Fargate** for scalable, serverless container deployment.

---

## Conclusion

Choosing the right replication solution depends on your specific requirements:

| Solution | Primary Use Case |
| :--- | :--- |
| **Amazon MSK Replicator** | Replicating from one MSK cluster to another within the same account; fully managed DR solution. |
| **MirrorMaker 2** | Migrations to Amazon MSK, hybrid environments, cross-account replication, or complex custom policies. |

These approaches provide customizable options to ensure data redundancy and business continuity, helping meet regulatory compliance while minimizing operational overhead.

_Source: Mazrim Mehrtens | 16 SEP 2025_
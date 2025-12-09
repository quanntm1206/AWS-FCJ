---
title: "Event 5"
date: "2025-11-29"
weight: 5
chapter: false
pre: " <b> 4.5.</b> "
---

# Summary Report: “BUILDING AGENTIC AI - Context Optimization with Amazon Bedrock”

## Event Objectives

- To conduct a technical deep-dive into the AWS Bedrock Agent Core.
- To demonstrate the construction of Agentic Workflows within the AWS ecosystem.
- To introduce **Diaflow** as an AI automation platform.
- To introduce **CloudThinker** and its capabilities in Cloud Operations.
- To explore Agentic Orchestration and Context Optimization strategies using Amazon Bedrock.
- To facilitate practical learning through the CloudThinker Hack: Hands-on Workshop.

## Speakers

- **Nguyen Gia Hung** - Head of Solutions Architect, AWS
- **Kien Nguyen** - AWS Startup Solutions Architect
- **Viet Pham** - CEO & Founder, Diaflow
- **Thang Ton** - Co-Founder & COO, CloudThinker
- **Henry Bui** - Head of Engineering, CloudThinker
- **Van Hoang Kha** - AWS Community Leader
- **Nhat Tran** - CTO, CloudThinker

## Key Highlights

### Amazon Bedrock AgentCore

**The Evolution to Agentic AI:** The adoption of Agentic AI systems by enterprises is accelerating rapidly. AWS positions itself as the optimal environment for building and scaling these AI Agents.

**AWS Ecosystem Provision:**
- **Frameworks:** Supports integration with Strands, LangGraph, OpenAI, etc.
- **Applications:** Offerings include Kiro and AWS QuickSuite.
- **Foundation:** Built upon Amazon SageMaker and Amazon Bedrock Models.

**Core Components of Amazon Bedrock AgentCore:**
- **Runtime:** A secure, serverless agent deployment environment that scales workloads and accelerates time-to-market.
- **Identity:** Enterprise-grade identity and access management (IAM) that accelerates development while securing access for AI Agents.
- **Gateway:** Provides unified, secure access to tools, featuring intelligent tool discovery capabilities.
- **Memory:** Facilitates intelligent, context-aware memory retention, simplifying the management of enterprise-grade data with deep customization options.
- **Browser:** A scalable, serverless cloud browser runtime offering enterprise-grade security and observability.
- **Code Interpreter:** A secure, sandboxed environment for code execution, enabling large-scale data processing with ease.
- **Observability:** Delivers complete visibility into agent performance to maintain quality and trust while integrating seamlessly with other observability tools.

### Diaflow: AI Automation Platform

Diaflow is an AI Automation Platform for Businesses designed to unlock team potential by providing flexible, no-code tools to automate critical workflows rapidly.

- **Mission:** To transform manual processes into intelligent workflows in minutes, addressing the statistic that 90% of businesses waste over 20 hours per person per week on repetitive tasks, while simultaneously solving data privacy concerns.
- **Adoption:** Over 6,000 users globally across Retail, IT Services, Finance, Marketing, and Healthcare.
- **Backing:** Developed by experts from major tech institutions and backed by partners like NVIDIA, Microsoft, AWS, and Google.
- **Presence:** Operating in the USA, Switzerland, France, South Korea, Singapore, and Vietnam.

**Core Capabilities & Features:**
- **AI-Powered Automation:** Reduces manual tasks by 80% by connecting Databases, Apps, Knowledge Bases, APIs, and Legacy systems.
- **Autonomous Task Execution:** Users describe a goal, and Diaflow plans and executes the necessary steps.
- **Multi-Model Processing:** Supports various LLMs including Claude, Gemini, and Deepseek.
- **Enterprise-Grade Security:** Compliant with HIPAA, SOC2, and GDPR.

### CloudThinker: Agentic Cloud Operations

CloudThinker addresses common customer challenges such as exploding cloud costs, the complexity of cloud management exceeding capability, and reactive incident responses.

**Capabilities: Insights -> Reasoning -> Execution**
- Multi-agent Collaboration
- Autonomous Operations
- Continuous Optimization & Learning
- Multi-cloud Capability

**The CloudThinker AI Agent Team:**
- **Alex:** Cloud Engineer
- **Kai:** Kubernetes Engineer
- **Anna:** General Manager
- **Oliver:** Security Engineer
- **Tony:** Database Engineer

### Agentic Orchestration and Context Optimization

#### AI Agent Architecture
- **Chatbots vs. Agents:** Unlike reactive chatbots that use rule-based decisions, Agents are proactive, capable of initiating actions, making dynamic decisions, and adapting through experience to handle multi-step tasks.
- **Core Components:**
    + **Planning:** Deconstructs tasks into executable steps.
    + **Memory:** Retains context and interaction history.
    + **Tools:** Interfaces with external APIs, search engines, and code interpreters.
    + **Action:** Executes the plan and formulates the final response.

#### Getting Started with Agents
- **ReAct Architecture:** A paradigm of interleaving thought and action (User Input → Reasoning/Thought → Action/Tool Use → Observation → Final Answer).
- **Tool Selection:** Effective tools must possess Agent Context, support diverse workflows, enable intuitive problem-solving, and undergo rigorous real-world testing.

#### Coordination Models: Solving Bottlenecks
Single-Agent systems often face "context isolation" (handling 100k+ tokens) and sequential processing bottlenecks. Distributed orchestration solves this via two main models:

| Feature | Network (Peer-to-Peer) | Supervisor |
| :--- | :--- | :--- |
| **Structure** | Agents communicate directly with one another. | A central Supervisor delegates tasks to specialized Worker agents. |
| **Pros** | * Flexible communication.<br>* High fault tolerance.<br>* Easier transition from single-agent modes. | * Clear task delegation.<br>* Centralized coordination.<br>* Modular and scalable architecture. |
| **Cons** | * Complex debugging.<br>* Ambiguity in ownership. | * Potential bottleneck risk.<br>* Inflexible switching to single-agent mode. |

**Supervisor Variants:**
1.  **Group Chat-based:** Collaborative context, simple coordination. *Used by CloudThinker.*
2.  **Supervisor as Tool (Subagents):** Fine-grained control, less worker autonomy.
3.  **Hierarchical:** Multi-layer supervision, scalable for large organizations.

#### Solving the 100:1 Agentic Cost Problem
Agentic Architectures face a "Context Explosion" where the Input/Output token ratio can reach 100:1 (compared to 3:1 for chatbots). To combat this, four "Quick-win" techniques were presented, offering 80–95% cost savings and 3–5x latency reduction:

1.  **Prompt Caching:**
    * *Goal:* 70–90% cost reduction.
    * *Method:* A Three-Tier Architecture where System Prompt and Conversation History are cached, while the current turn remains dynamic.
2.  **Context Compaction:**
    * *Goal:* 80% summarization cost reduction.
    * *Method:* Cache-Preserving Summarization appends instructions at the payload level to summarize old messages without breaking cache keys.
3.  **Tool Consolidation:**
    * *Goal:* 20% reduction in token count and hallucinations.
    * *Method:* Consolidating CRUD operations into single interfaces and using **Just-In-Time Schemas** to fetch documentation only when required.
4.  **Parallel Tool Calling:**
    * *Goal:* 30–40% reduction in round trips.
    * *Method:* Providing explicit instructions to the LLM to parallelize tool calls and reasoning steps.

#### Cross-Region Inference
To avoid rate limits caused by high-volume tool calls (50–100 per task), workloads are automatically routed across global regions (US, EU, APAC). This eliminates single points of failure and provides a global profile for near-zero latency.

> **Key Insight:** The best multi-agent system self-realizes when *NOT* to use multiple agents.

## CloudThinker Hack: Hands-On Workshop

The organizers provided attendees with access to CloudThinker instructions and a Free Standard Plan Code to analyze their personal AWS Accounts.

## Event Experience

This event was highly informative, significantly strengthening our understanding of Amazon Bedrock and introducing us to powerful tools like Diaflow and CloudThinker.

**Success Story:**
During the *CloudThinker Hack* workshop, our team utilized the tool to analyze our AWS Account's infrastructure.
- **The Finding:** CloudThinker successfully identified an abnormally high volume of S3 Bucket GET requests (over 3 million requests in a 2-week period).
- **The Solution:** The agent recommended using **Amazon Data Firehose** to consolidate logs before saving them to S3, rather than writing individual small files.
- **The Result:** Our team was awarded a prize for effectively utilizing CloudThinker to diagnose and resolve this issue. We received a CloudThinker T-Shirt and Keychain.

#### Some event photos
![Picture of all Attendees](/images/4-Event/Event7AllAttendee.jpg)
_Picture of all attendees_

![Recieving Prize From CloudThinker1](/images/4-Event/CloudThinkerPrize1.jpg)
_Receiving Prize From CloudThinker_

![Recieving Prize From CloudThinker2](/images/4-Event/CloudThinkerPrize2.jpg)
_Receiving Prize From CloudThinker_
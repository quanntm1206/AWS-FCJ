---
title: "Event 1"
date: "2025-10-03"
weight: 01
chapter: false
pre: " <b> 4.1 </b> "
---

# Summary Report: “AI-Driven Development Life Cycle: Reimagining Software Engineering”

### Event Objectives

- To explore the significant transformation in software development propelled by generative AI.
- To introduce the AI-Driven Development Life Cycle (AI-DLC) along with its fundamental concepts.
- To demonstrate the capabilities of Kiro and Amazon Q Developer.

### Speakers

- **Toan Huynh** – Specialist SA, PACE
- **My Nguyen** - Sr. Prototyping Architect, Amazon Web Services - ASEAN


### Key Highlights

- The session centered on the AI-DLC framework, a system where AI orchestrates the development process—including planning, task decomposition, and architectural suggestions—while developers retain ultimate responsibility for validation, decision-making, and oversight.

**- AI-DLC Core Concept:** This approach is distinctly human-centric, with AI acting as a collaborator to augment developer capabilities. This partnership leads to accelerated delivery, reducing cycles from weeks or months to merely hours or days.

**- AI-DLC Workflow:** The process follows an iterative loop comprising AI Tasks (such as creating and implementing plans or seeking clarification) and Human Tasks (providing clarification and implementing plans). In this workflow, the AI repeatedly asks clarifying questions and only proceeds with solutions following human validation.

**- AI-DLC Stages:** The lifecycle is divided into Inception, Construction, and Operation, with each stage establishing a richer context for the subsequent one:

+ Inception: Involves building context, elaborating on intent through User Stories, and planning via Units of Work.

+ Construction: Encompasses domain modeling, code generation and testing, the addition of architectural components, and deployment using Infrastructure as Code (IaC) and tests.

+ Operation: Focuses on production deployment and incident management.

**- Challenges AI-DLC Aims to Solve:**

+ Scaling AI development: AI coding tools often struggle when applied to complex projects.

+ Limited control: Current tools make collaborating with and managing AI agents difficult.

+ Code quality: Maintaining strict quality control when transitioning from a proof-of-concept to production remains a significant hurdle.

## Deep Dive: Kiro - The AI IDE for Prototype to Production

- Kiro is an AI-first Integrated Development Environment (IDE) designed to support the AI-DLC, with a specific focus on Spec-driven development.

**- Spec-driven Development:** Kiro transforms high-level prompts (e.g., "I want to create a chat application like Slack") into precise requirements (requirements.md), system designs (design.md), and discrete tasks (tasks.md). This fundamentally shifts development from "vibe coding" to a structured, traceable process where developers collaborate with Kiro on these specifications, which then serve as the single source of truth.

**- Agentic Workflows:** Kiro's AI agents execute specifications while ensuring the human developer remains in control. Key features include:

**+ Implementation Plan:** Kiro generates a comprehensive implementation plan containing start tasks and sub-tasks (such as "Implement user registration and login endpoints" or "Implement JWT middleware"), linking them directly to specific requirements for validation.

**+ Agent Hooks:** These hooks delegate tasks to AI agents triggered by events like a "file save." They execute autonomously in the background based on predefined prompts, helping to scale productivity by generating documentation, writing unit tests, or optimizing code performance.
### Key Takeaways
**- AI Ensures Production Readiness:** By creating detailed design documents—such as data flow diagrams and API contracts—and generating unit tests before code is written, Kiro ensures that AI-generated code is maintainable and production-ready, rather than just a quick prototype.

**- Human Control via Artifacts:** Developers maintain control not by writing the majority of the code, but by validating and refining the artifacts—specifically the requirements, design, and task plan—before AI agents proceed with implementation.

### Applying to Work

**- Integrate Amazon Q Developer/Similar Tools:** I intend to integrate AI coding assistants into my academic projects to automate boilerplate code and routine tasks, thereby boosting overall productivity.

**- Focus on High-Value Tasks:** By allowing AI to handle undifferentiated heavy lifting, I can dedicate my time to mastering higher-value, creative activities such as Domain Modeling and Architectural Design, which remain crucial human-centric elements in the Construction phase.

### Event Experience

Attending the **AI-Driven Development Life Cycle: Reimagining Software Engineering** event offered a fascinating glimpse into the future of software development. It became evident that Generative AI is not merely a coding assistant; it is poised to become the core orchestrator of the entire development process. The session was well-structured, progressing logically from the overarching concept of AI-DLC to specific demonstrations of Amazon Q Developer and Kiro. The Kiro demo was particularly impactful, illustrating how a single text prompt can be transformed into a comprehensive, executable, and traceable development plan directly within the IDE.

#### Lessons learned
- The three primary challenges associated with current AI development—scaling, limited control, and code quality—made the structured, human-validated approach of AI-DLC appear both highly necessary and well-conceived.


#### Some event photos
![Group picture during the event](/images/4-Event/TheBois-AIDLC.jpg)
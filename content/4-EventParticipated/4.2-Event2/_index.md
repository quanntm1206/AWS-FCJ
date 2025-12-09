---
title: "Event 2"
date: "2025-11-15"
weight: 02
chapter: false
pre: " <b> 4.2 </b> "
---

# Summary Report: “AWS Cloud Mastery Series #1 - AI/ML/GenAI on AWS”

### Event Objectives

- To provide an introduction to AI, Machine Learning, and Generative AI within the AWS ecosystem.

### Speakers

- **Lam Tuan Kiet** – Sr DevOps Engineer, FPT Software
- **Danh Hoang Hieu Nghi** - AI Engineer, Renova Cloud
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud AI Journey
- **Van Hoang Kha** - Cloud Security Engineer, AWS Community Builder
### Key Highlights

# Explored Generative AI with Amazon Bedrock:

**- Foundation Models:** Unlike traditional models, these serve as versatile tools adaptable to a multitude of tasks. Bedrock provides access to fully managed models from leading AI companies such as OpenAI, Claude, and Anthropic.
**- Prompt Engineering:** The art of crafting and refining instructions to optimize model output.
   + Zero-Shot Prompting: Providing a prompt without any prior context or examples.
   + Few-shot Prompting: Including a limited amount of context and examples within the prompt to guide the model.
   + Chain of Thought: Encouraging the model to outline its reasoning process and steps to derive the final answer.
**- Retrieval Augmented Generation (RAG):** A method for retrieving relevant information from specific data sources.
   + R: Retrieval - Gathers relevant information from a knowledge base or external data sources.
   + A: Augmented - Incorporates the retrieved information as additional context in the user's prompt before input.
   + G: Generation - Produces responses from the model based on the enhanced, augmented prompt.
   + Use cases: Applications include enhancing content quality, creating contextual chatbots, enabling personalized search, and facilitating real-time data summarization.

**- Amazon Titan Embedding:** A lightweight model designed to efficiently translate text into numerical representations (embeddings). It excels in high-accuracy retrieval tasks and supports over 100 languages.

**- Pretrained AI Services:** 
  + Amazon Rekognition: Facilitates image and video analysis.
  + Amazon Translate: Detects and translates text across languages.
  + Amazon Textract: Extracts text and layout data from documents.
  + Amazon Transcribe: Converts speech into text.
  + Amazon Polly: Converts text into lifelike speech.
  + Amazon Comprehend: Derives insights and identifies relationships within text.
  + Amazon Kendra: An intelligent enterprise search service.
  + Amazon Lookout: Detects anomalies in business metrics, equipment, and images.
  + Amazon Personalize: Tailors recommendations to individual users.

**- Demo:** AMZPhoto: A demonstration of face recognition capabilities using AI on images.

**- Amazon Bedrock AgentCore:** A comprehensive platform designed to address the challenges of deploying agents into production:
  + Securely executing and scaling agent code.
  + Incorporating memory to retain past interactions and facilitate learning.
  + Implementing identity and access controls for both agents and tools.
  + Enabling agentic tool use for complex workflows.
  + Discovering and connecting with custom tools and resources.
  + Understanding and auditing every interaction (observability).
  **+ Foundational Services:** Categorized services that ensure agents run securely at scale.

  **+ Enhance with tools & memory:** Includes components such as Memory, Gateway, Browser tools, and Code Interpreter.

  **+ Deploy securely at scale:** Covers Runtime and Identity management.

  **+ Gain operational insights:** Focuses on Observability.

  **+ Enabling Agents at Scale (Architecture):** Connects the AgentCore Gateway (via MCP) to Memory, Identity, Observability, Browser, and Code Interpreter components.

  **+ Frameworks for Building Agents:** Supports frameworks such as CrewAI, Google ADK, LangGraph/LangChain, LlamaIndex, OpenAI Agents SDK, and Strands Agents SDK.

### Key Takeaways
- Bedrock is the GenAI Hub: Amazon Bedrock serves as a central hub, offering fully managed Foundation Models from top industry players for a wide array of tasks.

- Customization via Prompts and Data: Users can customize interactions through various prompting techniques (Zero-Shot, Few-Shot, CoT) and utilize RAG to inject context for superior model responses.

- Embeddings Power Search: Amazon Titan Embeddings plays a critical role in translating text to numerical data, thereby facilitating high-accuracy retrieval tasks (such as RAG).

- Pretrained Models: AWS offers a suite of ready-to-deploy AI services for common requirements, such as Amazon Rekognition for imagery and Textract for documentation.

- AgentCore Solves Production Issues: Amazon Bedrock AgentCore is a comprehensive platform that addresses the complexities of operating AI Agents at scale, managing critical components like Memory, Identity, and Observability.

### Applying to Work

- The insights gained will be highly beneficial for the team's upcoming projects, which are likely to incorporate AI Foundation Models into our architecture.

### Event Experience
- The speakers were articulate and provided highly informative content.
- Q&A: A team member raised a project-critical question, despite it being slightly tangential to the main topic.
  + Q: Our architecture utilizes SNS to process GuardDuty findings, but we face bottlenecks when over 1000 alerts occur simultaneously. How can this be resolved?
  + A: Implementing SQS to queue the events ensures that no alerts are missed during high-volume periods.
- I secured a position in the top 10 during the concluding Kahoot quiz and had the opportunity to take a photo with the speakers.
- We established an unofficial group named "Mèo Cam Đeo Khăn," representing a collaboration between my group, "The Ballers," and "Vinhomies."

#### Some event photos
![Mèo Cam Đeo Khăn group](/images/4-Event/Meocamdeokhan.jpg)
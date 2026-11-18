[🏠 Home](../README.md) › [Module 5: Agentic AI for OCI Enterprise AI](README.md) › 5.8

# 5.8 Summary

## 1. OCI Console Setup & Prerequisites

To execute an agent using the OCI Enterprise AI Agents Service, four environmental requirements must be configured in the OCI Dashboard:

| **Requirement**              | **Action Required**                                                           | **Purpose**                                                                                              |
|------------------------------|-------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| **1. Account & Compartment** | Must have an active OCI account and a target compartment.                     | Organizes cloud resources and isolates boundaries.                                                       |
| **2. Project Creation**      | Create a Generative AI Project (e.g., `FirstAgentProject`).                     | Acts as the container for all agent assets. Requires saving the generated **Project OCID**.              |
| **3. API Key Generation**    | Generate an API Key (e.g., FirstAgentAPIKey) and copy the keys.               | Authenticates API requests. *Note: Non-admins must apply a specific IAM policy for the key to function.* |
| **4. Environment Setup**     | Install required SDK packages and store keys in an `.env` file (`GENAI_API_KEY`). | Securely loads credentials and dependencies into the application runtime.                                |

## 2. Code Configuration & Model Selection

To route requests to OCI's infrastructure instead of OpenAI's servers while using the standard OpenAI Python SDK, you must configure three specific parameters:

- **OCI Base URL:** Set to the specific OCI regional endpoint (e.g., us-chicago-1).

- **Project Header:** Pass the Project OCID explicitly in the client requests.

- **Model Name:** Specify the target model hosted on OCI.

  - *Demo Selection:* openai gpt oss 120 billion (~117 billion parameter open-weight LLM).

  - *Region Dependency:* The us-chicago-1 region was selected specifically because OCI documentation maps this open-weight GPT model to that data center for both on-demand and dedicated AI clusters.

**Key Architectural Takeaway:** You use the **identical OpenAI Python SDK**, but by swapping the `base_url`, model name, and passing the project ID header, your data and inference run entirely on OCI infrastructure.

## 3. The Responses API vs. Agent Frameworks

When calling the OCI Responses API directly without an abstraction framework (like LangChain or OpenAI Agents SDK), the developer assumes responsibility for lower-level orchestration:

## Tool Definition

- **Frameworks (LangChain):** Use `@tool` decorators that automatically generate JSON schemas.

- **Direct Responses API:** You must manually write out and describe each tool's schema as JSON so the model understands the available functions at runtime.

## The Agent Execution Loop

- **Frameworks:** Hide the execution loop behind simple commands like `agent.invoke()` or `runner.run_sync()`.

- **Direct Responses API:** You must manually code the while loop (approx. 35 lines of Python). This loop explicitly handles:

  1. Sending prompt and tool definitions to the LLM.

  2. Receiving the model's decision to call a tool (the LLM does not execute the tool; it only elects to call it).

  3. Executing the local tool (e.g., a math function) and capturing the output.

  4. Passing the output back to the LLM.

  5. Repeating until the model returns a final text response without requesting further tools.

## 4. Module Recap: Core Platform Concepts

- **The Role of the Runtime:** Moving from a prototype to a production agent requires a runtime infrastructure to manage execution, tool routing, memory compaction, and system integrations.

- **Unified Platform:** OCI Enterprise AI Platform combines model hosting, managed agent runtimes, and enterprise governance into a single stack.

- **Zero-Friction Migration:** Because the OCI Enterprise AI Agents Service exposes an **OpenAI-compatible Responses API**, legacy OpenAI-based applications can migrate to OCI with minimal code changes.

- **Deployment Flexibility:** Organizations can choose between **API Consumption** (managing their own application runtime and calling OCI Responses API) or **Hosted Application Deployment** (packaging code as a container and letting OCI manage end-to-end PaaS orchestration).

---

### 🔗 Related

- **Agent Loop** → [1.1 What Is an AI Agent?](../01-introduction-to-ai-agents/01-what-is-an-ai-agent.md)
- **Orchestration Layer** → [1.2 Agentic AI Core Components](../01-introduction-to-ai-agents/02-agentic-ai-core-components.md)
- **LangChain** → [2.2 Introduction to LangChain](../02-langchain-for-ai-agents/02-introduction-to-langchain.md)
- **Responses API** → [4.2 OpenAI Responses API](../04-openai-responses-api-agents-sdk/02-openai-responses-api.md)
- **OCI Enterprise AI** → [5.3 Introduction to OCI Enterprise AI Platform](03-introduction-to-oci-enterprise-ai-platform.md)
- **OCI Responses API** → [5.5 OCI Enterprise AI Agents Building Blocks](05-oci-enterprise-ai-agents-building-blocks.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [5.7 OCI Enterprise AI Agents: Deploy & Scale](07-oci-enterprise-ai-agents-deploy-and-scale.md) | [⬆️ Module 5](README.md) | [6.1 Agentic AI for Oracle AI Database](../06-oracle-ai-database-agentic-ai/01-agentic-ai-for-oracle-ai-database.md) ➡️

[🏠 Home](../README.md) › [Module 5: Agentic AI for OCI Enterprise AI](README.md) › 5.7

# 5.7 OCI Enterprise AI Agents: Deploy & Scale

## OCI Enterprise AI Agents Service: Local to Production

The OCI Enterprise AI Agents Service provides two distinct architecture models for transitioning agentic applications from local development to production. The core difference lies in **where the application runs** and **who manages the orchestration and infrastructure**.

| **Feature**                   | **Approach 1: API Consumption**                             | **Approach 2: Managed Deployment**                                |
|-------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------|
| **Primary Mechanism**         | OCI Responses API                                           | Hosted Application Deployment                                     |
| **Where App Runs**            | Customer environment (Laptop, VM, K8s, Custom Backend)      | Fully hosted on OCI                                               |
| **Framework Support**         | Any (e.g., OpenAI SDK with OCI base URL)                    | Any (LangChain, LangGraph, OpenAI Agents SDK)                     |
| **OCI Responsibilities**      | AI infrastructure, model execution, built-in tool reasoning | End-to-end hosting: scaling, networking, auth, runtime, endpoints |
| **Customer Responsibilities** | Application runtime, orchestration, scaling, deployment     | Code development, containerization, image push                    |

## Approach 1: API Consumption (OCI Responses API)

In this lightweight model, you treat OCI purely as an AI inference and reasoning backend while retaining total control over your application runtime.

- **Execution Location:** Your agent code runs on your own infrastructure—whether a local laptop, an on-premises Kubernetes cluster, a cloud VM, or an enterprise backend.

- **Implementation:** You call the **OCI Responses API** directly. A common implementation is pointing the standard OpenAI Python SDK's `base_url` directly to OCI endpoints.

- **Managed by OCI:** AI model infrastructure, LLM execution, and built-in tool reasoning capabilities.

- **Best For:** Teams that already have an established application hosting infrastructure or need custom, complex orchestration outside of OCI's runtime.

## Approach 2: Managed Application Deployment

In this end-to-end model, OCI acts as a Platform-as-a-Service (PaaS), hosting both the AI models and your entire agentic application.

- **Execution Location:** OCI hosts, runs, and scales the application containers natively.

- **Framework Flexibility:** Build using any preferred agent framework (e.g., LangGraph, LangChain, OpenAI Agents SDK).

- **Managed by OCI:** Production deployment concerns, including horizontal scaling, networking, authentication, runtime infrastructure, and endpoint exposure.

## 5-Step Managed Deployment Workflow

1. **Develop Locally:** Build and test your agent logic on your local machine using any agent framework.

2. **Package the Agent:** Containerize the application by creating a Docker image containing your agent code and all required dependencies.

3. **Upload to Registry:** Push the compiled container image to the OCI managed container registry (**OCIR**).

4. **Create a Generative AI Application:** Configure an application resource in OCI. This acts as the structural container that defines production rules for **scaling, storage, networking, and authentication**.

5. **Create a Deployment:** Select your uploaded OCIR container image and deploy it within the Generative AI Application. OCI automatically provisions a production **HTTP endpoint** that clients or multi-agent systems use to query your agent.

---

### 🔗 Related

- **Orchestration Layer** → [1.2 Agentic AI Core Components](../01-introduction-to-ai-agents/02-agentic-ai-core-components.md)
- **LangChain** → [2.2 Introduction to LangChain](../02-langchain-for-ai-agents/02-introduction-to-langchain.md)
- **LangGraph** → [2.4 Building Your First Agent with LangChain](../02-langchain-for-ai-agents/04-building-your-first-agent-with-langchain.md)
- **Responses API** → [4.2 OpenAI Responses API](../04-openai-responses-api-agents-sdk/02-openai-responses-api.md)
- **Agents SDK** → [4.3 OpenAI Agents SDK](../04-openai-responses-api-agents-sdk/03-openai-agents-sdk.md)
- **OCI Enterprise AI** → [5.3 Introduction to OCI Enterprise AI Platform](03-introduction-to-oci-enterprise-ai-platform.md)
- **OCI Responses API** → [5.5 OCI Enterprise AI Agents Building Blocks](05-oci-enterprise-ai-agents-building-blocks.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [5.6 Demo: OCI Enterprise AI Agents Setup](06-demo-oci-enterprise-ai-agents-setup.md) | [⬆️ Module 5](README.md) | [5.8 Summary](08-summary.md) ➡️

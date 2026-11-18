[🏠 Home](../README.md) › [Module 5: Agentic AI for OCI Enterprise AI](README.md) › 5.5

# 5.5 OCI Enterprise AI Agents Building Blocks

The OCI Enterprise AI Agents Service provides a structured suite of APIs, built-in tools, and memory management architectures to develop and execute agentic workflows.

## 1. OCI Responses API

The Responses API is the primary, high-level interface for building and interacting with AI agents on OCI.

- **Specification & Compatibility:** Built to conform to the **Open Responses specification** and is fully **OpenAI-compatible**.

- **Multistep Reasoning & Tool Calling:** A single API request can trigger an autonomous loop where the model calls multiple sequential tools (e.g., code interpreter, file search, custom functions, MCP servers) before returning a final answer.

- **Multimodel Routing:** Supports routing different tasks to specialized models from major providers including **OpenAI, Grok, Gemini, Llama, and Cohere**.

- **State & Memory Integration:** Native integration with the Conversations API for session state, long-term memory persistence, and context compaction.

- **Zero Infrastructure:** Fully serverless execution — developers invoke the API directly without provisioning or managing underlying runtime infrastructure.

## 2. Agent Tools (The "Hands")

While the LLM acts as the reasoning "brain," tools function as the "hands" that allow the agent to interact with data, APIs, and execution environments.

| **Tool Category**    | **Mechanism**                                              | **Core Use Case**                                                                                     |
|----------------------|------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **File Search**      | Semantic retrieval via an integrated vector store.         | Searching and extracting relevant data from uploaded enterprise documents.                            |
| **Code Interpreter** | Python code execution inside a secure sandbox environment. | Performing data analysis, complex mathematical computation, and algorithmic problem-solving.          |
| **Function Calling** | Developer-defined custom Python function invocation.       | Executing business logic, querying relational databases, or triggering external enterprise workflows. |
| **MCP Calling**      | Connection to remote Model Context Protocol (MCP) servers. | Standardized tool integration across external systems and remote server environments.                 |

## 3. Memory Architecture

To make agents intelligent across turns and sessions, the service provides three distinct layers of memory management:

| **Memory Type**                       | **Mechanism**                                                                                                                    | **Analogy**                                                    |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| **Conversations API (Short-Term)**    | Manages immediate session-based state and back-and-forth turn history within a single active conversation.                       | Your notepad during a live meeting.                            |
| **Long-Term Memory**                  | Persists critical data across distinct sessions over time (e.g., user preferences, historical decisions, accumulated knowledge). | Your personal journal.                                         |
| **Context Optimization (Compaction)** | Automatically summarizes lengthy conversations to fit within a specific model's context window without losing critical details.  | Summarizing a three-hour meeting into essential bullet points. |

## 4. Lower-Level APIs (Granular Control)

For advanced architectures that require custom orchestration beyond the high-level tools, OCI exposes OpenAI-compatible foundational APIs:

| **API**               | **Function**                                                           | **Architectural Application**                                                                   |
|-----------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| **Vector Stores API** | Manages vector databases, automated document chunking, and embeddings. | Building custom Retrieval-Augmented Generation (RAG) pipelines and semantic search indices.     |
| **Files API**         | Handles raw file uploads, storage, and lifecycle management.           | Managing unstructured documents and datasets the agent needs to ingest and process.             |
| **Containers API**    | Provisions and executes custom containerized workloads.                | Running specialized data processing tasks or custom tools inside secure, isolated environments. |

---

### 🔗 Related

- **Memory** → [2.3 Demo: LangChain Building Blocks](../02-langchain-for-ai-agents/03-demo-langchain-building-blocks.md)
- **Model Context Protocol (MCP)** → [3.2 What Is MCP?](../03-model-context-protocol/02-what-is-mcp.md)
- **Responses API** → [4.2 OpenAI Responses API](../04-openai-responses-api-agents-sdk/02-openai-responses-api.md)
- **RAG** → [6.3 Oracle AI Vector Search Workflow](../06-oracle-ai-database-agentic-ai/03-oracle-ai-vector-search-workflow.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [5.4 Agentic AI for Enterprises](04-agentic-ai-for-enterprises.md) | [⬆️ Module 5](README.md) | [5.6 Demo: OCI Enterprise AI Agents Setup](06-demo-oci-enterprise-ai-agents-setup.md) ➡️

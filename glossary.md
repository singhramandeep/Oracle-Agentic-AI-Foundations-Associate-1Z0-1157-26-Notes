[🏠 Home](README.md)

# Glossary

Key terms from the course, each linked to the lesson where it is covered in depth.

| Term | Meaning | Lesson |
|---|---|---|
| **ADB MCP Server** | A built-in, fully managed MCP server inside Autonomous AI Database; the database itself is the security boundary. | [6.7](06-oracle-ai-database-agentic-ai/07-oracle-autonomous-ai-database-mcp-server.md) |
| **Agent Lifecycle & Runtime** | Everything beyond the prototype: hosting, scaling, state, security, observability and governance. | [5.2](05-oci-enterprise-ai-agents/02-need-for-agent-lifecycle-and-runtime.md) |
| **Agent Loop** | The iterative Perceive → Reason → Act → Observe cycle that drives an agent until it has a final answer or hits a safety limit. | [1.1](01-introduction-to-ai-agents/01-what-is-an-ai-agent.md) |
| **Agents SDK** | OpenAI's Python framework on top of the Responses API for agents, handoffs, guardrails and tracing. | [4.3](04-openai-responses-api-agents-sdk/03-openai-agents-sdk.md) |
| **AI Agent** | A system that wraps an LLM in a decision loop with tools so it can perceive, reason, act and observe until a goal is met. | [1.1](01-introduction-to-ai-agents/01-what-is-an-ai-agent.md) |
| **Chain-of-Thought** | Prompting the model to reason step by step before answering. | [1.3](01-introduction-to-ai-agents/03-reasoning-patterns.md) |
| **Chains / LCEL** | Components connected with the pipe operator (`prompt | model | parser`) into a left-to-right pipeline. | [2.3](02-langchain-for-ai-agents/03-demo-langchain-building-blocks.md) |
| **Conversations API** | OCI API for session state, long-term memory and context compaction. | [5.5](05-oci-enterprise-ai-agents/05-oci-enterprise-ai-agents-building-blocks.md) |
| **create_agent** | LangChain's one-call constructor that wires a model, tools and a system prompt into a ReAct agent. | [2.5](02-langchain-for-ai-agents/05-demo-your-first-langchain-agent.md) |
| **Embeddings** | Numeric vector representations of text, images or documents used for semantic similarity. | [6.3](06-oracle-ai-database-agentic-ai/03-oracle-ai-vector-search-workflow.md) |
| **Function Calling** | The LLM emits a structured tool-call request from a JSON schema; the runtime, not the model, executes it and returns an observation. | [1.2](01-introduction-to-ai-agents/02-agentic-ai-core-components.md) |
| **Guardrails** | System-level checks and limits (input, output, tool and iteration controls) that keep an agent safe and on task. | [1.5](01-introduction-to-ai-agents/05-safety-and-guardrails.md) |
| **Handoff** | Transferring control from one agent to a more specialised agent in a multi-agent system. | [4.6](04-openai-responses-api-agents-sdk/06-multi-agent-handoff.md) |
| **Human-in-the-Loop** | Requiring human approval before an agent takes high-impact actions. | [1.5](01-introduction-to-ai-agents/05-safety-and-guardrails.md) |
| **LangChain** | An open-source framework of composable building blocks (models, prompts, chains, memory, tools, agents) for LLM apps. | [2.2](02-langchain-for-ai-agents/02-introduction-to-langchain.md) |
| **LangGraph** | LangChain's graph-based runtime for stateful, controllable agent workflows; `create_agent` runs on top of it. | [2.4](02-langchain-for-ai-agents/04-building-your-first-agent-with-langchain.md) |
| **MCP Host / Client / Server** | The host app embeds MCP clients, each holding a 1:1 connection to a server that exposes capabilities. | [3.3](03-model-context-protocol/03-core-mcp-concepts.md) |
| **MCP Primitives** | What a server exposes: tools (actions), resources (data) and prompts (templates). | [3.3](03-model-context-protocol/03-core-mcp-concepts.md) |
| **Memory** | Stored conversation messages fed back into the prompt so a stateless LLM keeps context. | [2.3](02-langchain-for-ai-agents/03-demo-langchain-building-blocks.md) |
| **Model Context Protocol (MCP)** | An open standard for connecting AI applications to tools and data through a common client–server protocol. | [3.2](03-model-context-protocol/02-what-is-mcp.md) |
| **OCI Enterprise AI** | OCI's platform for building, deploying and governing enterprise AI agents. | [5.3](05-oci-enterprise-ai-agents/03-introduction-to-oci-enterprise-ai-platform.md) |
| **OCI Responses API** | OCI's OpenAI-compatible Responses API with multi-model routing, built-in tools and serverless execution. | [5.5](05-oci-enterprise-ai-agents/05-oci-enterprise-ai-agents-building-blocks.md) |
| **OCIR / Managed Deployment** | Deploying a containerised agent from OCI Container Registry as a hosted Generative AI Application with an HTTP endpoint. | [5.7](05-oci-enterprise-ai-agents/07-oci-enterprise-ai-agents-deploy-and-scale.md) |
| **Oracle AI Vector Search** | Native vector storage and similarity search inside Oracle AI Database, combined with relational SQL. | [6.2](06-oracle-ai-database-agentic-ai/02-introduction-to-oracle-ai-vector-search.md) |
| **Orchestration Layer** | The application controller (the agent's 'nervous system') that manages the loop, memory, tool routing, state and guardrails. | [1.2](01-introduction-to-ai-agents/02-agentic-ai-core-components.md) |
| **Private Agent Factory** | Oracle's no-code platform to build, govern and deploy enterprise agents anchored to approved data. | [6.5](06-oracle-ai-database-agentic-ai/05-oracle-ai-database-private-agent-factory.md) |
| **Prompt Template** | A reusable prompt with placeholders filled in at run time; chat templates use system/human/AI message roles. | [2.3](02-langchain-for-ai-agents/03-demo-langchain-building-blocks.md) |
| **RAG** | Retrieval-Augmented Generation: retrieve relevant chunks and pass them to the LLM as grounding context. | [6.3](06-oracle-ai-database-agentic-ai/03-oracle-ai-vector-search-workflow.md) |
| **ReAct** | Reason + Act: the model interleaves reasoning steps with tool calls and observations. | [1.3](01-introduction-to-ai-agents/03-reasoning-patterns.md) |
| **Responses API** | OpenAI's stateful API for agents with function calling and built-in tools; OCI offers an OpenAI-compatible version. | [4.2](04-openai-responses-api-agents-sdk/02-openai-responses-api.md) |
| **Runner** | The Agents SDK component that runs the agent loop (`Runner.run` / `run_sync`). | [4.3](04-openai-responses-api-agents-sdk/03-openai-agents-sdk.md) |
| **Select AI** | Oracle Autonomous Database's natural-language-to-SQL capability, driven by AI Profiles. | [6.7](06-oracle-ai-database-agentic-ai/07-oracle-autonomous-ai-database-mcp-server.md) |
| **Tracing** | Recording each model call, tool call and handoff for debugging and observability. | [4.3](04-openai-responses-api-agents-sdk/03-openai-agents-sdk.md) |
| **Transports (stdio / Streamable HTTP)** | How MCP messages travel: stdio for local servers, Streamable HTTP for remote ones. | [3.3](03-model-context-protocol/03-core-mcp-concepts.md) |
| **Tree-of-Thought** | Exploring several reasoning paths in parallel and evaluating them before committing to one. | [1.3](01-introduction-to-ai-agents/03-reasoning-patterns.md) |
| **VECTOR data type** | Oracle's native column type for storing embeddings alongside business data. | [6.3](06-oracle-ai-database-agentic-ai/03-oracle-ai-vector-search-workflow.md) |
| **Vector Indexes (HNSW / IVF)** | Approximate indexes that make similarity search fast without full table scans. | [6.3](06-oracle-ai-database-agentic-ai/03-oracle-ai-vector-search-workflow.md) |
| **VECTOR_DISTANCE** | SQL function that scores similarity between vectors (cosine, Euclidean, dot product, etc.). | [6.3](06-oracle-ai-database-agentic-ai/03-oracle-ai-vector-search-workflow.md) |

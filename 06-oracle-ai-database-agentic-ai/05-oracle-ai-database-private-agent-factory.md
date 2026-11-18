[🏠 Home](../README.md) › [Module 6: Agentic AI for Oracle AI Database](README.md) › 6.5

# 6.5 Oracle AI Database Private Agent Factory

- Oracle AI Database Private Agent Factory is a no-code platform designed for business users and engineers to build, test, govern, and deploy enterprise-grade AI agents. It shifts agent development away from ad-hoc external tools by anchoring workflows directly to approved corporate data sources, database capabilities, and enterprise governance frameworks.

## Key Capabilities & Governance

- Building an enterprise agent requires more than basic prompt engineering. Agent Factory provides full-stack governance across the agent lifecycle:

- **Enterprise Integrations:** Natively connects to relational databases, REST APIs, Model Context Protocol (MCP) servers, and internal tools.

- **Security & Access Control:** Enforces Single Sign-On (SSO), role-based access management, and strict prompt guardrails.

- **Grounded Reasoning:** Ensures outputs are traceable to source-linked responses rather than hallucinations.

- **Model Flexibility:** Allows teams to configure and swap Large Language Models (LLMs) and embedding models based on security and performance requirements.

## Architecture & Deployment Modes

- When a user submits a natural language request, Agent Factory routes the query through the defined agent workflow. The workflow dynamically calls the configured LLM, queries structured tables, searches vector stores, or executes tools before returning a grounded response.

- The platform is deployed as a containerized application managed via **Podman** and **Podman Compose**, running on-premises, on Oracle Cloud Infrastructure (OCI), or across multi-cloud environments (AWS, Azure, Google Cloud):

- **Production Mode:** Connects to user-provisioned enterprise database instances (Oracle Database 19c+ or 26ai) and dedicated model endpoints.

- **Quick Start Mode:** Packages local containers—including the Oracle AI Database 26ai Free container—to provide a self-contained, rapid evaluation environment.

## Pre-Built Enterprise Agents

- Agent Factory ships out-of-the-box with two production-ready agents tailored for different data modalities:

| **Feature**             | **Knowledge Agent**                         | **Data Analysis Agent**                               |
|-------------------------|---------------------------------------------|-------------------------------------------------------|
| **Primary Data Type**   | Unstructured content                        | Structured database tables                            |
| **Supported Sources**   | SharePoint, Google Drive, websites, files   | Oracle Database 19c+, 26ai, Autonomous DB             |
| **Core Mechanism**      | Automated RAG pipeline & Vector Search      | Schema-aware Natural Language to SQL (NL2SQL)         |
| **Key Output Feature**  | Clickable source citations for traceability | SQL queries, charts, data tables, and explanations    |
| **Advanced Capability** | Auto-crawls, chunks, and embeds documents   | Suggests follow-up queries via **Variation Analysis** |

## Agent Builder & Custom Workflows

- For custom requirements beyond the pre-built agents, the platform provides **Agent Builder**—a drag-and-drop visual canvas that constructs workflows using modular nodes:

- **Core Nodes:** LLM routers and specialized sub-agents.

- **Tool & Integration Nodes:** REST APIs, MCP servers, Oracle Select AI, and external tools (e.g., Wikipedia search).

- **Output Nodes:** Formatted chat responses or automated email dispatches.

## Workflow Complexity Levels

1. **Simple Routing:** Direct question-and-answer exchanges between a user and an LLM.

2. **Tool-Enabled:** Workflows that trigger external APIs or query MCP servers to fetch real-time context before answering.

3. **Advanced Custom:** Execution of custom Python-based components and scripts inside the workflow.

4. **Multi-Agent Orchestration:** A primary manager agent analyzes complex user requests and delegates sub-tasks to specialized sub-agents.

## From Prototype to Production

- **Interactive Playground:** Developers test, debug, and refine agent reasoning and tool execution in a real-time sandbox.

- **API Publishing:** Once validated, publishing an agent exposes a secure HTTP POST endpoint, allowing enterprise applications to embed and invoke the workflow programmatically.

---

### 🔗 Related

- **Model Context Protocol (MCP)** → [3.2 What Is MCP?](../03-model-context-protocol/02-what-is-mcp.md)
- **MCP Host / Client / Server** → [3.3 Core MCP Concepts](../03-model-context-protocol/03-core-mcp-concepts.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [6.4 Demo: Oracle AI Vector Search](04-demo-oracle-ai-vector-search.md) | [⬆️ Module 6](README.md) | [6.6 Demo: Private Agent Factory](06-demo-private-agent-factory.md) ➡️

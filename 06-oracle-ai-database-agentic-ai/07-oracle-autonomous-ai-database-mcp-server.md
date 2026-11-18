[🏠 Home](../README.md) › [Module 6: Agentic AI for Oracle AI Database](README.md) › 6.7

# 6.7 Oracle Autonomous AI Database MCP Server

- The Oracle Autonomous AI Database (ADB) MCP Server is a **built-in, fully managed feature** that runs natively inside the database service. Unlike traditional deployments, it allows any Model Context Protocol (MCP) compatible client (such as Claude Desktop, VS Code with Cline, or LangChain) to securely interact with database tools and data over plain HTTPS, without requiring third-party integration infrastructure.

## 1. Traditional vs. Database-Native MCP Servers

- Running a third-party MCP server externally alongside an enterprise database introduces operational and architectural friction. Putting the MCP server directly inside the database resolves three critical problems:

| **Challenge Area**       | **External 3rd-Party MCP Server**                                                                                                                         | **Native Oracle ADB MCP Server**                                                                                                                                              |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Operational Overhead** | Requires deploying, patching, scaling, and securing separate containers or VMs (e.g., in Kubernetes).                                                     | **Zero infrastructure:** Activated via a single OCI free-form tag (adb\$feature). Oracle automatically handles high availability, scaling, and patching.                      |
| **Schema Discovery**     | Forces LLMs into a multi-step "dance" (list schemas → list tables → describe columns) that consumes tokens and increases latency. | **Bypasses discovery:** Leverages Select AI **AI Profiles**, which pre-register schemas, column metadata, and sample queries natively.                                        |
| **Security Mapping**     | Demands custom authorization code to map external MCP caller identities to internal database user privileges.                                             | **Native RBAC:** Uses standard database login credentials. All enterprise security controls (Role-Based Access Control, ACLs, Virtual Private Databases) apply automatically. |

## 2. Architectural Blueprint

- The native MCP architecture connects external clients to internal database engines using a streamlined, streamable HTTPS transport layer:

```text
[ MCP Clients ] ──(HTTPS / Streamable HTTP)──> [ Oracle Autonomous AI Database ]
(LangChain, OpenAI SDK, etc.)                    ├── 1. Multi-Tenant MCP Endpoint
                                                 └── 2. Select AI Agent Tools Engine
```

## Core Components

- **Streamable HTTP Endpoint:** Serves as the sole transport surface. It is a multi-tenant service managed by Oracle that hosts isolated endpoints for distinct ADB instances, keyed directly off each database's unique Cloud Identifier (OCID).

- **Select AI Agent Framework:** The engine does not invent a new tool format. Instead, it exposes tools created via the native `DBMS_CLOUD_AI_AGENT` PL/SQL package. Any custom tool defined in the schema instantly becomes a callable MCP tool.

## 3. Primary Execution & Extensibility Patterns

- **Natural Language to SQL (NL2SQL):** The headline use case. By relying on pre-registered AI Profiles, the server allows AI agents to bypass schema exploration and instantly compose and execute accurate SQL queries over enterprise tables.

- **Semantic Vector Retrieval:** Connects MCP clients directly to native vector indexes, enabling Retrieval-Augmented Generation (RAG) pipelines over unstructured enterprise data.

- **PL/SQL "Escape Hatch":** Any business logic, data transformation, or operational procedure that can be wrapped into a standard PL/SQL function can be published as a governed MCP tool.

## 4. Endpoint Structure & Security Boundary

## Managed Endpoint URL Format

- Each Autonomous Database instance is exposed via a standardized, secure HTTPS URL containing the instance's home region and unique OCID:

```text
https://dataaccess.adb.{region}.oraclecloudapps.com/adb/mcp/v1/databases/{database-ocid}
```

- **The Security Punchline:** *The database IS the security boundary.* There is no separate "MCP User" concept. The AI client connects using standard Oracle database credentials. If a database user is restricted from viewing a specific table row or executing a particular package via Virtual Private Database (VPD) policies, the AI agent calling through the MCP endpoint is strictly blocked by those exact same rules.

---

### 🔗 Related

- **AI Agent** → [1.1 What Is an AI Agent?](../01-introduction-to-ai-agents/01-what-is-an-ai-agent.md)
- **LangChain** → [2.2 Introduction to LangChain](../02-langchain-for-ai-agents/02-introduction-to-langchain.md)
- **Model Context Protocol (MCP)** → [3.2 What Is MCP?](../03-model-context-protocol/02-what-is-mcp.md)
- **MCP Host / Client / Server** → [3.3 Core MCP Concepts](../03-model-context-protocol/03-core-mcp-concepts.md)
- **RAG** → [6.3 Oracle AI Vector Search Workflow](03-oracle-ai-vector-search-workflow.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [6.6 Demo: Private Agent Factory](06-demo-private-agent-factory.md) | [⬆️ Module 6](README.md) | — ➡️

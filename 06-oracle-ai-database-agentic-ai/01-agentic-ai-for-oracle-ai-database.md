[🏠 Home](../README.md) › [Module 6: Agentic AI for Oracle AI Database](README.md) › 6.1

# 6.1 Agentic AI for Oracle AI Database

## Module Overview: Agentic AI for Oracle AI Database

This foundational module covers four core agentic AI services and features integrated directly into the Oracle AI Database ecosystem, shifting AI workflows from external application code to native database capabilities.

## Key Capabilities Summary

| **Capability / Service**           | **Architecture Type**     | **Target User**              | **Primary Function**                                                                           | **Course Coverage** |
|------------------------------------|---------------------------|------------------------------|------------------------------------------------------------------------------------------------|---------------------|
| **Oracle AI Vector Search**        | Built-in Database Feature | Developers / Data Engineers  | Store, index, and query vector embeddings alongside relational data using SQL.                 | Lessons 2, 3, and 4 |
| **Private Agent Factory**          | No-Code Platform          | Business Users / Engineers   | Build, test, and deploy custom or pre-built enterprise AI agents without code.                 | Lesson 5            |
| **Select AI Agent**                | Native Database Framework | Database Developers          | Build autonomous agents that live entirely inside the database using PL/SQL and SQL.           | Final two lessons   |
| **Autonomous Database MCP Server** | Native Protocol Server    | External AI Agents / Clients | Allow external MCP clients to securely query database capabilities without custom integration. | Final module lesson |

## 1. Oracle AI Vector Search & Autonomous AI Vector Database

- **Oracle AI Vector Search (Generally Available):** A foundational database feature that allows vector embeddings and traditional relational data to be stored, indexed, and searched together within a single system using standard SQL.

- **Oracle Autonomous AI Vector Database (Limited Availability - LA):** A fully managed cloud service built on top of the vector search engine. It operates in a self-driving environment that automatically handles provisioning, server tuning, scaling, and applying security patches.

- **Course Focus:** Because the Autonomous AI Vector Database is currently in Limited Availability, this module focuses exclusively on the foundational **Oracle AI Vector Search** feature.

## 2. Oracle AI Database Private Agent Factory ("Agent Factory")

- **No-Code Architecture:** Designed to let both engineers and business professionals build, test, and deploy intelligent enterprise workflows without writing application code.

- **Pre-Built Components:** Ships out-of-the-box with two standard agents:

  - **Knowledge Agent:** Optimized for information retrieval.

  - **Data Analysis Agent:** Optimized for analytical querying.

- **Customization Tools:** Includes a built-in **Visual Builder** and customizable templates for developing proprietary agentic workflows.

## 3. Select AI Agent (Autonomous Agent Framework)

- **The "Inside" Paradigm Shift:** Traditional agent frameworks (e.g., LangChain, OpenAI Agents SDK) reside in external application code and must reach into the database from the outside. Select AI Agent transforms the agent into a native "database citizen" that lives directly *inside* Oracle 23ai Database.

- **Core Mechanics:**

  - Configures Large Language Models (LLMs) natively through **AI Profiles**.

  - Accesses enterprise data and executes tools directly via **SQL**.

  - Managed entirely through **PL/SQL packages**, eliminating the need for external framework dependencies.

## 4. Oracle Autonomous Database MCP Server

- **Native Protocol Integration:** A Model Context Protocol (MCP) server integrated directly into the core database service rather than running as a third-party add-on or external OCI API server.

- **Secure External Access:** Once enabled, the database itself natively responds to MCP requests. This allows external AI agents and MCP clients to securely access database tools and enterprise data without custom integration code or manual security administration.

## Out-of-Scope Innovations (Not Covered in this Course)

To maintain a foundational scope, several advanced Oracle agentic AI features are excluded from this specific module:

- **Oracle Deep Data Security:** Next-generation data access control mechanisms designed to protect against AI-era threats.

- **Trusted Answer Search:** Specialized verification frameworks for query responses.

- **Oracle Vectors on Ice:** Cold-storage vector management.

- **Oracle Private AI Services Container:** Dedicated containerized AI service deployment.

---

### 🔗 Related

- **AI Agent** → [1.1 What Is an AI Agent?](../01-introduction-to-ai-agents/01-what-is-an-ai-agent.md)
- **Model Context Protocol (MCP)** → [3.2 What Is MCP?](../03-model-context-protocol/02-what-is-mcp.md)
- **MCP Host / Client / Server** → [3.3 Core MCP Concepts](../03-model-context-protocol/03-core-mcp-concepts.md)
- **Oracle AI Vector Search** → [6.2 Introduction to Oracle AI Vector Search](02-introduction-to-oracle-ai-vector-search.md)
- **Embeddings** → [6.3 Oracle AI Vector Search Workflow](03-oracle-ai-vector-search-workflow.md)
- **Private Agent Factory** → [6.5 Oracle AI Database Private Agent Factory](05-oracle-ai-database-private-agent-factory.md)
- **Select AI** → [6.7 Oracle Autonomous AI Database MCP Server](07-oracle-autonomous-ai-database-mcp-server.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [5.8 Summary](../05-oci-enterprise-ai-agents/08-summary.md) | [⬆️ Module 6](README.md) | [6.2 Introduction to Oracle AI Vector Search](02-introduction-to-oracle-ai-vector-search.md) ➡️

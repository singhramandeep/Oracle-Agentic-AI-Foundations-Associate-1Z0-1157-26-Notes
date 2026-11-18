[🏠 Home](../README.md) › [Module 3: Introduction to MCP](README.md) › 3.2

# 3.2 What Is MCP?

- **Definition:** Model Context Protocol (MCP) is an open, vendor-neutral standard that standardizes how AI applications connect to external tools, data sources, and systems.

- **The "USB-C for AI" Analogy:** Just as USB-C allows any compatible hardware device to connect to any compatible port, MCP allows any compatible AI client to connect to any compatible tool server.

- **Underlying Protocol:** Built on **JSON-RPC 2.0** (JavaScript Object Notation Remote Procedure Call), a lightweight, JSON-based wire protocol designed for structured request-response communication.

## The Problem MCP Solves: From Quadratic to Linear Complexity

- **Before MCP (**n × m **Quadratic Problem):** Every AI application required a custom integration for every individual tool.

  - *Example:* Connecting 3 AI applications (e.g., Claude, ChatGPT, custom app) to 4 tools required **12 separate, custom integrations**, creating complex and hard-to-maintain plumbing.

- **After MCP (**n + m **Linear Solution):** Each AI application builds **one** MCP client, and each tool exposes **one** MCP server.

  - *Example:* Connecting those same 3 AI applications to 4 tools now requires only **7 total integrations** (3 clients + 4 servers).

## MCP Architecture: The 3 Key Participants

## 1. The Host

- **Role:** The AI application the user directly interacts with (e.g., Claude Desktop, Cursor IDE, VS Code).

- **Core Responsibilities:**

  - Houses the LLM that performs the ReAct (Reason/Act) reasoning.

  - Creates and manages one or more MCP clients.

  - Handles context aggregation across multiple clients.

## 2. The Client

- **Role:** Created by the host to establish connectivity with servers.

- **Connection Rule:** A standard MCP client maintains a dedicated **1-to-1 connection** with exactly one MCP server.

- **Specialized Exception:** Frameworks like LangChain offer specialized multi-server clients capable of loading tools, prompts, and resources from multiple servers into a single client instance.

## 3. The Server

- **Role:** Independent programs that provide external context to the LLM.

- **Exposed Context:**

  - **Tools** (actions to execute).

  - **Data/Resources** (information to read).

  - **Prompts** (predefined interaction templates).

- **System Connections:** Can integrate with local file systems or external systems like GitHub, Slack, and enterprise databases.

- **Decoupling:** Servers are strictly decoupled from clients; they operate independently without needing to know which specific AI host is calling them.

## Communication & Transport Mechanisms

MCP relies on **JSON-RPC 2.0** over two distinct transport layers:

1. **Standard Input/Output (stdin/stdout):** Used primarily for running **local servers** directly on a user's machine without networking overhead.

2. **Streamable HTTP:** Used for connecting to **remote servers** deployed in cloud environments.

---

### 🔗 Related

- **MCP Host / Client / Server** → [3.3 Core MCP Concepts](03-core-mcp-concepts.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [3.1 Module Introduction](01-module-introduction.md) | [⬆️ Module 3](README.md) | [3.3 Core MCP Concepts](03-core-mcp-concepts.md) ➡️

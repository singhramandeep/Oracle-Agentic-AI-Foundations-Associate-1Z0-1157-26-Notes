[🏠 Home](../README.md) › [Module 3: Introduction to MCP](README.md) › 3.3

# 3.3 Core MCP Concepts

## MCP Core Components and Architecture

## 1. The Three MCP Primitives

MCP servers expose three distinct core components:

- **Tools (Doing something):** Functions or actions that the model can take which cause side effects (e.g., executing a calculation or querying an API). This is the most commonly used primitive.

- **Resources (Reading something):** Data sources that the model can read for context without causing side effects.

- **Prompts (Structuring something):** Predefined interaction templates or UI shortcuts (like /review) that load complex system instructions without manual typing.

## 2. Connection Lifecycle (4 Phases)

1. **Initialization:** The client sends an initialization request with its protocol version and capabilities. The server responds with its own version/capabilities, and the client confirms it is ready to exchange messages.

2. **Discover:** The client asks the server what primitives it offers. The server returns schemas detailing the available tools, resources, and prompts (including tool names, descriptions, and expected input arguments).

3. **Operate:** The active reasoning loop where real work happens:

    - Client receives a user query and sends it along with the discovered tool list to the LLM.

    - LLM decides which tool to call and sends the request back to the client.

    - Client executes the call against the server, and the result flows back to the LLM.

4. **Shutdown:** The client cleanly closes the transport connection once interactions are complete.

## 3. Messaging Protocol: JSON-RPC 2.0

- **Why JSON-RPC?** Unlike REST (which is designed primarily for simple client-to-server requests), JSON-RPC 2.0 natively supports **bidirectional communication**.

- **Message Structure:** Every message contains the "jsonrpc" version string, an "id" to link requests to responses, and either a method/params payload (for requests) or a result/error payload (for responses).

- **Framework Automation:** While libraries like LangChain and FastMCP handle JSON-RPC message construction automatically, understanding the raw payload structure is essential for debugging.

## 4. Key Agent Methods for Tools

- **`tools/list`:** Called dynamically when the client connects. The server responds with all available tools and their schemas, eliminating the need to hardcode tool definitions into the application code.

- **`tools/call`:** Used when the LLM decides to execute a tool. The client sends the chosen tool name and generated arguments to the server, which executes the function and returns the computation result.

## 5. Transport Mechanisms

Because JSON-RPC 2.0 is just a message format, it is not bound to a single networking layer. MCP leverages this to support two distinct transport mechanisms without changing the underlying protocol:

| **Transport Type**                | **Target Environment** | **How It Works**                                                                                 | **Key Characteristics**                                                                     |
|-----------------------------------|------------------------|--------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| **Standard Input/Output (stdio)** | Local Servers          | The host application spawns the MCP server as a local child/sub-process.                         | Simplest setup, fastest execution, zero network overhead. Server must be locally installed. |
| **Streamable HTTP**               | Remote / Cloud Servers | Client sends requests via HTTP POST; server streams responses back via Server-Sent Events (SSE). | Supports cloud deployments, multiple concurrent clients, and standard HTTP authentication.  |

---

### 🔗 Related

- **Model Context Protocol (MCP)** → [3.2 What Is MCP?](02-what-is-mcp.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [3.2 What Is MCP?](02-what-is-mcp.md) | [⬆️ Module 3](README.md) | [3.4 Add an MCP Server to Your First Agent](04-add-an-mcp-server-to-your-first-agent.md) ➡️

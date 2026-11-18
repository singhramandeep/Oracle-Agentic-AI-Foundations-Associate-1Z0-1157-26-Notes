[🏠 Home](../README.md) › [Module 3: Introduction to MCP](README.md) › 3.5

# 3.5 Demo: MCP Server with LangChain Clients and Codex

## Core Takeaway: "Define Once, Use Everywhere"

- **The Fundamental Shift:** Tool logic moves out of individual agent scripts and into a dedicated, reusable **Model Context Protocol (MCP) server**.

- **Interoperability:** Once defined, the exact same server and its tools can be automatically discovered and executed by any MCP-compatible AI host (e.g., custom LangChain scripts, OpenAI's Codex) with **zero modifications** to the server code.

## Part 1: LangChain Client & Local Server Execution

## 1. Codebase Refactoring

- **Before MCP:** Tools (add, multiply, divide, `square_root`) were hardcoded directly inside the agent script using `@tool` decorators, tightly coupling them to a single file.

- **After MCP:** Local tool definitions are removed/commented out. The agent code is updated at a single integration point to connect to the external MCP math server, allowing the client to dynamically discover available tools at runtime.

- **Agent Logic:** Core orchestration—agent creation, execution, invocation, and testing—remains completely unchanged.

## 2. Server Behavior & Standard I/O Transport

- **Terminal Execution Observation:** Running the MCP server directly in the terminal results in silence and no visible activity.

- **Why Silence is Normal:**

  - The server is configured with **Standard Input/Output (stdio) transport**.

  - On startup, the process immediately blocks, waiting passively to read incoming JSON-RPC messages over stdin.

  - Because no client is feeding it data in a standalone terminal, it sits idle. A silent terminal confirms a healthy state.

- **Subprocess Spawning:** In practice, a host application (like LangChain or Codex) launches the server as a background subprocess and automatically pipes JSON-RPC requests into it.

## 3. Client Execution & Edge Case Testing

- When the LangChain client script runs, it spawns the math server, discovers the four math tools dynamically, and executes a test suite:

  - Standard operations: addition, multiplication, and square root area calculations.

  - Boundary/Edge case: Dividing 100 by 0.

## Part 2: Cross-Host Reusability with OpenAI's Codex

## 1. Integrating with a Third-Party Host

- **The Host:** **Codex** (OpenAI's coding agent for software development), representing a completely different, off-the-shelf host application.

- **Configuration:** Connected by adding a couple of lines to Codex's configuration file, pointing it to the exact same Python math server used by LangChain. Zero changes were made to the math server codebase.

## 2. Tool Discovery in Codex

- **/mcp Command:** Displays server status, confirming the math server is connected and active (with authentication labeled as unsupported/unneeded for this local setup).

- **/mcp math Command:** Dynamically queries the server and lists the four discovered tools (add, multiply, divide, `square_root`).

## 3. Prompt Steering & Execution Control

- **Target Prompt:** "use the math MCP server divide tool on 100 divided by 0. Do not run shell commands or write code."

- **Why Steering is Required:** Highly capable hosts like Codex possess built-in execution environments (like local shells) and will natively compute mathematical calculations themselves unless explicitly directed to route the request to the external MCP server.

## 4. Security Handshake & Verification

- **Approval Card:** Before executing the external action, Codex halts execution and presents an interactive user permission prompt: *"allow the math MCP server to run tool divide"* displaying the exact target arguments (a=100, b=0).

- **Execution Proof:** Upon clicking **Allow**, the server executes the request and returns the exact Python string defined in the backend code: "error, cannot divide by 0".

- **Confirmation:** Receiving this exact string proves the computation was handled strictly by the external Python MCP server rather than Codex's internal LLM reasoning or local shell.

## Architecture Summary: Before vs. After MCP

| **Architectural Dimension**           | **Before MCP (Monolithic Agent)**                               | **After MCP (Client-Server Architecture)**                                   |
|---------------------------------------|-----------------------------------------------------------------|------------------------------------------------------------------------------|
| **Tool Location**                     | Hardcoded locally via `@tool` decorators inside the agent script. | Hosted independently inside a standalone MCP server file.                    |
| **Tool Discovery**                    | Static; hardwired directly into the application logic.          | Dynamic; queried at runtime via JSON-RPC over stdio.                         |
| **Code Reusability**                  | None; tool logic is trapped inside a single Python script.      | High; any compatible AI host (LangChain, Codex) connects to the same server. |
| **Server Code Changes for New Hosts** | N/A (Required copying and pasting tool code into new projects). | **Zero code changes required.**                                              |

---

### 🔗 Related

- **LangChain** → [2.2 Introduction to LangChain](../02-langchain-for-ai-agents/02-introduction-to-langchain.md)
- **Model Context Protocol (MCP)** → [3.2 What Is MCP?](02-what-is-mcp.md)
- **MCP Host / Client / Server** → [3.3 Core MCP Concepts](03-core-mcp-concepts.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [3.4 Add an MCP Server to Your First Agent](04-add-an-mcp-server-to-your-first-agent.md) | [⬆️ Module 3](README.md) | [3.6 Real-World MCP Walkthrough](06-real-world-mcp-walkthrough.md) ➡️

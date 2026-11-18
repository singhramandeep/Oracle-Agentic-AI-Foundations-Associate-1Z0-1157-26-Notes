[🏠 Home](../README.md) › [Module 3: Introduction to MCP](README.md) › 3.6

# 3.6 Real-World MCP Walkthrough

## 1. Sandbox vs. Real-World MCP: The Paradigm Shift

- In earlier learning exercises (like the math server), developers write both the client and the server. While ideal for learning basic mechanics, real-world Model Context Protocol (MCP) usage rarely looks like a sandbox environment.

- **Production Reality:** In production, the MCP server is almost always built and published by a third party (e.g., a software vendor like Oracle, a SaaS provider, or another internal team).

- **The "Black Box" Constraint:** As a developer, **you only write the client**. You do not read the server's source code, and you cannot inject print statements to debug failures. You must interact with the server entirely through standard protocol methods (`tools/list`, `tools/call`, and structured error responses).

- **Core Value Proposition:** MCP "earns its keep" in this regime. Vendors expose their tools **once**, and AI clients everywhere can consume them without writing custom, bespoke integration plumbing.

## What Stays the Same vs. What Changes

- When shifting from a locally written sandbox server to a third-party published server, the architecture evolves while the underlying protocol remains constant:

| **Architectural Aspect** | **What Stays the Same**                                                           | **What Changes**                                                                                                            |
|--------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **Protocol & Messaging** | Uses standard **JSON-RPC 2.0** for all communications.                            | **Server Ownership:** Built, updated, and published by an external entity (e.g., Oracle).                                   |
| **Tool Mechanics**       | Relies on dynamic discovery (`tools/list`) and execution (`tools/call`).              | **Backend Wrapping:** The server now wraps real-world enterprise REST APIs and cloud SDKs rather than local Python scripts. |
| **Client Code Shape**    | The agent orchestration loop and client configuration structure remain identical. | **Execution Environment:** Managed via isolated package execution rather than manual local file referencing.                |

## 2. The OCI Usage MCP Server

- To demonstrate real-world usage, the course utilizes Oracle's officially published **OCI Usage MCP Server** (`oracle.oci-usage-mcp-server`).

- **Distribution:** Published officially on **PyPI** (the Python Package Index, the centralized repository for third-party Python software).

- **What it Wraps:** It acts as a wrapper around the exact same **OCI Cost Analysis API** that powers the Oracle Cloud Infrastructure (OCI) Console's billing page.

- **Surface Area:** The server exposes a single, highly focused tool:

  - `get_summarized_usage`: Accepts arguments such as tenant ID, start time, end time, and granularity.

- **Verification Capability:** Because the server wraps the live billing API, any data returned by the agent can be verified "pixel-for-pixel" down to the exact cent against the actual OCI Console.

## 3. Architecture & Execution Mechanics

- A critical insight of this architecture is understanding **where the network boundaries lie**:

- \[ LangChain AI Agent \] --- (stdio / Local Pipes) ---\> \[ OCI Usage MCP Server \] --- (HTTPS / Internet) ---\> \[ OCI Usage REST API \]

## Local Transport vs. Remote API Calls

- **Local Communication (stdio):** Even though the OCI Usage MCP Server is an enterprise integration tool, **it runs locally on the same machine as the client**. There is zero network connection between your Python script and the MCP server process; they communicate through local standard input and output pipes (stdin / stdout).

- **Remote Communication (HTTPS):** The network boundary exists strictly between the local MCP server process and Oracle's cloud servers. The MCP server makes the outbound HTTPS calls to the OCI REST APIs to fetch billing data. Your client script **never** speaks directly to OCI.

## Why uvx is Used for Execution

- In the client configuration, the execution directive uses uvx instead of a standard python command:

- **What is uvx?** A utility shipping with the uv ecosystem that runs a Python package without permanently installing it into the local environment (analogous to npx in the Node.js ecosystem).

- **How it Works:** When triggered, uvx downloads `oracle.oci-usage-mcp-server` from PyPI, caches it, installs it into a temporary isolated environment, launches its entry point as a normal Python process, and opens its stdio pipes for the client.

- **Developer Advantage:** It eliminates environmental friction. Developers do not need to manually pip install packages, manage virtual environments, or debug dependency version conflicts.

## 4. Real-World Demo & Console Verification

- In the accompanying demonstration, an AI agent built with LangChain (powered by the **GPT-5.5** model) connects to the published OCI Usage MCP Server to analyze cloud expenditure.

## Step 1: Agent Execution (oci_usage_mcp_agent.py)

- **User Prompt:** *"Show me the cost for last 30 days as a daily breakdown by service."*

- **The Process:** The script verifies the API key, invokes the LLM reasoning loop, dynamically discovers the `get_summarized_usage` tool, and executes it for the specified 30-day window (May 5 to June 3/4).

## Step 2: Dual Output Generation

1. **Console Terminal Output:** Prints a textual summary and commentary highlighting major cost drivers (e.g., noting active workloads in VMware OCVS clusters, databases, and block storage, as well as identifying a recent cost drop caused by a stopped cluster).

2. **CSV File Generation:** Automatically compiles a structured spreadsheet detailing the exact daily cost breakdown by individual cloud service over the 30-day period.

## Step 3: "Pixel-for-Pixel" Verification

- To prove the MCP server reliably executes real enterprise tasks, the CSV output is audited against the live **OCI Console -\> Cost Management -\> Cost Analysis** dashboard:

- **Total Expenditure:** Both the generated spreadsheet and the OCI Console report a total cost of **~\$6,200** (just under \$6,200) for the account.

- **Line-Item Audit (Exact Cent Matching):**

  - **Block Storage:** Matches exactly at **~\$1,300**.

  - **Database:** Matches exactly at **~\$1,400**.

  - **VMware:** Matches down to the exact cent at **\$1,951**.

## 5. Enterprise Takeaways & Use Cases

- This architecture demonstrates how the Model Context Protocol transforms enterprise integrations:

- **Eliminating Custom Plumbing:** A third-party SaaS provider (such as a cloud cost management platform) can integrate with OCI billing by simply connecting a standard MCP client to Oracle's published server, completely avoiding the need to build and maintain custom API connectors.

- **Advanced AI Layering:** Once the data is retrieved through the standardized MCP interface, developers can seamlessly layer LLMs on top to perform natural language trend analysis, anomaly detection, and automated cost forecasting.

---

### 🔗 Related

- **LangChain** → [2.2 Introduction to LangChain](../02-langchain-for-ai-agents/02-introduction-to-langchain.md)
- **Model Context Protocol (MCP)** → [3.2 What Is MCP?](02-what-is-mcp.md)
- **MCP Host / Client / Server** → [3.3 Core MCP Concepts](03-core-mcp-concepts.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [3.5 Demo: MCP Server with LangChain Clients and Codex](05-demo-mcp-server-with-langchain-clients-and-codex.md) | [⬆️ Module 3](README.md) | [3.7 Summary](07-summary.md) ➡️

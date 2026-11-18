[🏠 Home](../README.md) › [Module 6: Agentic AI for Oracle AI Database](README.md) › 6.6

# 6.6 Demo: Private Agent Factory

## Oracle AI Database Private Agent Factory: Practical Demo

The Private Agent Factory is a visual, containerized no-code platform that allows developers and business users to create, test, and deploy enterprise-grade AI agents. Because these agents operate natively inside your infrastructure (deployed via OCI Marketplace virtual machines running on port 8080), your sensitive enterprise data never needs to leave your security boundary.

## 1. Knowledge Agent (Unstructured Data & RAG)

The Knowledge Agent is an automated Retrieval-Augmented Generation (RAG) system built to parse and synthesize unstructured content (such as internal websites, PDF documentation, and file systems).

## Demo Execution Flow

1. **Context & Ingestion:** The agent is connected to a pre-configured data source—in this demo, the *Private Agent Factory Documentation* website crawled by the system.

2. **User Prompt:** A user initiates a chat session and asks: *"How do I set up Private Agent Factory?"*

3. **Agent Synthesis:** The agent queries the ingested vector store and generates a step-by-step installation guide detailing the **Production Mode** and **Quick Start Mode**.

4. **Source Traceability:** To prevent hallucinations and enforce trust, the response embeds clickable inline citations and links directly to the corresponding sections of the source documentation.

## 2. Data Analysis Agent (Structured Data & NL2SQL)

The Data Analysis Agent connects directly to relational database tables and CSV datasets to translate natural language into safe SQL queries, automated visual plots, and statistical summaries.

## Demo Execution Flow

1. **Agent Setup:** The user selects **Create Agent**, attaches the out-of-the-box **Netflix Dataset**, and names it "Netflix agent".

2. **Exploration Mode:** Upon publishing, the agent launches an automated exploration workflow. It inspects the dataset schema, generates sample business questions, and auto-executes the necessary SQL and visual charts.

3. **Interactive Analysis:**

    - *Query 1:* *"How many titles were added to each genre in January 2020?"* → The agent outputs an aggregated genre breakdown.

    - *Query 2:* *"Show movies released before 2000 but added in the last five years along with their ratings."* → The agent translates the multi-condition prompt into SQL and returns a structured data table.

## 3. Agent Builder (No-Code Custom Workflows)

For custom requirements beyond the two pre-built agents, the **Agent Builder** provides a LangFlow-style drag-and-drop visual canvas to construct end-to-end agentic pipelines.

\[ Chat Input Node \] ──(User Message)──\> \[ Agent Node (Grok LLM) \] ──(Response)──\> \[ Chat Output Node \]

## Step-by-Step Canvas Configuration

- **Step 1 (Add Input):** Drag a **Chat Input** node onto the canvas to capture live user prompts.

- **Step 2 (Configure Agent & LLM):** Drag an **Agent** node onto the canvas. In the node settings, select the target Large Language Model (in this demo, a configured **Grok LLM** endpoint).

- **Step 3 (Link Nodes):** Click and drag a connection wire from the Chat Input node to the Agent node's prompt input.

- **Step 4 (Add Output):** Drag a **Chat Output** node onto the canvas and wire the Agent’s output message port directly into it.

- **Step 5 (Test in Playground):** Save the workflow and open the **Playground**. Submitting the test query *"What is Oracle AI Vector Search?"* routes the text through the visual canvas to the Grok LLM and streams the generated response back to the chat UI.

## Enterprise Extensibility

While this demo shows a simple text-in/text-out workflow, the visual canvas supports complex production patterns by allowing developers to drop in additional integration nodes:

- **Select AI Agents** for database-native reasoning.

- **Model Context Protocol (MCP) Servers** for third-party tool execution.

- **REST APIs** and enterprise system connectors (e.g., Slack, Confluence, ERPs).

---

### 🔗 Related

- **Model Context Protocol (MCP)** → [3.2 What Is MCP?](../03-model-context-protocol/02-what-is-mcp.md)
- **RAG** → [6.3 Oracle AI Vector Search Workflow](03-oracle-ai-vector-search-workflow.md)
- **Private Agent Factory** → [6.5 Oracle AI Database Private Agent Factory](05-oracle-ai-database-private-agent-factory.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [6.5 Oracle AI Database Private Agent Factory](05-oracle-ai-database-private-agent-factory.md) | [⬆️ Module 6](README.md) | [6.7 Oracle Autonomous AI Database MCP Server](07-oracle-autonomous-ai-database-mcp-server.md) ➡️

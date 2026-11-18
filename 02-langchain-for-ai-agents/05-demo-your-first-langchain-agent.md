[🏠 Home](../README.md) › [Module 2: LangChain for AI Agents](README.md) › 2.5

# 2.5 Demo: Your First LangChain Agent

## Overview of the AI Agent Demo

- **Core Concept**: Demonstrates a simple AI agent using the **ReAct pattern** (Reason, Act, Observe loop) via LangChain's `create_agent` function.

- **Prerequisites**: Installation of LangChain (and related packages) and an available OpenAI API key.

## Step-by-Step Agent Implementation

## 1. Environment Setup

- **Action**: Load environment variables from a separate file.

- **Best Practice**: Never store sensitive data like API keys directly inside code files to keep secrets secure.

## 2. Step 1: Initialize the Model

- **Role**: Acts as the **"brain"** that interprets questions, decides which tool to use, and generates the final output.

- **Specifics**: Initialized using the GPT-55 chat model.

## 3. Step 2: Define Tools

- **Role**: Acts as the **"hands"** that allow the agent to execute actions rather than just generating text responses.

- **Requirements**: Every tool must contain a clear name, a descriptive docstring (critical for the LLM), and type hints so the LLM understands the expected inputs.

- **Functions Used**: multiply, divide, and add.

## 4. Step 3: Create the Agent (Orchestration Layer)

- **Implementation**: A one-line `create_agent` function combining the model and the tools.

- **Framework Benefit**: Hides orchestration complexity by automatically building the full ReAct loop (Reasoning -\> Acting/Calling a tool -\> Observing results -\> Repeating) so the developer does not have to write the loop manually.

## 5. Step 4: Run the Agent

- **Implementation**: Executed by calling `agent.invoke` with a specific question.

- **Execution Levels**: Evaluated using three questions of increasing complexity (simple addition, two operations, and a complex question).

## Agent Execution Trace & Workflow

- **Definition**: A journey map showcasing the interaction trace between the user, framework, and LLM.

- **Workflow Execution**:

  1. The user submits a question.

  2. The LLM evaluates whether it can answer directly or requires an external tool.

  3. **Execution Separation**: The LLM does *not* execute the tool itself. It signals the framework (LangChain) to execute the tool on its behalf.

  4. The framework runs the tool, captures the results, and sends the observation back to the LLM.

  5. The LLM processes the data and generates the final answer.

---

### 🔗 Related

- **Orchestration Layer** → [1.2 Agentic AI Core Components](../01-introduction-to-ai-agents/02-agentic-ai-core-components.md)
- **ReAct** → [1.3 Reasoning Patterns](../01-introduction-to-ai-agents/03-reasoning-patterns.md)
- **LangChain** → [2.2 Introduction to LangChain](02-introduction-to-langchain.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [2.4 Building Your First Agent with LangChain](04-building-your-first-agent-with-langchain.md) | [⬆️ Module 2](README.md) | [2.6 LangChain Agents Under the Hood (Part 1)](06-langchain-agents-under-the-hood-part-1.md) ➡️

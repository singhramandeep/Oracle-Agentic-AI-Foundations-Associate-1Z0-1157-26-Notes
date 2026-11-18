[🏠 Home](../README.md) › [Module 2: LangChain for AI Agents](README.md) › 2.2

# 2.2 Introduction to LangChain

## Introduction to LangChain: Core Building Blocks

At a high level, **LangChain** is an open-source framework for building applications powered by Large Language Models (LLMs).

While an LLM alone is powerful at generating text, answering questions, and reasoning, it is fundamentally limited: it cannot call APIs, access databases, or execute code on its own. LangChain solves this by connecting the model to the outside world, allowing applications to take real-world actions rather than just generating passive text.

## 1. Three Core Capabilities of LangChain

LangChain transitions LLMs from simple models into comprehensive systems through three primary capabilities:

- **Connect:** Links the language model to external systems, such as APIs, tools, and databases.

- **Orchestrate:** Combines multiple processing steps into structured workflows, enabling multi-step logic instead of a single static response.

- **Build:** Enables the creation of full, end-to-end applications like AI agents, chatbots, and retrieval systems.

**Key Takeaway:** LangChain is not just about calling a model; it is about building systems around it.

## 2. The LangChain Ecosystem

The broader LangChain ecosystem consists of four main parts that support developers from beginner to advanced stages:

| **Ecosystem Part**  | **Core Function & Description**                                                                                                                                           | **Course Scope**          |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------|
| **1. LangChain**    | The core library containing all foundational building blocks (prompts, models, chains, and memory).                                                                       | **In Scope**              |
| **2. LangGraph**    | The recommended engine for building production agents. It models agent behavior as a graph with nodes and edges to provide fine control over loops, branching, and state. | Out of Scope              |
| **3. LangSmith**    | The observability layer used to trace every LLM call, tool invocation, and token spent for debugging and optimization.                                                    | Out of Scope              |
| **4. Integrations** | Over 500 connectors for various LLMs (OpenAI, Anthropic, Google, etc.), vector databases, search APIs, and more.                                                          | Out of Scope *(Advanced)* |

## 3. Core Building Blocks

## A. The Model (The Brain)

The model serves as the reasoning engine of any LangChain application.

- **Unified Interface:** LangChain provides a standardized interface to work across different providers (OpenAI, Anthropic, Google, or open-source models), allowing developers to switch models with minimal code changes.

- **Behavioral Nuance:** While the *interface* is unified, model *behavior* is not. Different models possess distinct capabilities (e.g., varying tool-calling proficiency, context window sizes, and reasoning behaviors). Always consult documentation to verify model support and capabilities.

## B. Prompt Templates (Steering the Model)

Prompt templates provide a structured, reusable way to communicate with the model. Instead of hardcoding prompt strings, templates use dynamic placeholders (e.g., explain {topic} to a beginner) that function like reusable program components—accepting inputs and returning structured outputs.

1. **Three Main Types of Prompt Templates:**

2. **Prompt Template:** Used for simple, straightforward tasks.

3. **Chat Prompt Template:** Designed for conversational models by defining explicit message roles:

    - **System Messages:** Special instructions that establish the AI model's overall behavior, tone, and capabilities.

    - **Human Messages:** Input or instructions originating from the end user.

    - **AI Messages:** The model's previous outputs or responses.

4. **Few-Shot Prompt:** Includes structured example inputs and outputs within the prompt to guide model behavior.

## C. Chains (The Namesake)

A chain is a sequence of processing steps where data flows continuously from one component to the next.

> **Prompt Template → LLM Model → Output Parser → Final Result**

- **LangChain Expression Language (LCEL):** LangChain uses the pipe operator (\|) to cleanly connect processing steps together (e.g., chain = prompt \| model \| parser). Each component transforms the data before passing it to the next step.

**Anatomy of a Simple Chain Execution (**`chain.invoke`**):**

When a simple three-step chain is executed, LangChain performs the following sequence under the hood:

1. **Template Filling:** It dynamically injects the input value into the prompt template placeholder (e.g., inserting "AI agent" into {topic} to generate the string *"explain AI agents"*).

2. **Model Processing:** It sends the formatted prompt to the selected LLM, which processes the text and returns a chat response.

3. **Output Parsing:** A parser (such as `StringOutputParser`) intercepts the model's structured chat response and converts it into a clean, plain Python string for the final output.

---

### 🔗 Related

- **AI Agent** → [1.1 What Is an AI Agent?](../01-introduction-to-ai-agents/01-what-is-an-ai-agent.md)
- **Chains / LCEL** → [2.3 Demo: LangChain Building Blocks](03-demo-langchain-building-blocks.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [2.1 Module Introduction](01-module-introduction.md) | [⬆️ Module 2](README.md) | [2.3 Demo: LangChain Building Blocks](03-demo-langchain-building-blocks.md) ➡️

[🏠 Home](../README.md) › [Module 2: LangChain for AI Agents](README.md) › 2.3

# 2.3 Demo: LangChain Building Blocks

## LangChain Code Building Blocks: Code Walkthrough Notes

## 1. Prerequisites

Before running the LangChain code demonstration, two main requirements must be fulfilled:

- **Required Packages:** Install LangChain and associated packages via the terminal command:

  - pip install langchain

- **OpenAI API Key:** Required because the example uses an OpenAI model (GPT 5.5).

  - Ensure account credits are added on the OpenAI platform dashboard (APIs will not work without credits).

  - Generate a key via **Create New Secret Key** (keys can be revoked anytime).

  - Load the saved key from an environment file into your development environment (e.g., Visual Studio Code).

## 2. Initializing & Invoking the Model (The Brain)

- **Unified Interface:** LangChain uses the `init_chat_model()` function to provide a single, universal interface across different LLM providers (e.g., switching effortlessly between OpenAI GPT 5.5, Anthropic Claude, or Google Gemini).

- **Universal Execution Method:** .`invoke()` is the universal method used across LangChain to run models and components.

- **Extracting Clean Output:**

  - When invoked with a text string (e.g., *"What is LangChain?"*), the model returns a full response object containing tokens and JSON metadata.

  - Use `response.content` to extract only the plain text answer from the response object.

## 3. Prompt Templates (Steering the Model)

Prompt templates are reusable structures that allow developers to write wording once and insert dynamic placeholders to be filled in later without hardcoding strings every time.

| **Template Type**        | **Structure & Description**                                                                                                                                                                                                                                                                                                                    |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Prompt Template**      | A simple reusable template containing dynamic placeholders to structure basic queries.                                                                                                                                                                                                                                                         |
| **Chat Prompt Template** | Built using structured message roles that match how conversational chat models expect their input:<br>• **System Role:** Sets the overall behavior and instructions for the LLM.<br>• **Human Role:** Represents the end user talking to the model (e.g., containing placeholders like requesting to explain a concept with a Python example). |

## 4. Chains (The Namesake & Pipeline)

Chains glue separate components together into an end-to-end processing pipeline where data flows continuously from left to right.

> **Prompt → Model → Parser**

- **The Pipe Operator (**\|**):** Used to connect reusable components together cleanly (e.g., Prompt \| Model \| Parser).

- **Component Roles in a Simple Chain:**

  1. **Prompt:** Dynamically fills in the blank placeholders with user input.

  2. **Model:** Processes the formatted prompt and generates an answer (e.g., GPT 5.5).

  3. **Parser (**`StringOutputParser`**):** Automatically pulls out and extracts the plain text string from the model's reply object, eliminating the need to manually write `response.content` every time.

- **Execution:** Executed by calling `chain.invoke()` and passing in dynamic values for the placeholders (e.g., passing "for" loops into the concept placeholder to generate an explanation and a code example).

## 5. Memory (Managing Conversation Context)

- **The Stateless Problem:** By default, LLMs are completely stateless—they forget everything between individual API calls.

- **How Memory Works:** Memory solves this by storing past conversation messages and dynamically feeding them back into the prompt so the model retains context.

- **Implementation Steps:**

  1. **Build a Store:** Create an In-memory Store (e.g., named Memory).

  2. **Seed the Data:** Store initial conversation history using message roles:

      - **Human Message:** The user's input (e.g., *"my name is Alex, I'm learning LangChain..."*).

      - **AI Message:** The model's previous response (e.g., *"nice to meet you, Alex..."*).

  3. **Inject Context:** Inject the stored messages directly into the `ChatPromptTemplate`.

  4. **Invoke:** When the chain is subsequently invoked with a follow-up question (e.g., *"what was my name again"*), the model reads the injected context and correctly answers *"Alex"*. Without this seeded memory, the model would not know the user's name.

---

### 🔗 Related

- **LangChain** → [2.2 Introduction to LangChain](02-introduction-to-langchain.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [2.2 Introduction to LangChain](02-introduction-to-langchain.md) | [⬆️ Module 2](README.md) | [2.4 Building Your First Agent with LangChain](04-building-your-first-agent-with-langchain.md) ➡️

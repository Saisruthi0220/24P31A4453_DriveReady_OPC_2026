# Day 3 – Your First AI Agent: Understanding Agents & LangChain

## Overview

Day 3 focuses on understanding AI agents and building a basic conversational AI assistant using LangChain and Large Language Models (LLMs).

This session introduces the fundamentals of AI agents, LangChain components, prompt templates, conversation history, and agent creation.

The practical implementation is based on a customer-support assistant for **Sweet Crumbs Home Bakery**, powered by the Groq API and GPT-OSS-120B model.

## Learning Objectives

- Understand what an AI agent is and how it works.
- Explore the fundamentals of LangChain.
- Integrate an LLM using the Groq API.
- Create structured prompts using LangChain.
- Build conversational chains using LCEL.
- Maintain conversation history and context.
- Create a basic AI agent using LangChain.
- Evaluate AI assistant responses using automated test cases.

## Topics Covered

### 1. Introduction to AI Agents

- Understanding AI agents.
- Difference between traditional LLM applications and AI agents.
- Understanding how agents process user requests.
- Exploring the basic components of an AI agent.

### 2. Introduction to LangChain

- Understanding the LangChain framework.
- Integrating language models with LangChain.
- Working with LangChain components.
- Understanding the role of prompts, models, and output parsers.

### 3. Groq API Integration

- Configuring the Groq API key.
- Managing API credentials using Google Colab Secrets.
- Connecting the GPT-OSS-120B model using `ChatGroq`.
- Generating responses using the integrated LLM.

### 4. Prompt Templates and Chains

- Creating prompts using `ChatPromptTemplate`.
- Using `MessagesPlaceholder` for conversation history.
- Implementing `StrOutputParser`.
- Building processing chains using LangChain Expression Language (LCEL).

### 5. Conversation History and Memory

- Maintaining conversation history.
- Managing user and assistant messages.
- Passing previous messages as context.
- Implementing conversational interactions using a Python function.

### 6. Automated Testing and Evaluation

- Creating test cases using CSV files.
- Evaluating assistant responses against expected keywords.
- Implementing automated test execution using Python.
- Calculating test pass percentages.
- Improving assistant responses through prompt refinement.

### 7. Creating a LangChain Agent

- Importing `create_agent` from LangChain.
- Initializing an agent with an LLM.
- Configuring the system prompt.
- Executing user queries through the agent.
- Displaying the final agent response.

## Practical Implementation

The session includes hands-on exercises such as:

- Installing LangChain and Groq dependencies.
- Connecting the Groq API to Google Colab.
- Initializing the GPT-OSS-120B language model.
- Creating a bakery customer-support system prompt.
- Building a conversational chain using LangChain.
- Implementing conversation history.
- Testing whether the assistant remembers customer information.
- Creating and executing 10 automated test cases.
- Developing a basic AI agent using `create_agent`.
- Evaluating and improving assistant responses.

## Technologies & Concepts

- Python
- Google Colab
- LangChain
- Groq API
- GPT-OSS-120B
- ChatPromptTemplate
- MessagesPlaceholder
- StrOutputParser
- LangChain Expression Language (LCEL)
- Conversation History
- CSV-based Testing
- AI Agents

## Testing and Evaluation

The Sweet Crumbs Home Bakery assistant was evaluated using 10 test cases covering product prices, eggless cake availability, order requirements, delivery enquiries, and price calculations.

| Implementation | Test Results |
|---|---:|
| Initial implementation | 6/10 |
| Improved implementation | 7/10 |

The improved version demonstrated progress in response accuracy. Further prompt refinement and testing are required to address the remaining failed test cases.

## Key Learning Outcomes

By completing Day 3, I gained an understanding of how to:

- Understand the fundamentals of AI agents.
- Integrate LLMs using the Groq API.
- Build conversational applications using LangChain.
- Design structured prompts and processing chains.
- Maintain conversation history and context.
- Create basic AI agents using LangChain.
- Perform automated testing and evaluate LLM responses.
- Improve AI assistant behavior through prompt engineering.

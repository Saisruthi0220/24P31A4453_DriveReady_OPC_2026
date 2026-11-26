# Day 4 – Building a Tool-Calling AI Agent with LangChain

## Overview

Day 4 focused on building a tool-calling AI agent using LangChain and Groq. The implementation involved creating an AI-powered bakery assistant capable of interacting with customers, calling Python tools, validating structured order data, handling follow-up messages and storing completed orders in Google Sheets.

The project demonstrates how an LLM can go beyond generating text and interact with external functions to perform practical tasks.

## Topics Covered

- Introduction to AI Agents
- LLM Integration using Groq
- LangChain Agent Creation
- Custom Tool Development
- Tool Calling and Tool Execution
- System Prompts and Agent Instructions
- Structured Output using Pydantic
- Data Validation
- Multi-turn Conversations
- Session-Based Conversation Memory
- Google Sheets Integration
- Order Processing and Confirmation
- Testing AI Agent Workflows

## Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core implementation |
| LangChain | Agent creation and tool orchestration |
| Groq | LLM inference |
| Pydantic | Structured data validation |
| Google Colab | Development environment |
| gspread | Google Sheets integration |
| Google Sheets | Order storage |

## 1. Environment Setup

Installed the required libraries to build and run the AI agent.

```bash
pip install langchain langchain-groq gspread pydantic
```

Configured the Groq API key and initialized the language model using `ChatGroq`.

## 2. LLM Integration using Groq

Integrated the Groq language model with LangChain to process customer queries and determine when tools should be used.

Configured the model with parameters such as temperature and retry handling.

## 3. Custom Tool Development

Created custom Python tools using LangChain's `@tool` decorator.

### get_price

Calculates the total price of a bakery item based on the item and quantity.

### is_open

Retrieves the bakery's opening hours for a specified day.

### log_order

Validates the customer order, calculates the total price and stores the order in Google Sheets.

## 4. Tool Calling

Implemented tool calling through the LangChain agent.

The agent determines when to invoke available tools based on the user's query, allowing it to retrieve prices, check opening hours and process completed orders.

## 5. System Prompt Engineering

Designed a system prompt to define the AI agent's:

- Role and identity
- Business information
- Menu and pricing rules
- Order requirements
- Tool usage instructions
- Customer interaction behaviour
- Response formatting

The system prompt guides the agent in collecting order details, handling missing information and providing customer confirmations.

## 6. Structured Output using Pydantic

Implemented a Pydantic model to define the structure of customer orders.

The order model includes:

- Customer name
- Item
- Quantity
- Pickup date
- Eggless preference

Used validation rules to restrict menu items and ensure valid quantities.

## 7. Multi-turn Conversation Handling

Implemented multi-turn conversation handling to allow customers to provide order details across multiple messages.

The agent can request missing information such as quantity, pickup date or item type before completing an order.

This allows the customer to interact naturally without providing every detail in a single message.

## 8. Session-Based Conversation Memory

Implemented separate conversation sessions using session identifiers.

Each customer conversation maintains its own history, allowing follow-up messages to be processed using previously provided information.

Separate sessions help prevent customer information from being mixed between conversations.

## 9. Google Sheets Integration

Integrated Google Sheets with the AI agent using `gspread` and Google authentication.

Completed orders are automatically stored in the spreadsheet with the following fields:

- Customer name
- Item
- Quantity
- Pickup date
- Eggless preference
- Total price

## 10. Order Processing Workflow

1. Customer initiates a conversation.
2. Agent collects required order information.
3. Agent identifies missing details.
4. Agent asks follow-up questions.
5. Agent calculates the order total using the pricing tool.
6. Order details are validated.
7. Completed order is stored in Google Sheets.
8. Agent provides order confirmation.

## 11. Testing and Validation

Tested the AI agent using seven customer scenarios.

The testing covered:

- Complete orders provided in a single message.
- Orders with missing pickup dates.
- Orders with missing quantities.
- Orders with missing item types.
- Follow-up messages within the same session.
- Separate conversation sessions for different customers.
- Order storage and price calculation.

The test scenarios were designed to evaluate the agent's ability to collect information gradually and process customer orders.

## 12. Learning Outcomes

Through this implementation, I explored:

- How AI agents work with LLMs.
- How LangChain orchestrates tool calling.
- How to create custom tools for an AI agent.
- How system prompts control agent behaviour.
- How to validate data using Pydantic.
- How to maintain session-based conversations.
- How to integrate AI agents with Google Sheets.
- How to build multi-step conversational workflows.


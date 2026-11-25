# Day 1 – AI Agents Training

## Overview
This project explores the fundamentals of building LLM-powered applications using Groq and LangChain. A simple AI assistant for a home bakery is developed using system prompting, LLM integration, and prompt safety testing.

## Objectives
- Integrate a Large Language Model (LLM) using Groq.
- Connect LangChain with Groq for conversational AI.
- Configure system prompts to define an AI assistant's behavior.
- Retrieve API credentials securely using Google Colab Secrets.
- Explore prompt safety testing using a Prompt Guard model.

## Implementation

### 1. LLM Integration
Installed and imported `langchain_groq` and initialized a Groq-powered language model using `ChatGroq`.

### 2. API Key Management
Accessed the Groq API key through Google Colab Secrets to configure the model securely.

### 3. System Prompt Configuration
Designed a system prompt for **Sweet Crumbs Home Bakery** to provide customer assistance based on predefined business information, response guidelines, and formatting constraints.

### 4. AI Query Function
Implemented an `ask()` function to pass user queries to the LLM along with the system instructions and retrieve generated responses.

### 5. Prompt Safety Exploration
Experimented with the `llama-prompt-guard-2-22m` model through the Groq API to explore prompt safety and instruction-related security testing.

## Technologies Used
- Python
- Google Colab
- LangChain
- Groq API
- GPT-OSS 120B
- Llama Prompt Guard

## Files
- `Day1.ipynb` – Notebook containing the implementation, model configuration, system prompting, AI query handling, and prompt safety testing.

## Learning Outcomes
- Learned how to connect an LLM to a Python application.
- Explored system prompts to control an AI assistant's behavior.
- Practiced API key management using Google Colab Secrets.
- Implemented a basic LLM-powered customer support assistant.
- Explored prompt safety and security testing concepts.

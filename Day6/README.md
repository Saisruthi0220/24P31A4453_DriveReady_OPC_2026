Day 6 – Building a Tool-Using Chatbot with LangGraph
Overview
Day 6 marks the move from a single LangChain agent to a graph-based workflow using LangGraph — the framework that will power multi-agent systems from here onward. This session introduces StateGraph, the agent loop as an explicit graph, tool nodes with prebuilt helpers, conditional edges, and building a chatbot that can look up information from Wikipedia and Arxiv.

The practical implementation builds a chatbot with tools powered by the Groq API and the GPT-OSS-120B model, using Wikipedia and Arxiv search tools to answer questions beyond the model's training data.

Learning Objectives
Understand what LangGraph is and why graph-based agents matter.

Explore StateGraph, State, and typed message lists.

Build a chatbot node that calls an LLM with bound tools.

Use prebuilt ToolNode and tools_condition from LangGraph.

Wire a tool-using loop with conditional edges.

Integrate community tools like Wikipedia and Arxiv.

Visualize and inspect the agent's flow.

Stream an agent's execution to see each step.

Topics Covered
1. Introduction to LangGraph
What LangGraph is (a graph-based framework for stateful agents).

Difference between LangChain agents (opaque) and LangGraph (explicit, inspectable).

Nodes, edges, states, and the loop that powers an agent.

Why a graph is the natural model for multi-agent systems.

2. Install and Patch Dependencies
Installing langgraph, langsmith, langchain, langchain_groq, langchain_community.

Installing wikipedia and arxiv<2.0.0.

Patching the cgi module for Python 3.13 compatibility (arXiv's legacy dependency).

Handling pip dependency conflicts gracefully.

3. Community Tools: Wikipedia and Arxiv
Loading WikipediaAPIWrapper and ArxivAPIWrapper.

Wrapping them in WikipediaQueryRun and ArxivQueryRun.

Limiting results with top_k_results and doc_content_chars_max.

Testing a tool directly with .invoke("...").

Composing multiple tools into one list.

4. State Definition
Using TypedDict to define the agent's state.

The messages key with Annotated[list, add_messages] — this auto-appends messages.

Why message accumulation is the core of agent memory.

5. Building the Graph
Creating a StateGraph(State).

Adding nodes: chatbot and tools.

Adding edges: START → chatbot, tools → chatbot.

Adding conditional edges with tools_condition (routes to tools if the LLM called one, or to END if it's done).

Compiling with graph.compile().

6. LLM and Tool Binding
Initializing ChatGroq with model_name="openai/gpt-oss-120b".

Binding tools with llm.bind_tools(tools=tools).

Writing a chatbot node that returns {"messages": [llm_with_tools.invoke(state["messages"])]}.

Understanding how a tool call shows up as an AIMessage with tool_calls.

7. Visualizing the Graph
Using graph.get_graph().draw_mermaid_png().

Displaying it with IPython.display.Image.

The standard agent shape: chatbot ↔ tools.

8. Streaming the Execution
Using graph.stream({"messages": [...]}, stream_mode="values").

Printing each step with .pretty_print().

Seeing the flow: human → AI (tool call) → tool result → AI (final answer).

Watching the model answer questions that rely on its knowledge (RLHF) vs. questions that need the tools.

Practical Implementation
The session includes hands-on exercises such as:

Installing and patching dependencies for Colab + Python 3.13.

Loading Wikipedia and Arxiv tools with sensible limits.

Testing wiki_tool.invoke("who is virat kohli") directly.

Defining State with Annotated[list, add_messages].

Building the StateGraph with chatbot and tools nodes.

Wiring conditional edges with tools_condition.

Compiling the graph and drawing the diagram.

Streaming a plain question ("Hi there, my name is Rajesh").

Streaming a tool-using question ("what is RLHF").

Reading the traces step by step.

Technologies & Concepts
Python

Google Colab (T4 GPU)

LangGraph (StateGraph, ToolNode, tools_condition, add_messages)

LangChain (bind_tools, message types)

LangChain Community tools (ArxivQueryRun, WikipediaQueryRun)

Groq API

GPT-OSS-120B

Streamed execution (graph.stream)

Mermaid graph visualization

Python 3.13 compatibility patching (cgi shim for legacy feedparser)

Testing and Evaluation
The chatbot was tested with both general-knowledge and tool-requiring questions to verify the graph routes correctly.

Test Scenario	Expected Behaviour	Result
"Hi there, my name is Rajesh"	Polite greeting, no tool call	✅ Passed
"What is RLHF?"	Long explanation from the model's knowledge	✅ Passed
"Who is Virat Kohli?" (via wiki_tool)	Wikipedia summary returned	✅ Passed
Tool call shown as AIMessage with tool_calls	Graph routes chatbot → tools → chatbot	✅ Passed
Final answer in the last message	.pretty_print() shows full trace	✅ Passed
The graph correctly handled the agent loop: the model decides when it needs a tool, LangGraph's tools_condition routes to the tool node, the tool result is appended to messages, and the loop returns to the chatbot until the model produces a plain text answer.

Key Learning Outcomes
By completing Day 6, I gained an understanding of how to:

Explain what LangGraph is and how it differs from LangChain agents.

Define a typed State for a graph-based agent.

Build a StateGraph with chatbot and tools nodes.

Use prebuilt ToolNode and tools_condition to handle the agent loop.

Integrate community tools (Wikipedia, Arxiv) into a chatbot.

Bind tools to an LLM with bind_tools.

Visualize the graph with draw_mermaid_png().

Stream an agent's execution with graph.stream(..., stream_mode="values").

Read agent traces with pretty_print() to debug routing.

Handle Python 3.13 packaging quirks in Colab.

---
title: Agents and automation
layout: default
parent: Roadmaps
grand_parent: Practice
nav_order: 8
---

# Roadmap: agents and automation

**Goal:** build a small AI agent that takes a goal, uses tools, and completes a task — first with a provider API, then fully local.

An **agent** is an LLM loop that can call tools (search, code, your RAG index, HTTP calls) to accomplish a task. This roadmap builds one with LangChain, then a multi-agent setup with CrewAI, both pointing at a local model. Frameworks are covered on the [agent-frameworks](/agent-frameworks/) pages.

## Step 1 — Decide the backend

| | Local (Ollama / vLLM) | Provider (OpenAI, Anthropic) |
|---|---|---|
| Privacy | Data stays local | Data leaves your machine |
| Cost | Free (your compute) | Per token |
| Reliability of tool calling | Good with modern models | Excellent |
| Ease | Slightly harder setup | Simplest |

Start with a provider to learn the concepts, then switch to local for privacy.

## Step 2 — Install

```bash
pip install langchain langchain-openai
pip install crewai
```

For local models also: `pip install langchain-ollama`.

## Step 3 — A simple agent with LangChain (local first)

```python
from langchain_ollama import ChatOllama
from langchain.agents import create_react_agent, AgentExecutor
from langchain.tools import tool

llm = ChatOllama(model="llama3.2")   # from the local LLM roadmap

@tool
def add(a: int, b: int) -> int:
    """Add two numbers and return the result."""
    return a + b

tools = [add]
prompt = ...  # a ReAct prompt template

agent = create_react_agent(llm, tools, prompt=prompt)
executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
print(executor.invoke({"input": "What is 20 + 22?"}))
```

The agent reasons, calls the `add` tool, and returns the result.

## Step 4 — The same with a provider

Swap the model to use a cloud API instead:

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o-mini")
```

Everything else stays the same.

## Step 5 — A multi-agent crew with CrewAI

CrewAI orchestrates role-based agents collaborating on tasks. A minimal setup:

```python
from crewai import Agent, Task, Crew, LLM

llm = LLM(model="ollama/llama3.2")    # local; or "gpt-4o-mini" for provider

researcher = Agent(role="researcher", goal="gather facts",
                   backstory="careful analyst", llm=llm)
writer = Agent(role="writer", goal="summarize", llm=llm)

research_task = Task(description="Find key facts about RLHF", agent=researcher)
write_task = Task(description="Summarize the facts in 3 bullets", agent=writer)

crew = Crew(agents=[researcher, writer], tasks=[research_task, write_task])
result = crew.kickoff()
print(result)
```

## Step 6 — Give the agent memory and tools

Real agents need state. Add tools (web search, a calculator) and memory / vector store so it can recall facts:

- **Tools**: LangChain's built-in toolkits (search, file operations, HTTP).
- **Memory**: conversation history passed back into the prompt.
- **RAG**: connect the [RAG assistant](roadmap-rag.html) index as a retrieval tool.

## Safety notes

- **Agents can do real things** (run commands, call APIs). Sandbox them; least privilege.
- **Prompt injection**: untrusted tool output can steer the agent. Sanitize inputs.
- **Hallucinated steps**: verify agent actions before relying on them.

## What's next

- Add a local coding model for agentic coding: [Coding roadmap](roadmap-coding.html).
- Scale agents on a real backend: [Production roadmap](roadmap-production.html).

## Theory needed (read separately)

- [Agent frameworks](/agent-frameworks/)
- [RLHF and alignment](/theory/training/dpo.html)
- [Jailbreaks and prompt injection](/theory/safety/jailbreak.html)
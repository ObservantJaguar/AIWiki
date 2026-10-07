---
title: LangChain
layout: default
parent: Agent frameworks
grand_parent: Tools
---

# LangChain

LangChain is the most widely used framework for building LLM applications. It provides modular building blocks — model wrappers, prompt templates, retrievers, tools and agent runtimes — for assembling RAG and agent workflows.

## Overview

- **Language**: Python and TypeScript/JavaScript
- **License**: MIT
- **Developer**: LangChain Inc. (open source)
- **Status**: mature, extremely large ecosystem and community

## Key features

- **Modular components**: models, prompts, output parsers, memory, chains.
- **Separate packages**: LangChain core, community integrations, LangGraph (graph-based), LangSmith (observability).
- **RAG helpers**: document loaders, splitters, retrievers, vector store adapters.
- **Agent runtime**: LangGraph supports stateful, controllable agent execution.
- **Broad integrations**: OpenAI, ANthropic, local models (Ollama, llama.cpp), vector stores.
- **Self-hostable**: works with fully local model servers and vector DBs.

## Best for

- Rapidly assembling RAG and agent applications with many integrations.
- Teams wanting a wide, maintained integration catalog.
- Graph-based, controllable agent flows via LangGraph.

## Trade-offs / notes

- The abstraction layer adds learning curve and occasional overfitting.
- Some teams prefer a more minimal library (e.g. LlamaIndex for data, or raw SDKs) to keep control.

## Resources

- [LangChain website](https://www.langchain.com/)
- [LangChain GitHub](https://github.com/langchain-ai/langchain)
- [LangChain docs](https://python.langchain.com/)
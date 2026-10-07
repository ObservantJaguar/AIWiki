---
title: AutoGen
layout: default
parent: Agent frameworks
grand_parent: Tools
---

# AutoGen

AutoGen is a multi-agent conversation framework from Microsoft Research that lets multiple LLM agents (and humans and tools) converse to solve tasks. Its "conversable agent" model is flexible for building agentic applications.

## Overview

- **Language**: Python
- **License**: MIT
- **Developer**: Microsoft Research (open source)
- **Status**: active; Microsoft also offers a commercial AutoGen platform

## Key features

- **Conversable agents**: agents that exchange messages to iterate toward a solution.
- **Multi-agent conversations**: role-based agents (e.g. assistant + user proxy + critic).
- **Tool calling and code execution**: agents can run code in controlled sandboxes.
- **Group chat**: orchestrate several agents around a topic.
- **Flexible integration**: local models, vLLM, Ollama, OpenAI-compatible endpoints.
- **Observability**: tracing and state management for debugging agent runs.

## Best for

- Multi-agent conversations and collaborative problem-solving.
- Prototyping agent autonomy with fine-grained control.
- Research into agent behavior and multi-agent dynamics.

## Resources

- [AutoGen GitHub](https://github.com/microsoft/autogen)
- [AutoGen docs](https://microsoft.github.io/autogen/)
- [AutoGen paper](https://arxiv.org/abs/2308.08155)
---
title: Roadmaps
layout: default
parent: Practice
nav_order: 2
has_children: true
---

# Roadmaps: how to use AI, step by step

Practical, goal-oriented roadmaps that take you from zero to a working result. Each roadmap is a **step-by-step path with terminal commands** you can copy and run, plus links to the theory and tool pages that explain what you did. Theory and practice are kept separate.

## When to self-host vs use a provider

The single most useful decision is where to run the AI. This table is the short version; each roadmap explains it in context.

| Factor | Self-host (run on your hardware) | Provider (API / subscription) |
|---|---|---|
| Best for | Privacy, control, no per-token cost at scale, offline | Latest/best models, zero setup, no GPU needed |
| Hardware needs | GPU recommended (or patience on CPU) | None — runs on their servers |
| Cost model | Up-front hardware + electricity | Per-token or monthly subscription |
| Data privacy | Data stays on your machine | Data leaves your machine (check their policy) |
| Setup effort | Medium to high | Low (sign up, paste API key) |
| Examples | Ollama, vLLM, Stable Diffusion, Whisper, Qdrant | GPT-4, Claude, Gemini, Midjourney, DALL-E |

## The roadmaps

### Beginner — use AI, don't build it

- **[Start using an LLM chat](roadmap-chat.html)** — pick a provider or chat app, write good prompts, get useful answers today. No terminal required.

### Self-host — run models on your hardware

- **[Run an LLM locally](roadmap-local-llm.html)** — Ollama on your machine: install, pull a model, chat from terminal and from an app.
- **[Serve a model in production](roadmap-production.html)** — vLLM/TGI on a GPU server behind an OpenAI-compatible API for real workloads.
- **[Build a RAG assistant on your data](roadmap-rag.html)** — give the model access to your documents with embeddings + a vector database.
- **[Generate images](roadmap-images.html)** — ComfyUI with Stable Diffusion or Flux on your own GPU.
- **[Transcribe audio and add voice](roadmap-audio.html)** — Whisper for speech-to-text, Bark for speech synthesis.

### Beyond chat — coding and agents

- **[A coding assistant on your machine](roadmap-coding.html)** — Continue + a local model in VS Code, and when Copilot/Cursor make more sense.
- **[Agents and automation](roadmap-agents.html)** — build a small autonomous agent with LangChain or CrewAI, first with a provider, then fully local.

## Keep in mind

- The AI landscape changes fast. Sizes, licenses and APIs shift; verify details on official pages before committing.
- Start with the smallest useful step, get a win, then scale up.
- Theory lives in the [Theory section](/theory/); tool details in the [Tools section](/tools/); generic how-tos in the [guides](/guides/).
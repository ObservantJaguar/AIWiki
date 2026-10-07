---
title: Run an LLM locally with Ollama
layout: default
parent: Guides
grand_parent: Practice
nav_order: 1
---

# Run an LLM locally with Ollama

This guide shows how to download and run an open language model on your own machine with Ollama — the fastest way to get a working local model.

## Prerequisites

- A machine with at least 8 GB RAM (ideally more for larger models).
- Optional: an NVIDIA GPU or Apple Silicon for acceleration.
- Ollama installed from [ollama.com](https://ollama.com/) (macOS, Linux, Windows).

## Step 1 — Install Ollama

Download and run the installer for your platform. On Linux:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Verify it works:

```bash
ollama --version
```

## Step 2 — Pull a model

Pick a model from the library. Start small to confirm everything works:

```bash
ollama pull llama3.2
```

This downloads the quantized weights — several gigabytes, depending on the model size.

## Step 3 — Run and chat

Start an interactive session:

```bash
ollama run llama3.2
```

Type a prompt and the model responds. Use `/bye` to exit. This is the same model interface you would use with a chat front end.

## Step 4 — Use the OpenAI-compatible API

Ollama runs a local server on `127.0.0.1:11434`. Test it with curl:

```bash
curl http://localhost:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model": "llama3.2", "messages": [{"role": "user", "content": "Hello!"}]}'
```

Any OpenAI SDK client can point its `base_url` at this endpoint.

## Step 5 — Choose the right size

If the model feels slow or runs out of memory:

```bash
ollama run llama3.2:1b    # smaller, faster variant
```

List installed models and remove unneeded ones:

```bash
ollama list
ollama rm llama3.2
```

## What's next

- Point a chat UI or an agent framework at the local API.
- See [the vLLM guide](guide-vllm.html) for high-throughput GPU serving.
- See [the RAG guide](guide-rag.html) to ground the model in your documents.

## References

- [Ollama library](https://ollama.com/library)
- [Ollama API docs](https://github.com/ollama/ollama/blob/main/docs/openai.md)
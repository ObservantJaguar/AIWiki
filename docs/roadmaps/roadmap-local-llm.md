---
title: Run an LLM locally
layout: default
parent: Roadmaps
grand_parent: Practice
nav_order: 2
---

# Roadmap: run an LLM locally

**Goal:** get a working, private, offline AI chat running on your own machine with Ollama — no cloud, no per-token cost.

This is the flagship self-host step. For deeper explanation, see the [details page for Ollama](/llm-servers/ollama.html) and the [generic Ollama guide](/guides/guide-ollama.html).

## Step 1 — Check your hardware

You can run models without a GPU, but a GPU (or Apple Silicon) makes everything faster.

- **8 GB RAM**: usable with small models (1B-3B).
- **16 GB RAM**: comfortable with 7B models via quantization.
- **20+ GB RAM or a GPU with 8+ GB VRAM**: smooth 7B-13B.

Don't overthink it — Ollama auto-detects hardware and offloads what it can.

## Step 2 — Install Ollama

**Linux:**

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

**macOS / Windows:** download the installer from [ollama.com](https://ollama.com/) and run it.

Verify:

```bash
ollama --version
```

## Step 3 — Pull a model

Start with a small, reliable one to confirm everything works:

```bash
ollama pull llama3.2
```

This downloads the quantized weights (a few GB). List what you have:

```bash
ollama list
```

## Step 4 — Chat from the terminal

```bash
ollama run llama3.2
```

Type prompts and press Enter. Type `/bye` to exit. This is a working private chat.

## Step 5 — Chat from a nicer interface

Ollama runs a local server on `http://127.0.0.1:11434`. You can:

- Use **Open WebUI** (a local ChatGPT-like web app) as a container:

```bash
docker run -d -p 3000:8080 \
  -v open-webui:/app/backend/data \
  -e OLLAMA_BASE_URL=http://host.docker.internal:11434 \
  --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

Then open `http://localhost:3000`.

- Or point any OpenAI-compatible app at the local server:

```bash
curl http://127.0.0.1:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"llama3.2","messages":[{"role":"user","content":"Hi!"}]}'
```

## Step 6 — Pick the right model size

If it's slow or out of memory, use a smaller variant:

```bash
ollama run llama3.2:1b       # smallest, fastest
ollama run llama3.2:3b       # middle ground
```

For heavier tasks, try Mistral or Qwen families — `ollama run mistral` or `ollama run qwen2.5:7b`.

## Troubleshooting

- **Out of memory**: use a smaller model or fewer layers (`OLLAMA_NUM_GPU`).
- **Slow**: it's normal on CPU; use a 1B-3B model for responsiveness.
- **No response**: ensure the server is running (`ollama serve`).

## What's next

When one machine isn't enough, or you need higher throughput for an app, serve a model on a GPU server with the [production roadmap](roadmap-production.html).

## Theory needed (read separately)

- [Inference fundamentals](/theory/inference/inference-basics.html)
- [Quantization](/theory/inference/quantization.html)
- [The KV-cache](/theory/inference/kv-cache.html)
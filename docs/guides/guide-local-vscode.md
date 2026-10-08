---
title: Run a local model in VS Code
layout: default
parent: Guides
grand_parent: Practice
nav_order: 3
---

# Guide: run a local model and use it in VS Code

**Goal:** deploy a language model on your own machine and connect it to VS Code as an AI coding assistant, so completions and chat work fully offline with no subscription.

Two engines can do this: **Ollama** (command line, lightweight) and **LM Studio** (graphical app). Both download a model and expose a local OpenAI-compatible server that the Continue extension talks to. This guide covers both, but the single most important thing to get right is **hardware** — read that section first.

## Hardware requirements — read this first

The model must fit in RAM (or VRAM if you have a GPU). The quick rule of thumb:

```text
Model size in GB ~= parameters (billions) x 0.55 (for Q4 quantization)
Full precision (FP16) models need roughly double that.
```

| Your RAM/VRAM | Models that fit (Q4) | Use case |
|---|---|---|
| 8-16 GB | 1B - 7B | Small chats, light autocomplete |
| 32 GB | 7B - 14B | Comfortable coding assistants |
| 64 GB | 14B - 32B | Strong coding + general models |
| 128 GB+ | 32B - 70B | Best local quality, big models |
| GPU 8-12 GB VRAM | 7B-8B (offload to GPU) | Fast autocomplete, short context |

### How to estimate your real model

A concrete way to check a model's RAM use before you commit: look at the model card or the file size, then add about 25% for the context window. If your machine has X GB of RAM, prefer the largest model that fits comfortably with room for the context cache to grow.

### Xeon + 32 GB: why it felt slow

A CPU-only server with 32 GB RAM can run a 7B-14B model fine, but a few things make it feel unusable:

- **Too big a model**: pulling a 30B+ model on 32 GB forces it to swap/offload, which is very slow.
- **FP16 weights**: using an unquantized model doubles memory use.
- **Context mushrooming**: every chat token adds to the cache; long chats slow down.

On a CPU-only 32 GB box, use **7B-13B in Q4** (e.g. `qwen2.5-coder:7b`). That gives usable autocomplete, not instant, but workable. If you want bigger models, 64 GB is the practical sweet spot; 128 GB only matters if you specifically need 32B-70B models.

## Option A — Ollama (command line)

### Step 1 — Install Ollama

```bash
curl -fsSL https://ollama.com/install.sh | sh   # Linux
```

Download the installer for macOS/Windows from [ollama.com](https://ollama.com/).

### Step 2 — Pull a coding model

```bash
ollama pull qwen2.5-coder:7b
```

On weaker hardware, try the 3B version:

```bash
ollama pull qwen2.5-coder:3b
```

Confirm it works in the terminal:

```bash
ollama run qwen2.5-coder:7b
```

Exit with `/bye`. Keep the server for VS Code:

```bash
ollama serve
```

### Step 3 — Connect VS Code

1. Install the **Continue** extension in VS Code.
2. Open Continue settings (gear icon) → **Models** → add a provider.
3. Choose **Ollama**, server `http://localhost:11434`, model `qwen2.5-coder:7b`. Continue usually auto-detects it.

### Step 4 — Check the API works

Test the loop from the terminal to confirm the server is reachable:

```bash
curl http://localhost:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"qwen2.5-coder:7b","messages":[{"role":"user","content":"Say hi"}]}'
```

## Option B — LM Studio (graphical)

LM Studio is the same idea with a GUI: you browse models, download them with a click, and run a local server. It is easier for first-time users than the terminal.

### Step 1 — Install LM Studio

Download from [lmstudio.ai](https://lmstudio.ai/). Install like any desktop app.

> Note: older guides told you to use a specific "dev build" for VS Code support. Current LM Studio includes the local OpenAI-compatible server for free, so the setup is simpler now — no need for old builds.

### Step 2 — Download a model

- In LM Studio, search for a coding model (e.g. **Qwen2.5 Coder 7B Q4_K_M**).
- Click **Download** on the quantized GGUF version that matches your RAM.
- Pick `Q4_K_M` or `Q5_K_M` for the best quality/size balance; smaller (Q4) if RAM is tight.

### Step 3 — Start the local server

1. Go to the **Local Server** tab (top menu).
2. Load the downloaded model.
3. Choose the GPU layers (more layers offloaded to GPU = faster; 0 = CPU only).
4. Start the server. It listens on `http://localhost:1234` by default.

Note the exact server URL and port — you'll point Continue at it.

### Step 4 — Connect VS Code

1. Install the **Continue** extension in VS Code.
2. Open Continue settings → **Models** → **Add**.
3. Choose **OpenAI** provider, set base URL to `http://localhost:1234/v1`, API key empty, model name matching the one loaded in LM Studio.

### Step 5 — Use it

- Type code; Continue suggests completions (Tab to accept).
- Select code and press **Ctrl+L** to chat with the model about it.
- Use `/edit` to apply changes.

## Choosing between Ollama and LM Studio

| | Ollama | LM Studio |
|---|---|---|
| Interface | Command line | Graphical |
| Ease for beginners | Medium | High |
| VS Code connection | Continue + auto-detect | Continue + manual OpenAI URL |
| Model management | `ollama pull` | Click-to-download |
| Headless server | Yes (great for servers) | GUI-first |

Use **Ollama** on a server (headless) or if you like the terminal. Use **LM Studio** on your desktop if you prefer clicking.

## Troubleshooting

- **Model won't load / slow**: the model is too big for your RAM. Use a smaller quant (Q4) or a smaller parameter count.
- **VS Code says "connection refused"**: check the server is running and the URL/port in Continue matches the engine.
- **Very slow responses**: not enough VRAM → offload fewer layers, or use CPU-only with a smaller model.
- **Out of memory**: reduce `max tokens` and context length; restart the engine.

## What's next

- Level up to a shared or bigger setup: [Production roadmap](/roadmaps/roadmap-production.html).
- Understand the mechanics: [Inference fundamentals](/theory/inference/inference-basics.html) and [Quantization](/theory/inference/quantization.html).

## References

- [Ollama](https://ollama.com/) and [Ollama docs](https://github.com/ollama/ollama)
- [LM Studio](https://lmstudio.ai/)
- [Continue extension](https://github.com/continuedev/continue)
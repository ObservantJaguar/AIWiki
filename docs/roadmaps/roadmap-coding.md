---
title: A coding assistant on your machine
layout: default
parent: Roadmaps
grand_parent: Practice
nav_order: 7
---

# Roadmap: a coding assistant on your machine

**Goal:** get AI code completion and chat working inside your editor, using a local model — then decide when a cloud coder (Copilot/Cursor) is the better tool.

This is fully self-hosted: Continue in VS Code (or JetBrains) talking to a local Ollama model. Privacy-aware, no subscription, works offline.

## Decision: local coder vs cloud coder

| | Local (Continue + Ollama) | Cloud (Copilot, Cursor) |
|---|---|---|
| Privacy | Your code stays local | Code sent to a provider |
| Cost | Free (your compute) | Subscription |
| Best model quality | Good, limited by your GPU | Excellent (GPT-4-class) |
| Works offline | Yes | No |

Start local to keep your code private and learn the mechanics; switch to cloud for the strongest completions.

## Step 1 — Install VS Code and Continue

Install [VS Code](https://code.visualstudio.com/), then install the **Continue** extension from the marketplace.

Alternatively, use JetBrains IDEs with the Continue plugin.

## Step 2 — Install a local model with Ollama

From the [local LLM roadmap](roadmap-local-llm.html):

```bash
ollama pull qwen2.5-coder:7b   # a strong open coding model
```

Keep the server running (`ollama serve`).

## Step 3 — Configure Continue to use Ollama

Open Continue settings and add an Ollama model provider pointing at `http://localhost:11434`, model `qwen2.5-coder:7b`. Continue auto-detects Ollama on the same machine, so this is often a one-click selection.

## Step 4 — Use it

- **Autocomplete**: start typing; Continue suggests completions (Tab to accept).
- **Chat**: highlight code and press Cmd/Ctrl+L to ask questions or request edits.
- **Commands**: use `/edit` to apply a change, `/generate` for new code.

## Step 5 — Speed it up

Coding models work best on a GPU. On CPU/weak hardware:

```bash
ollama pull qwen2.5-coder:3b
```

Then switch the Continue model to `qwen2.5-coder:3b` for snappier responses.

## Step 6 — Consider a cloud coder

If your hardware cannot run a model well, or you want the strongest completions, try GitHub Copilot or Cursor. You lose privacy and gain quality — a trade-off worth making consciously.

## Best practices

- Use a *coder* model (qwen2.5-coder, deepseek-coder-v2, codestral) — better than general models.
- Give the model file context: select the relevant code before asking.
- Review suggestions; they are starting points, not final code.
- For serious privacy about source code, local is the only option that truly keeps it.

## What's next

- Build agents that can run your code: [Agents roadmap](roadmap-agents.html).
- Serve a bigger model on a GPU: [Production roadmap](roadmap-production.html).

## Theory needed (read separately)

- [Coding benchmarks](/theory/benchmarks/benchmark-suites.html)
- [Inference fundamentals](/theory/inference/inference-basics.html)
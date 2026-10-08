---
title: Serve a model in production
layout: default
parent: Roadmaps
grand_parent: Practice
nav_order: 3
---

# Roadmap: serve a model in production

**Goal:** deploy a language model on a GPU server behind an OpenAI-compatible API that real applications can call at scale.

This is the step after the [local LLM roadmap](roadmap-local-llm.html). Use it when one local install isn't enough: multiple users, higher throughput, or an app backend. See the [vLLM page](/llm-servers/vllm.html) and the [vLLM guide](/guides/guide-vllm.html) for detail.

## Step 1 — Get hardware

You need a server with a CUDA GPU:

- **7B model**: 16 GB VRAM (or 8 GB with quantization).
- **70B model**: 80 GB VRAM, or 2x A100/H100, or quantization with a single large GPU.
- For testing only, a desktop GPU works; for production use, a cloud GPU (AWS, RunPod, Vast, etc.).

## Step 2 — Install vLLM

On the server:

```bash
pip install vllm
```

Or use the official Docker image (avoids build issues, recommended):

```bash
docker pull vllm/vllm-openai:latest
```

## Step 3 — Serve a model

Choose an open model from Hugging Face (e.g. Llama 3.2 or Qwen 2.5). Serve it:

```bash
vllm serve meta-llama/Llama-3.2-7B-Instruct \
  --served-model-name my-model \
  --max-model-len 8192
```

With Docker, mounting the cache and exposing port 8000:

```bash
docker run --runtime nvidia --gpus all \
  -v ~/.cache/huggingface:/root/.cache/huggingface \
  -p 8000:8000 \
  vllm/vllm-openai:latest \
  --model meta-llama/Llama-3.2-7B-Instruct --max-model-len 8192
```

If the model is gated, log in first: `huggingface-cli login`.

## Step 4 — Query it

The API is OpenAI-compatible on port 8000:

```bash
curl http://localhost:8000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"my-model","messages":[{"role":"user","content":"Hello!"}]}'
```

And from Python:

```python
from openai import OpenAI

client = OpenAI(base_url="http://localhost:8000/v1", api_key="EMPTY")
resp = client.chat.completions.create(
    model="my-model",
    messages=[{"role": "user", "content": "Hello!"}],
)
print(resp.choices[0].message.content)
```

## Step 5 — Fit more into memory with quantization

To serve a larger model on limited VRAM, enable quantization:

```bash
vllm serve meta-llama/Llama-3.2-7B-Instruct --quantization awq
```

## Step 6 — Scale out (when you need it)

- **Continuous batching** is automatic in vLLM — it already uses the GPU efficiently under load.
- **Multiple GPUs / nodes**: vLLM supports tensor and pipeline parallelism via flags; or use a managed service.
- **Load balancing**: put a reverse proxy (nginx) in front of several instances.

## Decision: vLLM vs TGI vs Ollama

| Engine | Best for |
|---|---|
| **Ollama** | Single machine, simplicity, personal/gui use |
| **vLLM** | Maximum throughput, production GPU serving, OpenAI API |
| **TGI** | Hugging Face ecosystem, model hub integration |
| **llama-server** | Lightweight CPU or embedded serving |

## Security note

The OpenAI-compatible endpoint has **no authentication by default**. Expose it behind a reverse proxy with auth or a firewall before putting it on the internet.

## What's next

Give the model access to your own documents with the [RAG roadmap](roadmap-rag.html).

## Theory needed (read separately)

- [Batching and serving](/theory/inference/batching.html)
- [The KV-cache](/theory/inference/kv-cache.html)
- [Quantization](/theory/inference/quantization.html)
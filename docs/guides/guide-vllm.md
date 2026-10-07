---
title: Serve a model with vLLM
layout: default
parent: Guides
grand_parent: Practice
nav_order: 2
---

# Serve a model with vLLM (OpenAI-compatible API)

This guide shows how to deploy a language model on a GPU with vLLM and expose an OpenAI-compatible API — the production path used for high-throughput serving.

## Prerequisites

- A machine with a CUDA GPU (16+ GB VRAM recommended for 7B-class models).
- NVIDIA drivers and CUDA toolkit installed.
- Python 3.10+.

## Step 1 — Install vLLM

Install from PyPI:

```bash
pip install vllm
```

Or run the official Docker image, which avoids build issues:

```bash
docker pull vllm/vllm-openai:latest
```

## Step 2 — Serve a model

Serve a Hugging Face model (e.g. Llama 3.2 7B) using the OpenAI-compatible server:

```bash
vllm serve meta-llama/Llama-3.2-7B-Instruct \
  --served-model-name my-model \
  --max-model-len 8192
```

With Docker:

```bash
docker run --runtime nvidia --gpus all \
  -v ~/.cache/huggingface:/root/.cache/huggingface \
  -p 8000:8000 \
  vllm/vllm-openai:latest \
  --model meta-llama/Llama-3.2-7B-Instruct --max-model-len 8192
```

For an open token-gated model you may need to log in with `huggingface-cli login` first.

## Step 3 — Query the API

Test the default endpoint on port 8000:

```bash
curl http://localhost:8000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model": "my-model", "messages": [{"role": "user", "content": "Hello!"}]}'
```

## Step 4 — Use OpenAI SDK clients

Point any OpenAI SDK at the local server:

```python
from openai import OpenAI

client = OpenAI(base_url="http://localhost:8000/v1", api_key="EMPTY")

resp = client.chat.completions.create(
    model="my-model",
    messages=[{"role": "user", "content": "Hello!"}],
)
print(resp.choices[0].message.content)
```

## Step 5 — Reduce memory with quantization

Add a quantization flag to fit more in VRAM:

```bash
vllm serve meta-llama/Llama-3.2-7B-Instruct --quantization awq
```

## Troubleshooting

- **Out of memory**: lower `--max-model-len` or enable quantization.
- **Model not found / gated**: authenticate with Hugging Face.
- **Wrong GPU**: set `CUDA_VISIBLE_DEVICES=0` to select a device.

## What's next

- Read the [RAG guide](guide-rag.html) to pair the server with retrieval.
- Check the [vLLM page](../llm-servers/vllm.html) for advanced options.

## References

- [vLLM serving docs](https://docs.vllm.ai/en/latest/serving/openai_compatible_server.html)
- [vLLM Docker examples](https://docs.vllm.ai/en/latest/serving/deploying_with_docker.html)
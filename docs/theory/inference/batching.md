---
title: Batching and serving
layout: default
parent: Inference
grand_parent: Theory
---

# Batching and serving

Serving an LLM means handling many concurrent requests efficiently. The key is **batching** — processing multiple generation streams in parallel on the GPU — especially **continuous batching**, which is how modern inference servers reach high throughput.

## Why batch on a GPU

A single decode step is memory-bandwidth-bound: the GPU mostly reads model weights and KV-cache while doing relatively little compute. By running several requests on the same model in one pass, the fixed cost of loading the weights is amortized across all of them, boosting tokens-per-second.

```text
fp16 decode, one request:  GPU reads 14 GB of weights, produces ~1 token
batch of 32:               GPU reads the same 14 GB once, produces 32 tokens
```

## Static batching

The naive approach: wait for N requests to fill a fixed-size batch, run them together until all finish. Simple, but wastes GPU when most requests finish early and idle slots remain.

## Continuous batching (in-flight batching)

Modern servers (vLLM, TGI, TensorRT-LLM) add and remove requests continuously: finishing streams are evicted immediately and new ones join, so the GPU is kept busy at all times.

- **Scheduling**: requests are iterated on, not run to completion together.
- **Paged attention**: gives each request its own KV-cache pages, making dynamic scheduling cheap.
- **Result**: substantially higher throughput and lower average latency under load.

## Key serving concepts

- **Static vs continuous batching** — the defining difference in throughput.
- **Prefill/decode scheduling**: separate the two phases or overlap them.
- **Speculative decoding**: a small draft model proposes tokens, the big model verifies several at once.

## Key features

- Batching raises throughput by amortizing weight loads across requests.
- Continuous batching + paged attention is the modern serving standard.
- Engine choice (vLLM, TGI, TensorRT-LLM) largely determines achievable throughput.

## Resources

- [LLM Inference Performance Engineering (blog)](https://www.databricks.com/blog/llm-inference-performance-engineering-best-practices)
- [Continuous batching in vLLM](https://docs.vllm.ai/)
- [Serving Llama 2 with TensorRT-LLM (NVIDIA)](https://developer.nvidia.com/blog/optimizing-inference-on-llama-2-with-tensorrt-llm/)
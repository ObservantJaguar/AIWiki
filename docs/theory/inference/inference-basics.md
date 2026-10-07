---
title: Inference fundamentals
layout: default
parent: Inference
grand_parent: Theory
---

# Inference fundamentals

Inference is running a trained model to generate an output. The engineering realities of inference — memory footprint, latency and throughput — are different from training and define how models are deployed.

## What happens during inference

For a generative LLM, inference is **autoregressive**: the model is called repeatedly, each call predicting the next token and appending it to the context.

```text
input tokens -> [ model ] -> next token
input + token -> [ model ] -> next token
... (repeat until end-of-sequence)
```

This loop is why LLM latency scales with the number of generated tokens, not just input length.

## The key metrics

- **Latency**: time to first token (TTFT) and time per output token (TPOT). Matters for interactive use.
- **Throughput**: tokens generated per second across all requests (tokens/s). Matters for cost per token.
- **Memory footprint**: whether the model and its KV-cache fit in VRAM.

## Where the work goes

- **Prefill phase**: processes the input prompt in parallel; compute-heavy.
- **Decode phase**: generates one token at a time; memory-bandwidth-bound because each step reads the whole model.

## Fitting models into memory

Model weights dominate memory at full precision:

```text
memory ~= parameters * bytes_per_param
7B model in fp16 ~= 7 * 2 GB = 14 GB
```

Techniques to shrink the footprint: **quantization** (INT8, INT4), the **KV-cache** for long contexts, and offloading (CPU/disk) for weak hardware.

## Key features

- Autoregressive decode is the fundamental latency cost.
- Serving engines optimize throughput via continuous batching (see [batching](batching.html)).
- Quantization and the KV-cache are the two main levers for memory.

## Resources

- [LLM inference lecture (Hugging Face)](https://huggingface.co/blog/llm-inference)
- [Mastering LLM Techniques: Inference Optimization](https://developer.nvidia.com/blog/mastering-llm-techniques-inference-optimization/)
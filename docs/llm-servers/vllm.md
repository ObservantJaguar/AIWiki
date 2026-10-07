---
title: vLLM
layout: default
parent: LLM servers
grand_parent: Tools
---

# vLLM

vLLM is a high-throughput GPU inference engine for LLMs. Its **PagedAttention** mechanism and continuous batching make it the standard choice for production serving of open models at scale, often 2-4x faster than naive serving.

## Overview

- **Language**: Python (PyTorch)
- **License**: Apache 2.0
- **Developer**: UC Berkeley, open source
- **Status**: production-grade, extremely widely adopted

## Key features

- **PagedAttention**: dynamic KV-cache allocation, near-zero wasted memory and high concurrency.
- **Continuous batching**: requests join and leave the GPU batch as they finish, maximizing utilization.
- **OpenAI-compatible API**: drop-in backend for existing OpenAI SDK clients.
- **Broad model support**: Llama, Mistral, Qwen, Gemma, vision-language and embedding models.
- **Quantization**: AWQ, GPTQ, FP8 and more for memory-efficient serving.
- **Parallelism**: tensor and pipeline parallelism for large models across multiple GPUs.

## Best for

- Production API serving of open LLMs on GPU infra.
- High-traffic retrieval-augmented generation and agent backends.
- Anyone needing maximum tokens/sec per dollar.

## Resources

- [vLLM documentation](https://docs.vllm.ai/)
- [vLLM GitHub](https://github.com/vllm-project/vllm)
- [PagedAttention paper](https://arxiv.org/abs/2309.06180)
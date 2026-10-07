---
title: Text Generation Inference
layout: default
parent: LLM servers
grand_parent: Tools
---

# Text Generation Inference (TGI)

TGI is Hugging Face's production inference server for LLMs. It combines high throughput, an OpenAI-compatible API and tight integration with the Hugging Face model hub, making it a popular choice alongside vLLM.

## Overview

- **Language**: Rust/Python
- **License**: Apache 2.0
- **Developer**: Hugging Face
- **Status**: production-grade, actively maintained

## Key features

- **Continuous batching** for high throughput.
- **OpenAI-compatible API** plus Hf features (message API, tokens details).
- **Memory optimizations**: quantization (GPTQ, AWQ, FP8), flash attention.
- **Hugging Face integration**: pulls models directly from the hub, incl. gated ones.
- **Multi-GPU**: tensor parallelism to serve large models.
- **Vision and embeddings support**: some multimodal and embeddings models.

## Best for

- Deploying models straight from the Hugging Face hub.
- Teams already invested in the HF ecosystem.
- Production GPU serving with OpenAI-compatible endpoints.

## Resources

- [TGI GitHub](https://github.com/huggingface/text-generation-inference)
- [TGI documentation](https://huggingface.co/docs/text-generation-inference/index)
- [Hugging Face Inference Endpoints](https://huggingface.co/inference-endpoints)
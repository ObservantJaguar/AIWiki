---
title: llama-server
layout: default
parent: LLM servers
grand_parent: Tools
---

# llama-server

`llama-server` is the built-in OpenAI-compatible HTTP server shipped with llama.cpp. It turns any GGUF model into a REST API in one command, with no extra dependencies — a lightweight alternative to full serving platforms.

## Overview

- **Engine**: llama.cpp (C/C++)
- **License**: MIT
- **Developer**: llama.cpp project
- **Status**: mature, improves with llama.cpp releases

## Key features

- **OpenAI-compatible API**: `/v1/chat/completions`, completions, embeddings.
- **Built-in web UI** for chat and model inspection.
- **GGUF native**: works with all llama.cpp quantization levels.
- **CPU and GPU**: runs on plain CPU or with GPU offload.
- **Server-side options**: context size, threads, GPU layers, sampling parameters.
- **Tool/function calling and structured output** support.

## Best for

- Running a single model as a local API for scripts and apps.
- Embedding a lightweight LLM server into an app or device.
- When vLLM/TGI are overkill or fail on CPU-only hardware.

## Resources

- [llama.cpp server example](https://github.com/ggml-org/llama.cpp/tree/master/examples/server)
- [llama.cpp README](https://github.com/ggml-org/llama.cpp)
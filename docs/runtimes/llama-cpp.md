---
title: llama.cpp
layout: default
parent: Runtimes and frameworks
grand_parent: Tools
---

# llama.cpp

llama.cpp is a C/C++ inference engine for LLMs, focused on running large models on consumer hardware, including on CPU. It introduced the widely used **GGUF** model format and is the engine behind many local-first AI tools.

## Overview

- **Language**: C/C++ (with bindings for many languages)
- **License**: MIT
- **Developer**: Georgi Gerganov (open source)
- **Status**: very active, huge community

## Key features

- **CPU-first but GPU-capable**: runs on plain CPUs, plus CUDA, Metal, Vulkan, ROCm and SYCL backends.
- **GGUF format**: quantized weights (q2_k … q8_0) giving precise size/quality control.
- **Low RAM footprint**: 4-bit quantization lets 7B models run on 8 GB machines.
- **Blazing-fast startup**: no heavy dependency stack, ideal for embeddable serving.
- **`llama-server`**: built-in OpenAI-compatible HTTP server with a chat UI.
- **Bindings**: Python, Go, Node, Rust and many others.

## Best for

- Running models locally on modest hardware or pure CPU.
- Embedded and edge deployments.
- On-device assistant apps and the backend of tools such as Ollama.

## Resources

- [llama.cpp GitHub](https://github.com/ggml-org/llama.cpp)
- [GGUF format documentation](https://github.com/ggml-org/llama.cpp/blob/master/README.md)
- [llama.cpp discussion / community](https://github.com/ggml-org/llama.cpp/discussions)
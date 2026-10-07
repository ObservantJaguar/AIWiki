---
title: Ollama
layout: default
parent: LLM servers
grand_parent: Tools
---

# Ollama

Ollama is the most approachable way to run open LLMs locally. It bundles model download, quantization logistics and an OpenAI-compatible API into a single command, hiding the complexity of GGUF files and inference engines.

## Overview

- **Language**: Go/C++ (llama.cpp backend)
- **License**: Apache 2.0 (MIT for most parts)
- **Developer**: Ollama Inc.
- **Status**: very active, large community

## Key features

- **One-command model download and run**: `ollama run llama3.2`.
- **GGUF-based**: uses llama.cpp with quantized models; choose your size/quality level.
- **OpenAI-compatible API** on `127.0.0.1:11434`.
- **Cross-platform**: macOS, Linux, Windows; runs on CPU or GPU.
- **Modelfile**: version your prompts, templates and parameters as code.
- **Library of curated models**: Llama, Mistral, Gemma, Qwen, embeddings and vision models.

## Best for

- Local prototyping and personal assistants.
- Teams that want the lowest setup effort for a runnable model.
- Educational use and fast experiments.

## Resources

- [Ollama website](https://ollama.com/)
- [Ollama GitHub](https://github.com/ollama/ollama)
- [Ollama library](https://ollama.com/library)
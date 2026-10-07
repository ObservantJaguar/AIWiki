---
title: LM Studio
layout: default
parent: LLM servers
grand_parent: Tools
---

# LM Studio

LM Studio is a desktop application (GUI) for discovering, downloading and running local language models. It wraps llama.cpp in a polished interface and provides a local OpenAI-compatible server for development.

## Overview

- **Type**: desktop GUI application (Windows, macOS, Linux)
- **License**: free to use (components open source; app is proprietary)
- **Developer**: LM Studio Software
- **Status**: mature, popular with hobbyists and developers

## Note on licensing

The LM Studio application itself is **Proprietary** (freeware), not open source. The underlying inference backend is based on llama.cpp. Keep this in mind when evaluating fully-open self-hosted alternatives.

## Key features

- **Model discovery**: browse and search the catalog, download with one click.
- **GGUF quantization selection**: pick a size/quality trade-off visually.
- **GPU offloading**: automatic layer offload between GPU and CPU.
- **Chat playground**: structured and free-form chat plus prompt presets.
- **Local OpenAI-compatible server** with CORS for local web apps.
- **Vision and multimodal support** for compatible models.

## Best for

- Non-engineers who want a model running in minutes.
- Prototyping apps against a local OpenAI-compatible endpoint.
- Evaluating models without dealing with the CLI.

## Resources

- [LM Studio website](https://lmstudio.ai/)
- [LM Studio docs](https://lmstudio.ai/docs)
---
title: LocalAI
layout: default
parent: LLM servers
grand_parent: Tools
---

# LocalAI

LocalAI is a free, self-hosted, OpenAI-compatible API that runs models locally, primarily on CPU, with no dedicated GPU required. It is designed as a drop-in replacement for OpenAI endpoints that you can run on your own hardware.

## Overview

- **Language**: Go and C++
- **License**: MIT
- **Developer**: LocalAI project (open source)
- **Status**: active, self-host focused

## Key features

- **OpenAI-compatible API**: chat, completions, embeddings, image generation endpoints.
- **CPU-friendly**: runs on consumer hardware; optional GPU acceleration.
- **Multiple backends**: llama.cpp, and more via configurable model engines.
- **Voice and vision**: also serves TTS (text-to-speech) and image generation.
- **Docker-first**: simple single-container deployment.
- **Privacy/control**: no external calls — everything runs inside your infrastructure.

## Best for

- Self-hosting a full AI gateway on modest or CPU-only hardware.
- Replacing OpenAI API URLs in existing apps with an OSS backend.
- Offline-first or data-sensitive deployments.

## Resources

- [LocalAI website](https://localai.io/)
- [LocalAI GitHub](https://github.com/mudler/LocalAI)
- [LocalAI models gallery](https://models.localai.io/)
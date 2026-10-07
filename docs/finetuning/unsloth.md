---
title: unsloth
layout: default
parent: Finetuning tools
grand_parent: Tools
---

# unsloth

unsloth is a fine-tuning framework that accelerates LoRA/QLoRA training of open LLMs and cuts memory usage, letting 7B-13B models be fine-tuned on a single consumer GPU. It redesigned HF training internals for speed.

## Overview

- **Language**: Python (PyTorch)
- **License**: Apache 2.0
- **Developer**: UnsLoth AI (open source)
- **Status**: fast-growing, very popular for consumer-grade fine-tuning

## Key features

- **Large speed-ups**: claims ~2x faster training with less VRAM.
- **Memory savings**: up to ~80% less memory than standard QLoRA.
- **Broad model support**: Llama, Mistral, Gemma, Qwen, and more.
- **Drop-in with PEFT/TRL**: uses standard Hugging Face interfaces.
- **Native trained GGUF**: quantize the fine-tuned model for llama.cpp/Ollama.
- **Simple notebook/CLI recipes**: low-friction to start.

## Best for

- Fine-tuning on a single GPU or even free-tier notebooks.
- Quickly producing a fine-tuned model you want to run locally (GGUF).
- Beginners who want speed without complex trainer customizations.

## Resources

- [unsloth GitHub](https://github.com/unslothai/unsloth)
- [unsloth documentation](https://docs.unsloth.ai/)
- [unsloth HF pages](https://huggingface.co/unsloth)
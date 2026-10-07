---
title: Hugging Face PEFT
layout: default
parent: Finetuning tools
grand_parent: Tools
---

# Hugging Face PEFT

PEFT (Parameter-Efficient Fine-Tuning) is Hugging Face's library of methods that fine-tune a model by learning a small number of additional parameters instead of updating the whole model. It is the reference way to apply LoRA and QLoRA within the HF ecosystem.

## Overview

- **Language**: Python (PyTorch)
- **License**: Apache 2.0
- **Developer**: Hugging Face (open source)
- **Status**: mature, the standard for HF fine-tuning

## Key features

- **Methods**: LoRA, QLoRA, and full fine-tuning variants (IA3, AdaLoRA, Prefix-Tuning).
- **Small adapters**: train 0.1-1% of parameters, save tiny adapter files.
- **QLoRA**: 4-bit base model + fp16 adapters for consumer-GPU fine-tuning.
- **Seamless integration**: works with the Transformers `Trainer`.
- **Merging**: adapters can be merged back into the base weights.
- **Multi-adapter**: swap adapters at inference time without reloading.

## Best for

- Fine-tuning Llama/Mistral/Qwen-class models on limited VRAM.
- Producing small, portable adapters for many tasks or users.
- Any HF-based training pipeline that needs efficient adaptation.

## Resources

- [PEFT documentation](https://huggingface.co/docs/peft/index)
- [PEFT GitHub](https://github.com/huggingface/peft)
- [LoRA / QLoRA papers](https://arxiv.org/abs/2305.14314)
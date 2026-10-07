---
title: axolotl
layout: default
parent: Finetuning tools
grand_parent: Tools
---

# axolotl

axolotl is a fine-tuning tool driven by a single YAML config, wrapping the HF ecosystem (Transformers, PEFT, TRL, datasets) behind a friendly interface. It is popular for full fine-tunes and LoRA/QLoRA runs of open LLMs.

## Overview

- **Language**: Python (PyTorch)
- **License**: Apache 2.0
- **Developer**: OpenAccess AI Collective (open source)
- **Status**: active, well-supported community

## Key features

- **YAML-only configuration**: dataset path, model, LoRA or full tune, hyperparameters in one file.
- **Config-preset style**: works well with progressive settings from the community.
- **QLoRA and multi-GPU** out of the box.
- **Hugging Face hub integration**: push training, push models and adapters.
- **Datasets**: uses HF `datasets`, supports standard chat formats (Alpaca, ShareGPT, etc.).
- **Reproducibility**: share the config and reproduce training exactly.

## Best for

- Running fine-tunes without writing much trainer boilerplate.
- Community-standard chat and instruct fine-tunes of Llama/Mistral models.
- Teams that want a single config file to version and share.

## Resources

- [axolotl GitHub](https://github.com/OpenAccess-AI-Collective/axolotl)
- [axolotl documentation](https://axolotl.ai/)
- [OpenAccess-AI-Collective](https://github.com/OpenAccess-AI-Collective)
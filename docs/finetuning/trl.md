---
title: TRL
layout: default
parent: Finetuning tools
grand_parent: Tools
---

# TRL (Transformer Reinforcement Learning)

TRL is Hugging Face's library for training chat and aligned models — supervised fine-tuning, preference optimization and RLHF — backed by the standard HF `Trainer`. It is the go-to tool for the post-training (alignment) stage.

## Overview

- **Language**: Python (PyTorch)
- **License**: Apache 2.0
- **Developer**: Hugging Face (open source)
- **Status**: mature, actively developed

## Key features

- **SFTTrainer**: supervised fine-tuning, optimizes chat/template data.
- **DPOTrainer**: direct preference optimization on preference pairs.
- **ORPO, KTO, GRPO**: a menu of modern preference/RL objectives.
- **PPO trainer** (classic RLHF) for reward-model-based training.
- **RewardModeling** utilities for training reward models.
- **DeepSpeed / distributed**: scales via existing trainer integrations.

## Best for

- The alignment stage: making a base model follow instructions.
- Fine-tuning with SFT then DPO on a small, focused dataset.
- Teams using the HF ecosystem who want robust, well-tested trainers.

## Resources

- [TRL documentation](https://huggingface.co/docs/trl/index)
- [TRL GitHub](https://github.com/huggingface/trl)
- [TRL examples](https://huggingface.co/docs/trl/quickstart)
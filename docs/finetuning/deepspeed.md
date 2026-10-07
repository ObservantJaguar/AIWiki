---
title: DeepSpeed
layout: default
parent: Finetuning tools
grand_parent: Tools
---

# DeepSpeed

DeepSpeed is Microsoft's deep learning optimization library that enables training and inference of very large models by sharding memory and compute across many GPUs. It underpins much of large-scale open-model fine-tuning.

## Overview

- **Language**: Python (PyTorch)
- **License**: Apache 2.0
- **Developer**: Microsoft (open source)
- **Status**: mature, industry-proven

## Key features

- **ZeRO**: sharding of optimizer states, gradients and parameters across GPUs (stages 1-3).
- **Offloading**: CPU and NVMe offload for memory beyond VRAM.
- **Pathways/inference**: optimized inference for large models.
- **Merging with HF `Trainer`**: `deepspeed` config inside Transformers.
- **Checkpointing**: Sparse attention kernels and communication optimizations.

## Best for

- Training models that do not fit on a single GPU.
- Multi-node, multi-GPU fine-tuning of large open models.
- Teams that need fine-grained control over memory and compute.

## Resources

- [DeepSpeed website](https://www.deepspeed.ai/)
- [DeepSpeed GitHub](https://github.com/microsoft/DeepSpeed)
- [DeepSpeed + Hugging Face tutorial](https://huggingface.co/docs/transformers/main_classes/deepspeed)
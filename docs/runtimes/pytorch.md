---
title: PyTorch
layout: default
parent: Runtimes and frameworks
grand_parent: Tools
---

# PyTorch

PyTorch is the de-facto standard deep learning framework for research and an increasingly common choice for production. Its define-by-run autograd and seamless GPU support underpin the open-source AI ecosystem.

## Overview

- **Language**: Python (with a C++ core)
- **License**: BSD-style
- **Developer**: Meta (PyTorch Foundation)
- **Status**: mature, very widely adopted

## Key features

- **Define-by-run**: dynamic computation graphs built as you execute Python, easy to debug.
- **Autograd**: automatic differentiation for backpropagation.
- **GPU acceleration**: CUDA, ROCm and Apple Silicon backends.
- **Strong ecosystem**: torchvision, torchaudio, Hugging Face Transformers all build on PyTorch.
- **Distribution**: torch.distributed, FSDP for sharded training.

## Best for

- Research and experimentation (the overwhelming default).
- Fine-tuning and inference of LLMs and diffusion models.
- Serving via TorchServe or integration with vLLM/TensorRT engines.

## Resources

- [PyTorch website](https://pytorch.org/)
- [PyTorch GitHub](https://github.com/pytorch/pytorch)
- [PyTorch tutorials](https://pytorch.org/tutorials/)
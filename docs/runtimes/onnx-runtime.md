---
title: ONNX Runtime
layout: default
parent: Runtimes and frameworks
grand_parent: Tools
---

# ONNX Runtime

ONNX Runtime is a cross-platform inference engine for models in the ONNX (Open Neural Network Exchange) format. It lets you train in any framework — PyTorch, TensorFlow, JAX — and deploy the resulting model to a wide range of CPUs, GPUs and edge devices.

## Overview

- **Language**: C++ core with Python, C#, Java, JS bindings
- **License**: MIT
- **Developer**: Microsoft (open source)
- **Status**: mature, production-proven

## Key features

- **Model portability**: any ONNX model runs anywhere with a compatible runtime.
- **Multiple execution providers**: CPU, CUDA, ROCm, DirectML, OpenVINO and mobile CPUs.
- **Optimization**: graph optimizations, quantization and model fusion for speed.
- **Quantization tooling**: convert fp32 models to INT8 with low accuracy loss.
- **Integration**: Hugging Face `optimum` can export and quantize transformers to ONNX.

## Best for

- Deploying one model across server, desktop, browser (via WebAssembly) and edge.
- Accelerating CPU inference on Windows/Linux/macOS.
- Teams that want framework-agnostic serving.

## Resources

- [ONNX Runtime website](https://onnxruntime.ai/)
- [ONNX Runtime GitHub](https://github.com/microsoft/onnxruntime)
- [Hugging Face Optimum](https://huggingface.co/docs/optimum/index)
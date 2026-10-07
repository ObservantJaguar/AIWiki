---
title: Quantization
layout: default
parent: Inference
grand_parent: Theory
---

# Quantization

Quantization reduces the precision of a model's weights — and often activations — to shrink memory and speed up inference at the cost of a small accuracy hit. It is the single most important technique for running models on limited hardware.

## The idea

Model weights in float16/bf16 use 2 bytes each. Quantizing to 8-bit (INT8) or 4-bit (INT4/NF4) stores each weight in 1 or 0.5 bytes, roughly halving or quartering the memory footprint.

```text
full precision:  7B params * 2 bytes = 14 GB
INT8:            7B params * 1 byte  = 7 GB
INT4:            7B params * 0.5 byte = 3.5 GB
```

## Levels of quantization

- **Post-training quantization (PTQ)**: quantize an already-trained model, no data. Fast to produce, slightly larger accuracy loss.
- **Weight quantization only (W4A16)**: quantize weights, keep activations at 16-bit. The standard for LLM inference engines.
- **Quantization-aware training (QAT)**: train with simulated quantization so the model learns to tolerate it. Best quality, more expensive.

## Formats in the open-source ecosystem

- **GGUF** (llama.cpp): multiple quantization levels (`q2_k`, `q4_k_m`, `q5_k_m`, `q8_0`), CPU-friendly, selected per quality/size trade-off.
- **NF4** (bitsandbytes / QLoRA): orthogonal 4-bit used for memory-efficient fine-tuning and load.
- **AWQ** and **GPTQ**: 4-bit weight formats popular with GPU serving (vLLM).

## Practical guidance

- `q4_k_m` / `q5_k_m` GGUF are good defaults for local CPU/GPU use.
- INT4 via AWQ/GPTQ is typical for high-throughput API serving on GPU.
- Quality loss grows as precision drops; for 7B models 4-bit is often acceptable.

## Key features

- Cuts memory and increases tokens/sec.
- INT4/INT8 dominate practical LLM deployment.
- Choice of format depends on hardware and serving engine.

## Resources

- [Introduction to quantization (Hugging Face)](https://huggingface.co/docs/transformers/main/en/quantization/overview)
- [GGUF format (llama.cpp)](https://github.com/ggml-org/llama.cpp/blob/master/README.md)
- [AWQ](https://github.com/mit-han-lab/llm-awq) and [GPTQ](https://arxiv.org/abs/2210.17323)
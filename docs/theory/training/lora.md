---
title: LoRA and QLoRA
layout: default
parent: Training concepts
grand_parent: Theory
---

# LoRA and QLoRA

Fine-tuning a large model by updating every weight is expensive. LoRA (Low-Rank Adaptation) and its successor QLoRA make fine-tuning feasible on a single consumer GPU by learning only a tiny set of injected parameters.

## The LoRA idea

Instead of updating the full weight matrix `W`, LoRA freezes `W` and learns a low-rank update `W + B*A`, where `B` and `A` are small matrices whose product has low rank.

```text
output = W*x + (B * A) * x
```

Because `B*A` is small, only a fraction of the parameters are trainable — often 0.1% to 1% of the model — while performance stays close to full fine-tuning.

## Why it works

Pretrained models sit near a low-dimensional subspace of suitable behaviors. The low-rank update captures the task-specific shift without disturbing the base weights.

## QLoRA

QLoRA pushes this further by keeping the base model in 4-bit precision while training the LoRA adapters at higher precision, dramatically cutting GPU memory.

- **4-bit base model**: quantized to NF4 (normal float 4) to save memory.
- **High-precision adapters**: LoRA weights stay in float16/bf16.
- **Gradient checkpointing**: trades compute for memory.

Result: a 7B model can be fine-tuned on a single consumer GPU with 16–24 GB of VRAM.

## When to use

- Limited VRAM (consumer GPUs).
- Many small adapters for different tasks or users.
- Fast iteration on datasets.

## Key features

- Tiny trainable parameter count (0.1–1%).
- Inferentially free: adapters can be merged back into the weights.
- QLoRA makes fine-tuning viable on commodity hardware.

## Resources

- [LoRA: Low-Rank Adaptation of Large Language Models](https://arxiv.org/abs/2106.09685)
- [QLoRA: Efficient Finetuning of Quantized LLMs](https://arxiv.org/abs/2305.14314)
- [Hugging Face: PEFT documentation](https://huggingface.co/docs/peft/index)
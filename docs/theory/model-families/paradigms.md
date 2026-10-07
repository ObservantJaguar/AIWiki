---
title: Training paradigms
layout: default
parent: Model families and paradigms
grand_parent: Theory
---

# Training paradigms: pretraining, scaling and transfer

"Training a model" can mean very different things depending on how much data, compute and labels are available. The major paradigms are pretraining, fine-tuning, few-shot learning and reinforcement-learning-from-human-feedback.

## Pretraining

Pretraining trains a model on a huge, mostly unlabeled corpus to learn general representations or next-token prediction. It is the enormously expensive first step.

- **Self-supervised**: learns from the data itself (masked token prediction for BERT, next-token prediction for GPT).
- **Compute-heavy**: requires large GPU clusters, often many days or weeks.
- **Foundation model**: the result is a general-purpose base used for downstream tasks.

## Fine-tuning

Fine-tuning continues training a pretrained model on a smaller, task-specific dataset, adapting it to a domain or behavior.

- **Instruction tuning**: fine-tune on prompt/response pairs so the model follows instructions.
- **Domain adaptation**: specialize with domain data (legal, medical, code).
- **Efficient variants**: LoRA and QLoRA update a small set of parameters (see the [finetuning tools topic](/finetuning/)).

## Few-shot and in-context learning

A model can often be steered with relatively few examples supplied in the prompt, without any training. This is **in-context learning**; a handful of demonstrations is *few-shot* prompting, none is *zero-shot*.

## RLHF and alignment

Reinforcement learning from human feedback trains the model to produce outputs humans rate highly, improving helpfulness, safety and following instructions. See [Ethics and safety](/theory/safety/).

## Scaling laws

Across models of different sizes, performance follows predictable **scaling laws** in parameters, data and compute — the empirical basis for the "bigger is better" trajectory of modern LLMs.

## Key features

- Pretraining is capital-intensive; fine-tuning is comparatively cheap and done on commodity hardware.
- Efficient fine-tuning (LoRA, QLoRA) is the standard way to adapt open models.
- Few-shot prompting requires no training at all.

## Resources

- [Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361)
- [Llama 3 technical report (pretraining + instruction tuning)](https://arxiv.org/abs/2407.21783)
- [Hugging Face: Fine-tune a pretrained model](https://huggingface.co/docs/transformers/training)
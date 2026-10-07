---
title: Instruction tuning and few-shot
layout: default
parent: Training concepts
grand_parent: Theory
---

# Instruction tuning and few-shot learning

Two practical techniques that turn a raw base model into something that follows directions: instruction tuning (a training step) and few-shot prompting (no training at all).

## Instruction tuning

Models pretrained on raw text predict the next token well but do not reliably follow instructions. **Instruction tuning** fine-tunes the model on many (instruction, response) examples, teaching it the expected input/output behavior.

- **Data**: crowdsourced or synthetically generated instruction sets.
- **Effect**: dramatic improvement in helpfulness, chat and zero-shot generalization.
- **Standard**: introduces an explicit chat/template format for the model.

Popular instruction datasets include Alpaca, Dolly and GPT-4-generated sets. This is the "chat" or "instruct" checkpoint that most open models ship.

## Few-shot learning

Few-shot learning changes the behavior at inference time by including a few demonstrations in the prompt — no weight updates needed.

```text
Input: "Translate to French: hello"
Demonstration 1: "dog -> chien"
Demonstration 2: "cat -> chat"
Target: "hello -> ..."
```

- **Zero-shot**: no examples, just the instruction.
- **One-shot / few-shot**: 1 or a few examples.
- **In-context learning**: the model infers the pattern from the demonstrations.

## In-context vs in-weights

- **In-context (few-shot prompting)**: no training, cheap, easily changeable, limited by context window.
- **In-weights (instruction tuning / fine-tuning)**: persistent behavior, robust, requires a training run.

## Which to use

- Have a task and examples? Start with **few-shot prompting**.
- Need consistent, structured behavior? **Instruction tune** (or fine-tune).
- Changing behavior constantly? Prefer **prompting**.

## Key features

- Instruction tuning is the standard post-training step for chat models.
- Few-shot prompting is a powerful no-code way to steer behavior.
- They complement each other: tune the base, then prompt the tuned model.

## Resources

- [Stanford Alpaca](https://github.com/tatsu-lab/stanford_alpaca)
- [Language Models are Few-Shot Learners (GPT-3)](https://arxiv.org/abs/2005.14165)
- [Hugging Face: Fine-tune a chat model](https://huggingface.co/docs/transformers/training)
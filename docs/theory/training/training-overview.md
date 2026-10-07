---
title: Training from scratch vs fine-tuning
layout: default
parent: Training concepts
grand_parent: Theory
---

# Training from scratch vs fine-tuning

There are two very different ways to obtain a working model. Understanding the trade-off — compute, data and expertise — explains why the ecosystem is built the way it is.

## Training from scratch

Training a model's weights from random initialization on a large dataset. For an LLM this means pretraining on massive text for weeks on GPU clusters.

- **Cost**: extremely high (hundreds of thousands of dollars in GPU time for a large model).
- **Data**: enormous, curated corpora (hundreds of billions of tokens).
- **Expertise**: distributed training, data pipelines, convergence debugging.
- **Result**: a foundation model.

Who does this? Research labs and companies with GPU fleets. For almost everyone else it is impractical.

## Fine-tuning

Starting from a pretrained model and continuing training on a smaller, specialized dataset.

- **Cost**: low to moderate; often possible on a single GPU.
- **Data**: relatively small (thousands to millions of examples).
- **Expertise**: moderate; tooling (PEFT, axolotl, TRL) has lowered the bar.
- **Result**: a specialized version of the base model.

## When to choose which

```text
Situation                                | Approach
-----------------------------------------------------
You need a new base model               | train from scratch
You need a domain expert                | fine-tune
You need instruction-following behavior | instruction fine-tune
You need to steer behavior cheaply      | LoRA / QLoRA
You need one-off tasks                  | prompt engineering
```

## Pretraining then fine-tuning

The dominant recipe is: pretrain a capable base model, then fine-tune it with supervised fine-tuning (SFT) and alignment to make it helpful and safe. Open models ship both the base and the instruct checkpoints.

## Key features

- From-scratch = foundation work, done by the few.
- Fine-tuning = adaptation, done by the many.
- Pretrained open weights make fine-tuning the economically rational path.

## Resources

- [The Bitter Lesson (Sutton)](http://www.incompleteideas.net/IncIdeas/BitterLesson.html)
- [Hugging Face: Fine-tune a pretrained model](https://huggingface.co/docs/transformers/training)
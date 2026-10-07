---
title: RLHF and direct alignment
layout: default
parent: Training concepts
grand_parent: Theory
---

# RLHF and direct alignment

After supervised fine-tuning, models are usually **aligned** — trained to be helpful, harmless and instruction-following. The classic method is RLHF; newer direct methods such as DPO are rapidly replacing it for simplicity.

## RLHF (reinforcement learning from human feedback)

RLHF has three stages:

1. **Supervised fine-tuning (SFT)**: train on curated instruction/response pairs.
2. **Reward model**: collect human pairwise comparisons of model outputs and train a reward model to predict which response humans prefer.
3. **RL optimization**: use reinforcement learning (e.g. PPO) to maximize the reward model's score while staying close to the SFT policy.

The result is a model whose outputs land where humans rate them highly — more helpful, safer, more aligned with instructions.

## Costs and drawbacks of RLHF

- Expensive: needs a reward model, RL training loop, and careful prompt distribution.
- Unstable: PPO is notoriously sensitive to hyperparameters and reward hacking.

## DPO (direct preference optimization)

DPO reframes alignment as a classification problem: given preference pairs, it updates the model directly with a supervised loss, without an explicit reward model or RL loop.

- **Simpler**: one training run, no reward model.
- **Stable**: standard supervised training machinery.
- **Equivalent in principle** to RLHF for a family of reward functions.

## Other direct methods

- **KTO**: works from binary "desired/undesired" signals instead of pairs.
- **ORPO**: combines SFT and preference optimization in one objective.
- **RLAIF**: uses AI-generated comparisons instead of human labels.

## Typical alignment pipeline

```text
pretrain  ->  SFT  ->  preference optimization (RLHF or DPO)
```

## Key features

- Alignment makes base models usable for chat and instruction following.
- DPO and related direct methods make alignment cheaper and more accessible.
- The choice of reward signal (human vs AI) shapes what "alignment" means.

## Resources

- [Training language models to follow instructions (InstructGPT)](https://arxiv.org/abs/2203.02155)
- [Direct Preference Optimization: Your Language Model is Secretly a Reward Model](https://arxiv.org/abs/2305.18290)
- [Hugging Face: TRL documentation](https://huggingface.co/docs/trl/index)
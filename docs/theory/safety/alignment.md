---
title: Alignment
layout: default
parent: Ethics and safety
grand_parent: Theory
---

# Alignment

Alignment is the discipline of making a model's behavior track human intent and values: helpfulness, harmlessness, truthfulness and following instructions. It spans training objectives, evaluation and ongoing governance.

## What alignment addresses

A raw pretrained model only predicts the next token; it has no notion of being helpful or safe. Alignment shapes behavior so the model:

- Follows instructions and stays on task.
- Refuses harmful or disallowed requests.
- Produces accurate and honest responses where possible.
- Behaves predictably under varied prompting.

## Methods

- **Supervised fine-tuning (SFT)**: instruction and good-bad response pairs.
- **Reinforcement learning from human feedback (RLHF)**: optimize a reward model trained on human preferences.
- **Direct preference optimization (DPO)** and relatives: simpler, direct-behavior alignment.
- **Constitutional / RLAIF**: align against a written rule set with AI-generated judgment.
- See the [training concepts](/theory/training/) section for the technical detail.

## Alignment vs capability

Alignment is distinct from capability: a more capable model is not automatically more aligned — in fact more capable models can find subtler ways to misbehave. Progress in capability can outpace alignment work, which is why red-teaming and evaluation stay essential.

## Evaluating alignment

- Safety and refusal benchmarks (e.g. refusal, harm categories).
- Helpfulness/harmlessness trade-offs measured with human and LLM judges.
- Continuous red-team testing for jailbreaks and prompt injection.

## Key features

- Alignment is a training + evaluation + governance problem, not a single step.
- Methods (SFT → RLHF/DPO) form a standard pipeline.
- Alignment must keep pace with capability growth.

## Resources

- [Constitutional AI](https://arxiv.org/abs/2212.08073)
- [Chinchilla (scaling and alignment trade-offs)](https://arxiv.org/abs/2203.15556)
- [OpenAI: Our approach to alignment research](https://openai.com/safety/)
---
title: Positional encoding
layout: default
parent: Transformer architecture
grand_parent: Theory
---

# Positional encoding

Transformers process tokens in parallel and have no intrinsic notion of order. Positional encodings inject information about each token's position so the model can reason about sequence structure.

## Why it is needed

Attention is permutation-equivariant: if you shuffle the input tokens, the attention output shuffles accordingly. That makes order invisible to the model. Positional encodings break this symmetry by adding a position-dependent signal.

## Absolute positional encoding

The original transformer added fixed sinusoidal vectors, one per position, whose frequencies differ per dimension:

```text
PE(pos, 2i)     = sin(pos / 10000^(2i / d_model))
PE(pos, 2i + 1) = cos(pos / 10000^(2i / d_model))
```

The frequencies let the model attend to relative offsets via linear combinations of the sinusoidals.

## Learned embeddings

Many modern models instead use learned positional embeddings — a trainable vector per position. Simple and effective within the trained context window, but they do not extrapolate to longer sequences.

## Rotary position embeddings (RoPE)

RoPE rotates the query and key vectors by an angle proportional to their position. It encodes **relative** position cheaply and generalizes better to longer contexts. It is the standard choice in modern LLMs such as LLaMA, Mistral and Qwen.

## Relative and ALiBi

Alternatives such as ALiBi add a position-dependent bias to the attention scores instead of modifying embeddings, which improves length extrapolation without additional learnable parameters.

## Key features

- Essential for any permutation-equivariant sequence model.
- Absent or weak positional encoding degrades long-context performance.
- RoPE and ALiBi are preferred for long-context LLMs today.

## Resources

- [Attention Is All You Need: positional encoding](https://arxiv.org/abs/1706.03762)
- [RoFormer: Enhanced Transformer with Rotary Position Embedding](https://arxiv.org/abs/2104.09864)
- [Train Short, Test Long: Attention with Linear Biases (ALiBi)](https://arxiv.org/abs/2108.12409)
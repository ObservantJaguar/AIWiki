---
title: Attention and self-attention
layout: default
parent: Transformer architecture
grand_parent: Theory
---

# Attention and self-attention

Attention is the mechanism that lets a model weigh the relevance of different tokens when computing a representation. It was the key idea that made transformers possible, replacing the fixed-size memory of recurrent networks.

## The idea

For each output position, the model computes a weighted combination of input values, where the weights are determined by similarities between a query and keys. This is the "attention matrix".

```text
Attention(Q, K, V) = softmax( (Q * K^T) / sqrt(d_k) ) * V
```

- `Q` (queries), `K` (keys), `V` (values) are linear projections of the inputs.
- `d_k` is the key dimension; the `sqrt(d_k)` scaling keeps dot products in a stable range.
- Softmax turns the scores into a probability distribution over positions.

## Self-attention

In **self-attention**, Q, K and V all come from the same sequence, so every token attends to every other token in the sequence. This is what lets the model capture long-range dependencies directly, without a recurrent loop.

## Multi-head attention

Instead of one attention function, the model runs several in parallel (the **heads**), each attending to different subspaces, then concatenates and projects the results. This gives the model multiple views of the relationships in the sequence.

## The attention mask

For decoder-only models, a causal (upper-triangular) mask prevents tokens from attending to future tokens, preserving the left-to-right generation property.

## Key features

- Parallel over positions: unlike RNNs, the whole sequence is processed at once.
- O(n^2) cost in sequence length — the main scaling bottleneck.
- The attention matrix is interpretable and has been used for attribution studies.

## Resources

- [Attention Is All You Need (Vaswani et al., 2017)](https://arxiv.org/abs/1706.03762)
- [The Illustrated Transformer (Jay Alammar)](https://jalammar.github.io/illustrated-transformer/)
- [Distill: Attention? Attention!](https://distill.pub/2016/augmented-rnns/)
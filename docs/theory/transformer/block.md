---
title: The transformer block
layout: default
parent: Transformer architecture
grand_parent: Theory
---

# The transformer block

A transformer is a stack of identical **blocks** (also called layers). Each block combines an attention sublayer with a feed-forward sublayer, wrapped in residual connections and normalization. Understanding one block explains the whole model.

## Structure of one block

```text
input x
  |
  +--> [ LayerNorm ] -> [ Multi-head attention ] -> + -->
  |                                                  |
  +----------------- residual add -------------------+
  |
  +--> [ LayerNorm ] -> [ Feed-forward MLP ] ------> + -->
  |                                                  |
  +----------------- residual add -------------------+
  |
output
```

## The sublayers

- **Multi-head attention**: mixes information across tokens (see [attention](attention.html)).
- **Feed-forward network (FFN)**: a two-layer MLP applied independently to each token position. In modern LLMs it usually expands the hidden dimension ~4x and uses GELU or SiLU.
- **LayerNorm**: normalizes activations per token to stabilize training.
- **Residual connections**: add the block input to the output, letting gradients flow through many layers and enabling very deep networks.

## Pre-norm vs post-norm

- **Post-norm**: normalization after the residual add (original transformer). Harder to train at depth.
- **Pre-norm**: normalization before each sublayer (modern default). More stable; leads to the "Sandwich" RMSNorm variants used by LLaMA and Mistral.

## Encoder vs decoder blocks

- **Encoder block**: fully visible self-attention (bidirectional). Used by BERT-style models.
- **Decoder block**: causal self-attention plus cross-attention over encoder output in encoder-decoder models. Decoder-only LLMs (GPT style) use only the causal self-attention branch.

## Key features

- Same block repeated many times with different weights.
- Residual connections + normalization allow hundreds of layers.
- The FFN holds the majority of trainable parameters.

## Resources

- [The Illustrated Transformer (layers part)](https://jalammar.github.io/illustrated-transformer/)
- [The Illustrated GPT-2 (residual structure)](https://jalammar.github.io/illustrated-gpt2/)
- [On Layer Normalization in Transformer](https://arxiv.org/abs/2002.04745)
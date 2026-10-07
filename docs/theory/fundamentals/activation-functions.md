---
title: Activation functions
layout: default
parent: ML/DL fundamentals
grand_parent: Theory
---

# Activation functions

Activation functions introduce non-linearity into a neural network, deciding whether and how strongly a neuron should fire given its weighted input. They are what let deep networks approximate complex functions.

## Common functions

| Function | Formula | Range | Notes |
|---|---|---|---|
| Sigmoid | `1 / (1 + exp(-x))` | (0, 1) | Classic, but suffers from vanishing gradients |
| Tanh | `(exp(x) - exp(-x)) / (exp(x) + exp(-x))` | (-1, 1) | Zero-centered, still can saturate |
| ReLU | `max(0, x)` | [0, inf) | Default for hidden layers in many models |
| Leaky ReLU | `max(0.01*x, x)` | (-inf, inf) | Allows a small gradient for negative inputs |
| GELU | `x * Phi(x)` | (-inf, inf) | Smoother ReLU, used in many modern transformers |
| Softmax | exp-normalized over a vector | (0, 1), sums to 1 | Converts logits to a probability distribution |

## Why ReLU dominates

ReLU is cheap, avoids the exponential saturation of sigmoid, and its constant gradient for positive inputs fights the vanishing-gradient problem — though dead neurons are a known issue, mitigated by leaky variants.

## Output-layer choices

- **Binary classification**: sigmoid — probability of the positive class.
- **Multi-class classification**: softmax — a full probability distribution over classes.
- **Regression**: no activation, or identity — a real-valued output.

## Key features

- Non-linearity is what makes deep networks expressive.
- Choice of activation affects trainability, speed and stability.
- Modern transformers predominantly use GELU or its variants in the feed-forward blocks.

## Resources

- [CS231n notes: Common activation functions](https://cs231n.github.io/neural-networks-1/#actfun)
- [PyTorch: Activation functions](https://pytorch.org/docs/stable/nn.html#non-linear-activations-weighted-sum-nonlinearity)
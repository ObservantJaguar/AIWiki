---
title: Gradient descent
layout: default
parent: ML/DL fundamentals
grand_parent: Theory
---

# Gradient descent

Gradient descent is the optimization algorithm used to train neural networks. It iteratively adjusts the parameters to reduce a loss function that measures how wrong the network is.

## The idea

Treat the loss `L` as a function of the parameters `w`. The gradient `grad L(w)` points in the direction of steepest increase of `L`; moving **against** the gradient decreases the loss.

```text
w := w - learning_rate * grad L(w)
```

## Variants

- **Batch gradient descent**: computes the gradient on the full dataset. Accurate but slow and memory-hungry.
- **Stochastic gradient descent (SGD)**: computes the gradient on a single sample. Noisy but fast to iterate.
- **Mini-batch SGD**: the practical middle ground — a gradient computed on a small batch of samples each step.
- **Momentum**: accumulates a running velocity to smooth updates and escape flat regions.
- **Adam**: adaptive per-parameter learning rates, the de-facto default optimizer for deep learning.

## Learning rate

The step size. Too large and training diverges; too small and training is impractically slow. Schedules (warmup, cosine decay) vary the rate over training.

## Backpropagation

The efficient algorithm for computing gradients in deep networks: the chain rule applied layer by layer, from output back to input. Without it, calculating gradients for millions of parameters would be intractable.

## Key features

- Iterative, local: finds a minimum, not guaranteed the global one.
- Sensitive to the learning rate and initialization.
- Scales via mini-batches and hardware parallelism.

## Resources

- [Deep Learning (Goodfellow et al.), chapter 8](https://www.deeplearningbook.org/)
- [PyTorch: What is a Neural Network?](https://pytorch.org/tutorials/beginner/blitz/neural_networks_tutorial.html)
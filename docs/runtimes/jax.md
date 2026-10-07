---
title: JAX
layout: default
parent: Runtimes and frameworks
grand_parent: Tools
---

# JAX

JAX is a high-performance numerical computing library from Google that brings NumPy-style programming together with automatic differentiation, GPU/TPU acceleration and just-in-time compilation via XLA. It powers a growing number of research-grade and high-performance models.

## Overview

- **Language**: Python
- **License**: Apache 2.0
- **Developer**: Google
- **Status**: mature research tool, increasingly used for large models

## Key features

- **NumPy-compatible API**: `jax.numpy` mirrors NumPy.
- **Autodiff (`grad`)**: supports `vmap`, `jit`, `pmap` — vectorization, compilation and parallelism as transformations.
- **XLA compilation**: fuses operations for fast GPU/TPU execution.
- **Composable transforms**: `jit`, `vmap`, `grad`, `pmap` compose arbitrarily.
- **Ecosystem**: Flax and Equinox (neural networks), Penzai, Optax (optimizers).

## Best for

- Research requiring custom large-scale training methods.
- Models that benefit from XLA fusing (language, vision, RL).
- Teams wanting fine-grained control over parallelism.

## Resources

- [JAX website](https://jax.readthedocs.io/)
- [JAX GitHub](https://github.com/google/jax)
- [Flax (neural network library for JAX)](https://github.com/google/flax)
---
title: The KV-cache
layout: default
parent: Inference
grand_parent: Theory
---

# The KV-cache

The KV-cache is the memory that stores the Key and Value tensors of past tokens across decode steps. It is what makes autoregressive generation tractable, and it is the main reason serving long contexts is memory-hungry.

## Why it exists

At each decode step the model computes attention for the current token against all previous tokens. Rather than recompute the K and V projections of every past token each step, the serving engine caches them and reuses them.

```text
step 1: compute K,V for token_1        -> cache
step 2: compute K,V for token_2        -> cache, reuse token_1
step 3: compute K,V for token_3        -> cache, reuse token_1,2
```

Without the cache, decode would be O(n^2) compute per token; with it, each step is O(n) over the cache.

## Memory growth

The cache grows with every token across all layers and heads:

```text
cache_per_token ~= layers * heads * head_dim * bytes * 2 (K and V)
```

For long context and many concurrent requests, the KV-cache can exceed the weights themselves in memory.

## Managing it

- **KV-cache quantization**: store cached values at lower precision to save memory.
- **Paged attention**: allocate cache in small pages, share memory across requests (used by vLLM).
- **Sliding window attention**: keep only a fixed-size recent window (Mistral).
- **FlashAttention**: fuses attention to reduce memory traffic, improving cache-bound performance.
- **Key reuse / prompt caching**: cache the prefill KV of shared prefixes across requests.

## Key features

- Essential for efficient autoregressive decode.
- Grows linearly with context and request count — the bottleneck for long-context serving.
- Paged attention and quantization are the main mitigations.

## Resources

- [PagedAttention / vLLM paper](https://arxiv.org/abs/2309.06180)
- [FlashAttention-2](https://arxiv.org/abs/2307.08691)
- [Mistral 7B (sliding window attention)](https://arxiv.org/abs/2310.06825)
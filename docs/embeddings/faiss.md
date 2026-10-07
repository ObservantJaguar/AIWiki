---
title: FAISS
layout: default
parent: Embeddings and vector databases
grand_parent: Tools
---

# FAISS

FAISS (Facebook AI Similarity Search) is Meta's library for efficient similarity search and clustering of dense vectors. It is not a database but a high-performance indexing library that many vector databases build upon.

## Overview

- **Language**: C++ with Python bindings
- **License**: MIT
- **Developer**: Meta (open source)
- **Status**: mature, foundational to the vector-search ecosystem

## Key features

- **Fast exact and approximate search**: exhaustive (flat) and compressed (IVF, PQ) indexes.
- **Index types**: FLAT, IVF, HNSW, PQ, and combinations for the memory/speed trade-off.
- **GPU support**: accelerated search on NVIDIA GPUs.
- **Billion-scale** indexing with compression.
- **Clustering and evaluation**: built-in k-means and recall measurement.
- **Python API**: integrate directly into NumPy/PyTorch workflows.

## Best for

- In-process similarity search within a Python service.
- Research and prototyping of retrieval methods.
- As the search core inside larger applications rather than a managed store.

## Resources

- [FAISS GitHub](https://github.com/facebookresearch/faiss)
- [FAISS wiki](https://github.com/facebookresearch/faiss/wiki)
- [Meta blog: FAISS](https://engineering.fb.com/2017/03/29/data-infrastructure/faiss-a-library-for-efficient-similarity-search/)
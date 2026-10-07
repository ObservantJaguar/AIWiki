---
title: Qdrant
layout: default
parent: Embeddings and vector databases
grand_parent: Tools
---

# Qdrant

Qdrant is a high-performance vector search engine written in Rust. It offers strong filtering, a clean REST/gRPC API and easy self-hosting, making it a top choice for production RAG systems.

## Overview

- **Language**: Rust (with a Python client)
- **License**: Apache 2.0
- **Developer**: Qdrant (open source)
- **Status**: mature, production-proven

## Key features

- **Precise filtering**: combine dense vector search with filters on payload metadata.
- **REST + gRPC APIs** and official Python, JS, .NET clients.
- **Distributed**: scale-out sharding and replication for large collections.
- **Quantization**: binary and scalar quantization to cut memory.
- **Multiple similarity metrics**: cosine, dot product, Euclidean.
- **Hybrid search**: bring-your-own sparse (BM25) tail and fuse results.

## Best for

- Production RAG with complex metadata filtering.
- Self-hosted vector search with a modern, ergonomic API.
- Anywhere confidence in recall and predictable latency matters.

## Resources

- [Qdrant website](https://qdrant.tech/)
- [Qdrant GitHub](https://github.com/qdrant/qdrant)
- [Qdrant documentation](https://qdrant.tech/documentation/)
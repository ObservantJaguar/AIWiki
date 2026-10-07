---
title: Weaviate
layout: default
parent: Embeddings and vector databases
grand_parent: Tools
---

# Weaviate

Weaviate is an open-source vector database with a REST-first, GraphQL-style API and GraphQL-native navigation. It builds in ML model modules (embeddings, generative), making it a batteries-included choice for RAG.

## Overview

- **Language**: Go
- **License**: BSD-3-Clause (core)
- **Developer**: Weaviate (open source)
- **Status**: mature, production-proven

## Key features

- **REST + GraphQL API**: expressive queries, including filters and hybrid search.
- **Modules**: text2vec and generative modules wrap embedding and LLM providers.
- **Hybrid search**: combines vector and BM25 keyword search.
- **Multi-tenancy**: isolation by tenant for SaaS workloads.
- **Sharding and replication**: scales across clusters.
- **Bring-your-own embeddings**: use any model or provider.

## Best for

- RAG systems that want search, retrieval and optional generation in one service.
- Teams that like GraphQL for structured queries.
- Multimodal (image/text) search with vectors in one store.

## Resources

- [Weaviate website](https://weaviate.io/)
- [Weaviate GitHub](https://github.com/weaviate/weaviate)
- [Weaviate documentation](https://weaviate.io/developers/weaviate)
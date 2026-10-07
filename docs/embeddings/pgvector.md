---
title: pgvector
layout: default
parent: Embeddings and vector databases
grand_parent: Tools
---

# pgvector

pgvector is an open-source extension that adds vector similarity search to PostgreSQL. It lets you store embeddings in the same database as your relational data, avoiding an extra infrastructure component.

## Overview

- **Type**: PostgreSQL extension
- **License**: PostgreSQL (permissive)
- **Developer**: pgvector community
- **Status**: mature, widely adopted in production

## Key features

- **Vector column type** with cosine, Euclidean and inner-product distance.
- **HNSW and IVFFlat indexes** for approximate nearest-neighbor search.
- **Hybrid structured + vector queries** in standard SQL.
- **Redundancy and transactions** inherited from PostgreSQL.
- **Scaling**: partitions, replicas and extensions like `pgvectorscale` for higher performance.

## Best for

- Teams already on PostgreSQL that want vector search with no new system to run.
- Moderate-scale RAG with transactional consistency.
- When SQL joins, filters and full-text search must coexist with vector similarity.

## Resources

- [pgvector GitHub](https://github.com/pgvector/pgvector)
- [pgvector documentation](https://github.com/pgvector/pgvector#installation)
- [pgvectorscale (extension)](https://github.com/timescale/pgvectorscale)
---
title: Milvus
layout: default
parent: Embeddings and vector databases
grand_parent: Tools
---

# Milvus

Milvus is an open-source vector database built for large-scale similarity search, with a cloud-native architecture that separates storage and compute. It is a strong choice for high-volume, distributed workloads.

## Overview

- **Language**: Go/C++
- **License**: Apache 2.0
- **Developer**: Zilliz, Linux Foundation project
- **Status**: mature, operates at very large scale

## Key features

- **Cloud-native**: separates the data plane (object storage) from the compute plane (query nodes), scaling independently.
- **Distributed**: horizontal scaling for billions of vectors.
- **Extensive index types**: HNSW, IVF, SCANN, DiskANN, and binary indexes.
- **Filters and scalar fields**: metadata filtering alongside vector search.
- **Milvus Lite**: an embedded single-node version for local development.
- **PyMilvus**: a rich Python SDK plus RESTful API.

## Best for

- Very large vector collections (billions of vectors).
- Distributed, managed-style deployments with Kubernetes.
- Teams that want Milvus Lite for local dev and Milvus for production.

## Resources

- [Milvus website](https://milvus.io/)
- [Milvus GitHub](https://github.com/milvus-io/milvus)
- [Milvus documentation](https://milvus.io/docs/overview.md)
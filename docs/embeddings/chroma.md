---
title: Chroma
layout: default
parent: Embeddings and vector databases
grand_parent: Tools
---

# Chroma

Chroma is an embedded, developer-friendly vector database designed to get a RAG prototype up and running in minutes. It runs in-process like SQLite, with no server to manage for development.

## Overview

- **Language**: Python and Rust
- **License**: Apache 2.0
- **Developer**: Chroma (open source)
- **Status**: active; ideal for prototyping, maturing for production

## Key features

- **Embedded defaults**: `chromadb` in-process store and a lightweight client-server mode for production.
- **Simple API**: `client.get_collection(name).add(ids, documents)` / `.query()`.
- **Automatic embeddings**: bundled default embedding function.
- **Metadata filtering**: query by metadata alongside vector similarity.
- **Multi-modal**: supports text and image documents.
- **Persistent storage**: cheap and durable local persistence.

## Best for

- Prototyping RAG quickly before committing to a heavier database.
- Embedded/local docs tools and small apps.
- Educational use and demos of retrieval.

## Resources

- [Chroma website](https://www.trychroma.com/)
- [Chroma GitHub](https://github.com/chroma-core/chroma)
- [Chroma documentation](https://docs.trychroma.com/)
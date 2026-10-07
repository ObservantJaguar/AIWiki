---
title: LlamaIndex
layout: default
parent: Agent frameworks
grand_parent: Tools
---

# LlamaIndex

LlamaIndex is a data-centric framework for building RAG and document-grounded LLM applications. It focuses on indexing, retrieving and querying your own data — documents, databases and APIs — with strong control over each stage.

## Overview

- **Language**: Python and TypeScript
- **License**: MIT
- **Developer**: LlamaIndex (open source)
- **Status**: mature, popular for RAG-heavy work

## Key features

- **Document loaders**: connectors for files, PDFs, DBs, Notion, Slack and more.
- **Indexing**: splits and indexes documents into nodes with embeddings.
- **Retrieval**: vector, keyword, hybrid and query-level retrieval with reranking.
- **Query engines**: abstraction between raw retrieval and a final LLM answer.
- **Agents**: minimal LLM agent abstractions over tools and data.
- **Fine-grained control**: choose retrieval strategy and prompt per use case.

## Best for

- Building robust, document-grounded RAG pipelines.
- Projects where data source variety and retrieval quality are the focus.
- Teams wanting a cleaner separation between data and model concerns than more general frameworks.

## Resources

- [LlamaIndex website](https://www.llamaindex.ai/)
- [LlamaIndex GitHub](https://github.com/run-llama/llama_index)
- [LlamaIndex docs](https://docs.llamaindex.ai/)
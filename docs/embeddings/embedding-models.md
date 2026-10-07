---
title: Sentence embeddings and transformers
layout: default
parent: Embeddings and vector databases
grand_parent: Tools
---

# Sentence embeddings (sentence-transformers)

Sentence-transformers turns text into dense vector embeddings — fixed-size vectors where similar texts are close together. These embeddings are what vector databases index and search, and the library is the de-facto standard for producing them.

## Overview

- **Language**: Python (PyTorch)
- **License**: Apache 2.0
- **Developer**: UKPLab (University of Frankfurt)
- **Status**: mature, widely used

## Key features

- **Encoder models**: BERT/RoBERTa and modern giant models (GTE, E5, BGE, Nomic).
- **Sentence-level embeddings**: pools token outputs into a single vector.
- **Efficient and optimized**: ONNX and OpenVINO runtime options, fast batching for bulk embedding.
- **Clean API**: `SentenceTransformer("model-name")` → `encode(texts)`.
- **Fully open**: models hosted on Hugging Face, self-hostable.

## Embedding dimensions

- Output size varies by model architecture, typically 384 to 1024+ dimensions.
- The dimension choice affects storage, speed and quality; pick to match your vector DB and recall needs.

## Best for

- Building the embedding layer of a RAG pipeline.
- Semantic search over documents, questions and code.
- Clustering and deduplication of text.

## Resources

- [sentence-transformers website](https://sbert.net/)
- [sentence-transformers GitHub](https://github.com/UKPLab/sentence-transformers)
- [Hugging Face sentence-transformers leaderboard](https://huggingface.co/spaces/mteb/leaderboard)
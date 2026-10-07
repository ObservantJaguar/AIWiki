---
title: Build a RAG application
layout: default
parent: Guides
grand_parent: Practice
nav_order: 3
---

# Build a RAG application

Retrieval-augmented generation (RAG) grounds an LLM's answers in your own documents: relevant chunks are retrieved from a vector database and passed to the model along with the question. This guide builds a minimal working RAG pipeline.

## How RAG works

```text
documents -> chunk -> embed -> store (vector DB)
                                            |
question  -> embed -> retrieve top-k -------+
                                            |
prompt = question + retrieved chunks -> LLM -> answer
```

## Step 1 — Install dependencies

```bash
pip install sentence-transformers chromadb llama-index
```

We use LlamaIndex for brevity, but the concepts apply to any stack.

## Step 2 — Load and index your documents

```python
from llama_index.core import VectorStoreIndex, SimpleDirectoryReader

docs = SimpleDirectoryReader("path/to/docs").load_data()
index = VectorStoreIndex.from_documents(docs)
```

This chunks the documents, embeds each chunk and stores the vectors in an in-memory vector store.

## Step 3 — Query the index

```python
query_engine = index.as_query_engine()
response = query_engine.query("What is the refund policy?")
print(response)
```

By default LlamaIndex uses an OpenAI model for generation — or configure a local model (below).

## Step 4 — Use a completely local stack

To avoid any API call, use a local embedding model and a local LLM:

```python
from llama_index.embeddings.huggingface import HuggingFaceEmbedding
from llama_index.llms.ollama import Ollama

index = VectorStoreIndex.from_documents(
    docs,
    embed_model=HuggingFaceEmbedding(model_name="BAAI/bge-small-en-v1.5"),
)

query_engine = index.as_query_engine(
    llm=Ollama(model="llama3.2", request_timeout=120.0)
)
response = query_engine.query("Summarize the key points.")
```

## Step 5 — Persist to a real vector DB

For production, swap the in-memory store for a durable vector database such as Qdrant or pgvector:

```python
from llama_index.vector_stores.qdrant import QdrantVectorStore
import qdrant_client

client = qdrant_client.QdrantClient(url="http://localhost:6333")
store = QdrantVectorStore(client=client, collection_name="my_docs")
index = VectorStoreIndex.from_vector_store(store)
```

## Best practices

- Chunk size matters: 300-800 tokens with overlap works well for most docs.
- Retrieve 4-10 chunks and pass them with the original question.
- Add metadata filters (source, date) for precise, debuggable retrieval.

## What's next

- Read the [vector database pages](../embeddings/index.html) to compare stores.
- See [hallucination](../theory/safety/hallucination.html) for why grounding helps.

## References

- [LlamaIndex docs](https://docs.llamaindex.ai/)
- [Qdrant](https://qdrant.tech/)
- [Hugging Face embeddings](https://huggingface.co/spaces/mteb/leaderboard)
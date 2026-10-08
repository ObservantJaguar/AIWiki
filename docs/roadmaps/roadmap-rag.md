---
title: Build a RAG assistant
layout: default
parent: Roadmaps
grand_parent: Practice
nav_order: 4
---

# Roadmap: build a RAG assistant on your own data

**Goal:** give a language model access to your documents so it answers from *your* knowledge, with citations, instead of guessing. This is called Retrieval-Augmented Generation (RAG).

For the concept, see the [RAG guide](/guides/guide-rag.html); for tool choices, see the [embeddings section](/embeddings/). You can build RAG entirely self-hosted, or mixed with a provider — this roadmap shows the fully local path, then the provider shortcut.

## Step 0 — Understand the pipeline

```text
documents -> chunk -> embed -> store in vector DB
                                        |
question  -> embed -> retrieve top-k ---+
                                        |
prompt = question + retrieved chunks -> LLM -> answer
```

Two AI pieces matter: an **embedding model** (turns text into vectors) and an **LLM** (writes the answer). You can self-host both.

## Step 1 — Choose the stack

Fully self-hosted (recommended for this roadmap):

| Component | Self-host option | Provider option |
|---|---|---|
| Embeddings | sentence-transformers (BGE, E5) on your machine | OpenAI/Cohere embeddings API |
| Vector DB | Qdrant, pgvector, Chroma | Pinecone, Weaviate Cloud |
| LLM | Ollama / vLLM local model | OpenAI / Claude / Gemini API |

We'll use **LlamaIndex** as the framework — it hides most of the plumbing.

## Step 2 — Install dependencies

```bash
pip install llama-index
pip install llama-index-llms-ollama
pip install llama-index-embeddings-huggingface
pip install qdrant-client
```

## Step 3 — Start a local LLM and get your documents ready

Ensure a local model is running (from the [local LLM roadmap](roadmap-local-llm.html)):

```bash
ollama run llama3.2   # or keep the server running with: ollama serve
```

Put your documents (PDF, markdown, txt) in a folder, e.g. `/home/me/docs`.

## Step 4 — Index your documents

```python
from llama_index.core import VectorStoreIndex, SimpleDirectoryReader
from llama_index.embeddings.huggingface import HuggingFaceEmbedding

docs = SimpleDirectoryReader("/home/me/docs").load_data()
index = VectorStoreIndex.from_documents(
    docs,
    embed_model=HuggingFaceEmbedding(model_name="BAAI/bge-small-en-v1.5"),
)
```

This chunks the documents, embeds each chunk and stores the vectors in memory.

## Step 5 — Query with the local LLM

```python
from llama_index.core import Settings
from llama_index.llms.ollama import Ollama

Settings.llm = Ollama(model="llama3.2", request_timeout=120.0)

query_engine = index.as_query_engine()
response = query_engine.query("What does our policy say about refunds?")
print(response)
```

The answer is now grounded in *your* documents instead of the model's general knowledge.

## Step 6 — Make it durable with Qdrant

In-memory storage is lost on restart. Use Qdrant for persistence:

```bash
docker run -p 6333:6333 -v qdrant_storage:/qdrant/storage qdrant/qdrant
```

```python
import qdrant_client
from llama_index.vector_stores.qdrant import QdrantVectorStore

client = qdrant_client.QdrantClient(url="http://localhost:6333")
store = QdrantVectorStore(client=client, collection_name="my_docs")
index = VectorStoreIndex.from_vector_store(store)
```

Re-embed and `add_to_vector_store` your documents once; then query repeatedly.

## Step 7 — The provider shortcut

If you'd rather not run models, use provider APIs for the same pipeline — just swap the embedding and LLM:

```python
from llama_index.llms.openai import OpenAI
from llama_index.embeddings.openai import OpenAIEmbedding

Settings.llm = OpenAI(model="gpt-4o-mini")
Settings.embed_model = OpenAIEmbedding(model="text-embedding-3-small")
```

Everything else stays the same. The trade-off: data leaves your machine and you pay per token.

## Best practices

- **Chunk size**: 300-800 tokens with overlap works well for most documents.
- **Retrieve 4-10 chunks** and pass them with the question.
- **Add metadata filters** (source, date) for precise retrieval.
- **Verify answers**: RAG reduces hallucination but does not eliminate it; ask the model to cite sources.

## What's next

- Add agents that can act on the retrieved data: [Agents roadmap](roadmap-agents.html).
- Run a heavier model via [production roadmap](roadmap-production.html).

## Theory needed (read separately)

- [Sentence embeddings](/embeddings/embedding-models.html)
- [Vector databases overview](/embeddings/)
- [Hallucination and grounding](/theory/safety/hallucination.html)
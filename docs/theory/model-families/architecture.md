---
title: Architecture families
layout: default
parent: Model families and paradigms
grand_parent: Theory
---

# Encoder-only, decoder-only and encoder-decoder architectures

Transformers come in three broad architectural families, each suited to different tasks. The line between them is whether attention sees the whole sequence (bidirectional) or only the past (causal).

## Encoder-only

The encoder reads the whole input at once using **bidirectional** self-attention. Because every token can see every other token, these models produce rich, context-aware representations.

- **Representative**: BERT, RoBERTa, ModernBERT.
- **Best at**: embeddings, classification, retrieval, named-entity recognition.
- **Not** designed for free-form text generation.

## Decoder-only

The decoder uses **causal** (left-to-right) attention and generates text autoregressively, one token at a time. This is the architecture of the modern generative LLM boom.

- **Representative**: GPT-2/3/4, LLaMA, Mistral, Qwen, Gemma.
- **Best at**: text generation, chat, coding, instruction following, agentic tasks.
- **Note**: with the right prompting they also perform classification and retrieval.

## Encoder-decoder

A full encoder-decoder has an encoder that reads the input contextually and a decoder that generates output while attending to the encoder's representation (cross-attention).

- **Representative**: T5, BART, and the original transformer.
- **Best at**: translation, summarization, any mapping from a full input to a generated output.

## Which to choose

```text
Task                        | Suggested family
-----------------------------------------------
Classification / embeddings | encoder-only (BERT)
Free-form generation / chat | decoder-only (GPT / LLaMA)
Translation / summarization | encoder-decoder (T5)
```

## Key features

- Encoder-only = understanding; decoder-only = generation; encoder-decoder = strong sequence-to-sequence.
- Decoder-only models dominate because they unify generation with strong general ability and scale efficiently.

## Resources

- [BERT paper](https://arxiv.org/abs/1810.04805)
- [Exploring the Limits of Transfer Learning (GPT-2)](https://arxiv.org/abs/2005.14165)
- [T5: Exploring the Limits of Transfer Learning (encoder-decoder)](https://arxiv.org/abs/1910.10683)
---
title: Hallucination
layout: default
parent: Ethics and safety
grand_parent: Theory
---

# Hallucination

A hallucination is a model output that is fluent but factually wrong or fabricated. Because LLMs generate the most probable continuation rather than retrieve verified facts, they can confidently state things that are not true.

## Why models hallucinate

- **Next-token prediction**: the model optimizes likelihood, not truth.
- **Missing or conflicting knowledge**: the fact is absent or contradictory in the training data.
- **Prompt pressure**: leading or ambiguous prompts evoke plausible-sounding completions.
- **Stochasticity**: sampling can land on wrong but coherent continuations.

## Kinds of hallucination

- **Factual**: wrong but plausible statements about people, dates, places.
- **Fabricated sources/links**: convincing-looking but nonexistent citations and URLs.
- **Intrinsic vs extrinsic**: wrong relative to the model's own knowledge vs wrong relative to external reality.

## How to measure

- Factuality benchmarks (TruthfulQA, FactScore, RAG truthfulness evals).
- Human- and LLM-judge review of sampled outputs for unverifiable claims.
- Retrieval-grounded settings where answers can be checked against documents.

## Practical mitigations

- **Retrieval-augmented generation (RAG)**: ground answers in retrieved documents (see [the RAG guide](../../guides/guide-rag.html)).
- **Grounding and citations**: instruct the model to cite; verify manually or programmatically.
- **Temperature control**: lower sampling temperature reduces random fabrication.
- **Confidence signaling**: teach models to hedge or refuse when unsure.
- **Post-hoc verification**: search or validate claims and sources.

## Key features

- Hallucination is inherent to generative models, not a bug that can be fully removed.
- RAG and grounding are the most effective practical mitigations.
- Monitoring and human review remain necessary for high-stakes uses.

## Resources

- [Survey of Hallucination in Natural Language Generation](https://arxiv.org/abs/2202.03629)
- [TruthfulQA paper](https://arxiv.org/abs/2109.07958)
- [Hugging Face: RAG docs](https://www.langchain.com/)
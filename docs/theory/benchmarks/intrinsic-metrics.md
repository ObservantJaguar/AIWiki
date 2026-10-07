---
title: Intrinsic metrics
layout: default
parent: Benchmarks and evaluation
grand_parent: Theory
---

# Intrinsic metrics

Before judging a model on a test suite, there are intrinsic, task-agnostic metrics that quantify how well the model models the data distribution. The most important is **perplexity**.

## Perplexity

Perplexity measures how surprised a language model is by a sequence of tokens — the model's effective branching factor in terms of the probability it assigns to the data.

```text
perplexity = exp( average cross-entropy over the sequence )
```

- **Lower is better**: a perplexity of 1 means perfect prediction; a uniform 10-option choice gives perplexity 10.
- **Comparable across models and architectures** on the same corpus.
- **Caution**: low perplexity on a corpus does not guarantee good answers — it measures likelihood, not correctness or helpfulness.

## Other intrinsic metrics

- **Cross-entropy loss**: the training loss; related to perplexity.
- **Bits-per-character / bits-per-token**: perplexity expressed per token in bits.
- **Perplexity on held-out text**: the standard way to compare LMs on their modeling ability.

## Limitations

Perplexity cannot tell you whether the model can code, reason or follow instructions. That is what downstream benchmarks and human evaluation are for. It should be read as a complementary signal, not a proxy for quality.

## Key features

- Model-agnostic, cheap to compute on a GPU/CPU.
- Best used for comparing distributions and during training.
- Not a substitute for task-based evaluation.

## Resources

- [Hugging Face: Perplexity of fixed-length models](https://huggingface.co/docs/transformers/perplexity)
- [Language Modeling (Lecture, CMU)](http://www.phontron.com/class/nn4nlp2021/assets/slides/07-language-models.pdf)
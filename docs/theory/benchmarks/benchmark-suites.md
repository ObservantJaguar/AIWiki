---
title: Benchmark suites
layout: default
parent: Benchmarks and evaluation
grand_parent: Theory
---

# Major benchmark suites

Practical LLM comparison is dominated by a set of widely used evaluation suites, each measuring a different capability. Familiarity with these acronyms is essential when reading model cards and leaderboards.

## The big ones

| Benchmark | What it measures | Format |
|---|---|---|
| **MMLU** | broad knowledge across 57 subjects | multiple-choice |
| **HumanEval / MBPP** | code generation | pass@k on function completion |
| **GSM8K / MATH** | mathematical reasoning | word problems |
| **ARC** | science reasoning | multiple-choice |
| **HellaSwag** | commonsense reasoning | next-sentence |
| **TruthfulQA** | truthfulness of claims | generation + judge |
| **BIG-Bench** | many capabilities (subset: BIG-Bench Hard) | varied tasks |
| **IFEval** | instruction following | verifiable constraints |

## How scores are quoted

- **MMLU**: accuracy, usually reported as a percentage (e.g. 88.4). Often evaluated 0-shot or 5-shot.
- **HumanEval**: `pass@k` — the probability that at least one of k sampled solutions passes unit tests; the commonly quoted value is pass@1.
- **Leaderboards**: the Open LLM Leaderboard (archived) and the LMArena Elo leaderboard are popular reference points.

## Caveats when reading benchmarks

- **Contamination**: if the model saw the test set during pretraining, scores are inflated.
- **Prompt sensitivity**: results differ between 0-shot, few-shot and with/without a chain-of-thought prompt.
- **Saturation**: top models now near the ceiling on MMLU, so suites evolve (MMLU-Pro, etc.).
- **HumanEval is small**: 164 problems — noise is real; adjacent code benchmarks matter.

## Key features

- MMLU (knowledge), HumanEval (code), GSM8K (math) anchor most comparisons.
- Benchmarks are imperfect proxies and must be read with contamination and prompt bias in mind.

## Resources

- [MMLU](https://arxiv.org/abs/2009.03300)
- [HumanEval](https://arxiv.org/abs/2107.03374)
- [Hugging Face Open LLM Leaderboard](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard)
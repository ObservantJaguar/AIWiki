---
title: Evaluating LLMs in practice
layout: default
parent: Benchmarks and evaluation
grand_parent: Theory
---

# Evaluating LLMs in practice

Static benchmarks are a starting point, not the final word. Production teams evaluate models with custom evals, human judgment and continuous monitoring, because a good MMLU score does not guarantee good behavior on a specific workload.

## The limits of static benchmarks

- **Distribution shift**: your prompts differ from the benchmark's.
- **Contamination and saturation**: top models cluster at the ceiling.
- **Narrow scope**: benchmarks miss subtle issues such as style, safety and robustness.

## Custom evals

Define a small, labeled set of representative inputs and expected (or rubric-graded) outputs. This is the most reliable way to test whether a model meets *your* requirements.

- **Golden set**: fixed inputs with expected answers.
- **Rubric / LLM-as-judge**: an LLM grades free-form responses against criteria.
- **Assertions**: for code or structured output, check programmatic conditions.

## LLM as judge

Using a strong model (e.g. GPT-4-class or an open leader model) to evaluate another model's output is now standard. Pros: cheap, scalable, language-aware. Cons: judge bias, self-preference, occasional inconsistency — mitigate with rubrics and several judge runs.

## Human evaluation

For chat style, preference and harm, human raters remain the gold standard. Teams run side-by-side comparisons and ELO-style rankings (as in LMArena).

## Continuous monitoring in production

After deployment, monitor the model like any service: latency, error rate, output length, refusal rate, and sampled review of outputs against a rubric. Regressions can occur without any code change if upstream models update.

## Key features

- Combine static benchmarks with task-specific evals and human review.
- LLM-as-judge scales evaluation but needs careful rubric design.
- Production evaluation is a process, not a one-off score.

## Resources

- [OpenAI Evals](https://github.com/openai/evals)
- [LMArena (formerly LMSYS Chatbot Arena)](https://lmarena.ai/)
- [Hugging Face: LightEval](https://github.com/huggingface/lighteval)
---
title: Jailbreaks
layout: default
parent: Ethics and safety
grand_parent: Theory
---

# Jailbreaking

A jailbreak is a prompt or technique that causes a model to bypass its safety and alignment guardrails and produce content it was trained to refuse. It is a factual, actively researched phenomenon on both sides — attackers and defenders.

## How jailbreaks work

Safety-tuned models are trained to refuse certain categories of requests. Jailbreaks find ways to evade the refusal mechanism while keeping the model generating. Common vectors:

- **Role/context injection**: asking the model to act as a persona or scenario where refusal rules supposedly do not apply.
- **Encoding and obfuscation**: switching languages, ROT13, base64, or splitting the request into pieces.
- **Indirect instruction**: requesting a summary, script or "creative writing" that implicitly produces the disallowed content.
- **Nested prompting**: chain-of-thought style decomposition that hides the final intent.

## Non-text and indirect attacks

- **Picture/audio injection**: hidden instructions in images or other modalities (indirect prompt injection).
- **Prompt injection via content**: unexpected instructions in tool output, documents or web pages the model reads.
- **Weight/adapters**: fine-tuning or malicious LoRA adapters that weaken refusal behavior.

## Defenses

- **Red-teaming**: actively probing models with known and novel jailbreak techniques.
- **Refusal fine-tuning**: continually improving the alignment data.
- **Guardrails and classifiers**: separate input/output moderation layers.
- **Deployment controls**: restricting tool access, sandboxing, least privilege.

## Why it matters

Jailbreaks are a live arms race. New attack families appear regularly, making evaluation, red-teaming and layered defense an ongoing operational requirement rather than a one-time fix.

## Key features

- Jailbreaks exploit alignment gaps, not a single fixable bug.
- Attacks are prompt-based, injection-based and weight-based.
- Defense is iterative: red-teaming + guardrails + monitoring.

## Resources

- [Universal and Transferable Adversarial Attacks (GCG)](https://arxiv.org/abs/2307.15043)
- [Not what you've signed up for: Compromising Real-World LLM-Integrated Applications](https://arxiv.org/abs/2302.12173)
- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
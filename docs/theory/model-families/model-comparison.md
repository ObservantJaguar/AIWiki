---
title: Model comparison table
layout: default
parent: Model families and paradigms
grand_parent: Theory
nav_order: 4
---

# LLM model comparison: open weights vs closed source

A quick-reference table of the most important language model families, sorted by whether their weights are openly available. The key distinction is **open weights** (you can download and run them yourself) versus **closed / proprietary** (accessible only through an API or product).

## Reading the columns

- **Open weights**: the model file can be downloaded and run locally. Note that "open weights" is not the same as OSI open source — many licenses restrict commercial use or redistribution.
- **License**: the actual license of the weights. `Apache-2.0` and `MIT` are OSI-approved; Llama-style and DeepSeek-style community licenses are permissive but not OSI-compliant.
- **Params**: approximate parameter counts of the most notable checkpoints.
- **Context**: the supported context window (in tokens), approximate.

## Open-weight models

| Model | Developer | License | Params | Context | Notes |
|---|---|---|---|---|---|
| LLaMA 3 / 3.1 | Meta | Llama Community License (not OSI) | 8B, 70B, 405B | 8K-128K | Flagship open family; strong general and instruct models |
| Llama 3.2 | Meta | Llama Community License | 1B, 3B, 11B, 90B | 128K | Newer iteration; includes small edge + vision models |
| Mistral 7B / 8x7B | Mistral AI | Apache-2.0 | 7B, 46.7B (MoE) | 32K | Efficient, strong; popular for local use |
| Mistral Small / Medium | Mistral AI | Apache-2.0 | 22B, 123B | 32K | Larger Mistral checkpoints |
| Qwen 2.5 | Alibaba | Apache-2.0 | 0.5B-72B | 32K-128K | Broad multilingual family incl. coding and math variants |
| Gemma 2 / 3 | Google | Gemma License (not OSI) | 2B-27B | 8K-128K | Google's open-weight family |
| DeepSeek V3 / R1 | DeepSeek | DeepSeek License (not OSI) | 67B, 671B (MoE) | 128K | Strong open reasoning models; R1 trained with RL |
| Phi-3 / Phi-4 | Microsoft | MIT | 3.8B-14B | 4K-128K | Compact, capable small models |
| Falcon | TII | Apache-2.0 | 7B, 40B, 180B | 4K-32K | Open family from the Technology Innovation Institute |
| Grok-1 | xAI | Apache-2.0 | 314B | 8K | Open-weight release of the initial Grok model (older generation) |
| DBRX | Databricks | Databricks Open Model License | 132B (MoE) | 32K | Mixture-of-experts open model |
| OLMo | AI2 | Apache-2.0 | 1B-7B | 2K-4K | Fully open (weights + data + code); research-focused |

## Closed / proprietary models (API only)

| Model | Developer | Availability | Notes |
|---|---|---|---|
| GPT-4 / GPT-4o / GPT-4 Turbo | OpenAI | API / product | Flagship closed model family; multimodal in recent versions |
| o1 / o3 | OpenAI | API / product | Reasoning-focused closed models (extended "thinking") |
| Claude 3 / 3.5 / 4 | Anthropic | API / product | Strong closed model family, emphasis on safety |
| Gemini 1.5 / 2.0 | Google | API / product | Multimodal closed family |
| Grok 3 | xAI | API / product | Closed flagship; late 2025 |
| Midjourney | Midjourney | product | Closed image generator (included for context) |
| Stable Diffusion 3 | Stability AI | Open weights (non-OSI) | Image; included as a widely-known diffusion model |

## Key takeaways

- **Open weights** gives you ownership, auditability and offline use, but "open" can still mean a restrictive license — always check the terms.
- **Closed / proprietary** models are typically the most capable at a given time, but you depend on an external API, its pricing and its data policies.
- For self-hosting, focus on the open-weight line; see the [LLM servers](/llm-servers/) and [guides](/guides/) sections to run them yourself.
- Caution: model landscape changes quickly. Verify current licenses and sizes on the official pages below.

## Resources

- [Hugging Face model search (filter by license)](https://huggingface.co/models)
- [Hugging Face Open LLM Leaderboard](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard)
- [AI Openness and licensing (Wikipedia)](https://en.wikipedia.org/wiki/Open_weights)
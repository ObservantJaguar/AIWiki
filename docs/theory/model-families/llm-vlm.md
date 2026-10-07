---
title: LLM / VLM / diffusion
layout: default
parent: Model families and paradigms
grand_parent: Theory
---

# LLM, VLM, diffusion and multimodal models

Modern models are classified as much by what they generate as by their architecture. This page distinguishes large language models, vision-language models, diffusion models and multimodal systems.

## LLM (large language model)

An LLM is a large neural network trained on massive text corpora to predict the next token. The dominant implementation is a decoder-only transformer. Key properties:

- **Parameters**: typically 1B to 100B+; e.g. LLaMA 2 70B, Mistral 7B, Qwen-14B.
- **Context window**: the number of tokens of context, from 4K to 100K+.
- **Generation**: autoregressive — one token at a time, feeding the output back as input.

## VLM (vision-language model)

A VLM handles both images and text — commonly by aligning an image encoder with a language model. Examples include LLaVA, and the vision variants of proprietary models (GPT-4V). They support image captioning, visual question answering and image-grounded chat.

## Diffusion models

Diffusion models generate data by learning to reverse a noise-adding process. They dominate **image and video generation**:

- **Denoising process**: start from pure noise, iteratively remove it to reveal an image.
- **Latent diffusion**: operate in a compressed latent space to save memory (Stable Diffusion).
- **Conditioning**: text, images or other signals steer generation.
- **Video and audio**: the same paradigm extends to video (Sora-like) and audio generation.

## Multimodal models

Multimodal models accept several input modalities (text, image, audio, video) and sometimes produce several. They are built by:

- **Cross-attention**: a language model attends over the inputs of another modality.
- **Alignment / fine-tuning**: connecting a pretrained vision or audio tower to a frozen LLM.

## Comparing by output

| Family | Input | Output | Typical use |
|---|---|---|---|
| LLM | text | text | chat, coding, agents |
| VLM | text + image | text | captioning, VQA |
| Diffusion | text / image | image / video / audio | generation |
| TTS / ASR | text / audio | audio / text | speech |

## Key features

- Decoder-only transformers power most LLMs today.
- Diffusion is the standard for visual generation.
- Multimodal alignment is an active research frontier.

## Resources

- [Hugging Face: Transformers models overview](https://huggingface.co/docs/transformers/index)
- [Stable Diffusion paper (Latent Diffusion)](https://arxiv.org/abs/2112.10752)
- [LLaVA: Large Language and Vision Assistant](https://arxiv.org/abs/2304.08485)
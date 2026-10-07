---
title: Stable Diffusion
layout: default
parent: Multimodal generation
grand_parent: Tools
---

# Stable Diffusion

Stable Diffusion is the open-source family of latent diffusion models for text-to-image generation. Released by Stability AI, it made high-quality image generation freely runnable on a single consumer GPU, spawning an enormous ecosystem.

## Overview

- **Type**: text-to-image machine-learning model (open-source weights)
- **License**: CreativeML Open RAIL variants (non-OSI, permissive with clauses)
- **Developer**: Stability AI / CompVis / Runway
- **Status**: mature, with SD1.5, SDXL, SD3 and community forks

## How it works

Latent diffusion adds and removes noise in a compressed latent space instead of pixels, dramatically cutting compute. A text encoder (CLIP) conditions the denoiser on the prompt.

## Key features

- **Text-to-image**: generate images from an English prompt.
- **Image-to-image**: redraw/inpaint from an input image.
- **ControlNet and LoRA**: add structural control and style adapters.
- **Run locally**: needs roughly 6-12 GB VRAM for SDXL-class models.
- **Ecosystem**: countless checkpoints, fine-tunes and web UIs.

## Web UIs

- **ComfyUI** — node-based, powerful, popular with creators (see [ComfyUI](comfyui.html)).
- **AUTOMATIC1111** — feature-rich classic web UI (see [AUTOMATIC1111](a1111.html)).
- **Fooocus** — simplified one-click, GPT-style prompt box.

## Resources

- [Stable Diffusion official site](https://stability.ai/)
- [Latent Diffusion paper](https://arxiv.org/abs/2112.10752)
- [Hugging Face diffusers](https://github.com/huggingface/diffusers)
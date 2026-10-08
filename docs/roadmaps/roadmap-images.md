---
title: Generate images
layout: default
parent: Roadmaps
grand_parent: Practice
nav_order: 5
---

# Roadmap: generate images

**Goal:** generate images from a text prompt on your own GPU, or via a cloud provider, whichever fits — and get a real result you can use.

This is the self-host path with ComfyUI and Stable Diffusion/Flux, plus the provider shortcut. See the [ComfyUI page](/multimodal/comfyui.html) and the [Stable Diffusion page](/multimodal/stable-diffusion.html) and the [image guide](/guides/guide-sd.html) for depth.

## Decision first: self-host or provider?

| | Self-host (ComfyUI + SD/Flux) | Provider (Midjourney, DALL-E, etc.) |
|---|---|---|
| Cost | Your GPU + electricity | Subscription or per-image credit |
| Privacy | Images stay local | Images uploaded to a service |
| Control | Full: you can fine-tune, use LoRA, batch | Little control |
| Quality | Very high with Flux/SDXL | Very high, often more polished |
| Setup | Medium | Low (sign up and start) |

Start with the provider if you just want images fast; self-host for control, privacy and volume.

## Self-host path: ComfyUI

### Step 1 — Install ComfyUI

```bash
git clone https://github.com/comfyanonymous/ComfyUI.git
cd ComfyUI
pip install -r requirements.txt
```

### Step 2 — Add a checkpoint model

Download a `.safetensors` checkpoint (e.g. an SD 1.5, SDXL or Flux model) and place it in:

```text
ComfyUI/models/checkpoints/
```

### Step 3 — Launch and open the UI

```bash
python main.py
```

Open `http://127.0.0.1:8188` in your browser.

### Step 4 — Build a minimal workflow

Connect these nodes: **Load Checkpoint** → **CLIP Text Encode (Prompt)** (your prompt + a negative prompt node) → **Empty Latent Image** → **KSampler** (cfg ~7, steps 20-30) → **VAE Decode** → **Save Image**. Press **Queue Prompt**.

The image appears in `ComfyUI/output/`.

### Step 5 — Improve your results

- Write descriptive prompts: subject, style, lighting, quality tags.
- Use a solid negative prompt: `blurry, bad anatomy, low quality`.
- Try community LoRA adapters for style or character consistency.
- Use ControlNet nodes for precise structural control.

### Step 6 — Automate (optional)

ComfyUI workflows are JSON: export a workflow and re-run it headless:

```bash
python main.py --workflow my_workflow.json --output-directory ./out
```

## Provider shortcut

Use a cloud image service (Midjourney, DALL-E, ideogram, etc.):

1. Sign up on the provider's site.
2. Enter a prompt.
3. Iterate: adjust the prompt, use variations, upscale.

Faster to start, but images leave your machine and each generation costs credits.

## Troubleshooting

- **Out of memory**: use a smaller resolution (512x512 for SD 1.5) or a lighter model.
- **Slow**: GPU offload may be off; enable it in settings or use a smaller model.
- **Black/garbage images**: check the negative prompt and CFG scale.

## What's next

- Combine with RAG-style workflows or agents that generate and iterate on images.
- Fine-tune a style with LoRA ([fine-tuning](/finetuning/)).

## Theory needed (read separately)

- [Diffusion models](/theory/model-families/llm-vlm.html)
- [Stable Diffusion architecture](/multimodal/stable-diffusion.html)
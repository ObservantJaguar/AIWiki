---
title: Generate images with Stable Diffusion
layout: default
parent: Guides
grand_parent: Practice
nav_order: 5
---

# Generate images with Stable Diffusion

This guide generates an image from a text prompt using Stable Diffusion, running locally with ComfyUI — the most flexible open diffusion interface.

## Prerequisites

- A GPU with 6-12 GB VRAM (SD 1.5 needs less, SDXL more); CPU-only is possible but slow.
- A Stable Diffusion checkpoint (model) downloaded from Civitai or Hugging Face.

## Step 1 — Install ComfyUI

Clone the repository and install dependencies:

```bash
git clone https://github.com/comfyanonymous/ComfyUI.git
cd ComfyUI
pip install -r requirements.txt
```

## Step 2 — Add a checkpoint model

Place a `.safetensors` checkpoint file in:

```text
ComfyUI/models/checkpoints/
```

Download one (e.g. an SD 1.5 or SDXL model) from Hugging Face or Civitai.

## Step 3 — Launch ComfyUI

```bash
python main.py
```

Open `http://127.0.0.1:8188` in a browser. You will see the node-based workflow editor.

## Step 4 — Build a basic workflow

A minimal text-to-image graph needs four nodes:

1. **Load Checkpoint** → select your model.
2. **CLIP Text Encode (Prompt)** → type your prompt; add a second node for negative prompt.
3. **Empty Latent Image** → set width/height/batch (e.g. 512x512).
4. **KSampler** → connect checkpoint, positive, negative and latent; pick a sampler and `cfg` (~7).
5. **VAE Decode** → connect the sampler output.
6. **Save Image** → connect the decoded image.

Press **Queue Prompt** to generate. The image appears in `ComfyUI/output/`.

## Step 5 — Tips for better results

- Write descriptive prompts with subject, style, lighting and quality tags.
- Use a negative prompt: `blurry, bad anatomy, low quality`.
- Raise the sampler steps to 20-30 for crisper output.
- Use ControlNet or LoRA adapters for structure and style control.

## What's next

- Read the [ComfyUI page](../multimodal/comfyui.html) for workflows as code (JSON).
- Try image-to-image or inpainting with the [Stable Diffusion page](../multimodal/stable-diffusion.html).

## References

- [ComfyUI GitHub](https://github.com/comfyanonymous/ComfyUI)
- [ComfyUI docs](https://docs.comfy.org/)
- [Civitai (checkpoints and LoRAs)](https://civitai.com/)
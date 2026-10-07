---
title: Transcribe audio with Whisper
layout: default
parent: Guides
grand_parent: Practice
nav_order: 6
---

# Transcribe audio with Whisper

This guide turns an audio file into text using Whisper, the open-source speech recognition model, running locally for privacy and no per-minute cost.

## Prerequisites

- Python 3.9+.
- `ffmpeg` installed and on PATH (Whisper needs it to read audio files).
- Optional: an NVIDIA GPU or Apple Silicon for faster transcription; CPU works fine.

## Step 1 — Install Whisper

```bash
pip install -U openai-whisper
```

Verify `ffmpeg` is available:

```bash
ffmpeg -version
```

## Step 2 — Transcribe a file

Run the CLI. It downloads the model on first use:

```bash
whisper "meeting.mp3" --model base --language english
```

Outputs a transcript, subtitles and timestamp files next to the input.

## Step 3 — Choose the right model size

| Model | Sizes / VRAM | Speed | Accuracy |
|---|---|---|---|
| `tiny` | ~1 GB | fast | low |
| `base` | ~1 GB | fast | ok |
| `small` | ~2 GB | medium | good |
| `medium` | ~5 GB | slow | better |
| `large` / `large-v3` | ~10 GB | slowest | best |

Use `--model base` for a quick check, `--model medium` or larger for quality.

## Step 4 — Transcribe in Python

```python
import whisper

model = whisper.load_model("base")
result = model.transcribe("meeting.mp3", language="en")

print(result["text"])
for seg in result["segments"]:
    print(f"{seg['start']:.1f}s-{seg['end']:.1f}s: {seg['text']}")
```

## Step 5 — Transcribe faster on CPU

`faster-whisper` (CTranslate2) is noticeably faster and lighter on CPU:

```bash
pip install faster-whisper
```

```python
from faster_whisper import WhisperModel

model = WhisperModel("base", device="cpu", compute_type="int8")
segments, info = model.transcribe("meeting.mp3")
for seg in segments:
    print(f"{seg.start:.1f}s: {seg.text}")
```

## What's next

- Read the [Whisper page](../multimodal/whisper.html) for model details.
- Combine with a meeting-summary pipeline using [RAG](guide-rag.html).

## References

- [OpenAI Whisper GitHub](https://github.com/openai/whisper)
- [faster-whisper GitHub](https://github.com/SYSTRAN/faster-whisper)
- [Whisper paper](https://arxiv.org/abs/2212.04356)
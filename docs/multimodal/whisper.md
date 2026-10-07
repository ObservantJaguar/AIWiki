---
title: Whisper
layout: default
parent: Multimodal generation
grand_parent: Tools
---

# Whisper

Whisper is OpenAI's open-source speech recognition (ASR) model. It transcribes audio to text robustly across many languages, and its open weights make it the standard for self-hosted transcription.

## Overview

- **Type**: open-source automatic speech recognition model
- **License**: MIT (code) / weights freely usable
- **Developer**: OpenAI (open source)
- **Status**: mature; v3 and distillation variants (distil-whisper) available

## Key features

- **Multilingual**: 90+ languages, strong multilingual and English performance.
- **Robust**: handles noisy audio, accents and varied recording conditions well.
- **Model sizes**: tiny, base, small, medium, large — trade size/VRAM for accuracy.
- **Timestamps and translation**: word/segment timestamps; translation to English.
- **Local-first**: runs entirely on your own hardware (CPU or GPU).
- **Faster copies**: distil-whisper and faster-whisper run with much lower latency.

## Best for

- Transcribing meetings, podcasts, video and support calls.
- Building self-hosted subtitling and note-taking pipelines.
- On-prem voice-to-text when data privacy matters.

## Resources

- [OpenAI Whisper GitHub](https://github.com/openai/whisper)
- [faster-whisper (CTranslate2)](https://github.com/SYSTRAN/faster-whisper)
- [Whisper paper](https://arxiv.org/abs/2212.04356)
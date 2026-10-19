---
title: Russian AI services and models
layout: default
parent: Tools
nav_order: 8
---

# Russian AI services and models

A reference of notable AI models and services developed in **Russia**. This section is language-neutral but practical: several Russian models are strong in Russian-language tasks, some are open-weight, and some are API-only with local payment options.

> **About the "Country" signal**: listing where a model comes from is informational, not a rating. You may pick based on jurisdiction trust, language support, data policies or payment convenience — all are legitimate reasons. Always verify current status on official pages.

## Chat and assistant models

| Model / Service | Developer | Access | Notes |
|---|---|---|---|
| **GigaChat** | Sber | Freemium + API (partly open weights) | Multimodal assistant (text, images, audio, code). Strong in Russian, supports English. Models: GigaChat 3.5 Ultra, Lightning, 2 Max/Pro/Lite. API has a free yearly token allowance; payment in rubles |
| **Yandex AI** (YandexGPT) | Yandex | Product / API | Chat, search and browser scenarios in the Yandex ecosystem |
| **Alice Pro** | Yandex | Product | Dialogue assistant for text and work queries via the Alice ecosystem |
| **Nicebot** | Russian dev | Freemium | Online chat for Russian text generation and coding tasks |

## Speech and audio

| Model / Service | Developer | Access | Notes |
|---|---|---|---|
| **GigaAM** | Sber | Open weights (MIT), GitHub | Open-source acoustic models for Russian ASR (transcription). Conformer architecture, ~220-240M params. Variants: GigaAM-v1/v2/v3 (v3 pretrained on 700K hours) and GigaAM-Emo (emotion). Stronger than Whisper large-v3 on Russian in some benchmarks. Runs via pip, exports to ONNX |
| **Yandex SpeechKit** | Yandex | API (proprietary) | Popular Russian speech recognition and synthesis platform |
| **SaluteSpeech** | Sber | API / Freemium | Speech-to-text and voice APIs for Russian |

## Image and creative

| Model / Service | Developer | Access | Notes |
|---|---|---|---|
| **Kandinsky** | Sber | Freemium (partly open weights) | One of the most visible Russian image/video generation services |
| **GigaChat image mode** | Sber | Included in GigaChat | Text-to-image and image interpretation inside the chat |

## Open-source Russian highlights

- **GigaAM** — the standout open Russian ASR model (MIT license, GitHub). Transcribes Russian speech locally, supports word-level timestamps and emotion detection, ONNX export for production.
- **GigaChat (weights)** — Sber releases part of its model line as open weights; check current availability.

## Why these matter

- **Russian-language quality**: native models often outperform US/China models on Russian text.
- **Local access**: services and APIs are usable in Russia without VPN or foreign cards; payment in rubles.
- **Open-weight options**: GigaAM gives a fully self-hostable Russian ASR, relevant for privacy-sensitive Russian transcription.

## Self-hosting note

For self-hosting Russian ASR, use [GigaAM](https://github.com/salute-developers/GigaAM). For Russian multimodal chat, use GigaChat API or, where weights are available, deploy them on a local [LLM server](/llm-servers/).

## Resources

- [GigaChat](https://giga.chat/) and [GigaChat API](https://developers.sber.ru/docs/ru/gigachat/api/overview)
- [GigaAM on GitHub](https://github.com/salute-developers/GigaAM)
- [Yandex SpeechKit](https://cloud.yandex.com/en/services/speechkit)
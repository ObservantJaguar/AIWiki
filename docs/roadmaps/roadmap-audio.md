---
title: Transcribe audio and add voice
layout: default
parent: Roadmaps
grand_parent: Practice
nav_order: 6
---

# Roadmap: transcribe audio and add voice

**Goal:** turn audio into text (speech-to-text) and generate speech from text (text-to-speech) — self-hosted or via a provider.

This roadmap covers Whisper for transcription and Bark for speech synthesis, then the provider alternatives. See the [Whisper page](/multimodal/whisper.html), the [Bark page](/multimodal/bark.html) and the [Whisper guide](/guides/guide-whisper.html) for depth.

## Decision: self-host or provider?

| | Self-host (Whisper, Bark) | Provider (OpenAI API, ElevenLabs) |
|---|---|---|
| Cost | Free (your compute) | Per minute/Voiceload subscription |
| Privacy | Audio stays local | Audio uploaded |
| Quality | Very high | Very high |
| Setup | Medium | Low (API key) |

Start self-hosted for privacy and volume; use a provider when you want the simplest start.

## Speech-to-text with Whisper (self-host)

### Step 1 — Install

```bash
pip install -U openai-whisper
```

You also need `ffmpeg` on your PATH (install per your OS package manager).

### Step 2 — Transcribe a file

```bash
whisper "meeting.mp3" --model base --language english
```

Output: transcription text, subtitles and timestamp files next to the audio.

### Step 3 — Pick the model size

| Model | Speed | Accuracy |
|---|---|---|
| `tiny` / `base` | fast | ok |
| `small` | medium | good |
| `medium` | slow | better |
| `large` / `large-v3` | slowest | best |

Use `--model base` for a quick check; `medium` or `large` for quality.

### Step 4 — Transcribe from Python

```python
import whisper
model = whisper.load_model("base")
result = model.transcribe("meeting.mp3", language="en")
print(result["text"])
```

### Step 5 — Faster on CPU

`faster-whisper` (CTranslate2) is much faster on CPU:

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

## Text-to-speech with Bark (self-host)

### Step 1 — Install

```bash
pip install git+https://github.com/suno-ai/bark.git
```

Or via `pip install soundfile` and Hugging Face transformers.

### Step 2 — Generate speech

```python
from bark import SAMPLE_RATE, generate_audio, preload_models
import soundfile as sf

preload_models()
text = "Hello! This is a test of local speech synthesis."
audio_array = generate_audio(text)
sf.write("out.wav", audio_array, SAMPLE_RATE)
```

Play `out.wav` — you have a working local text-to-speech.

## Provider shortcuts

**Transcription (OpenAI Whisper API):**

```python
from openai import OpenAI
client = OpenAI()
with open("meeting.mp3", "rb") as f:
    t = client.audio.transcriptions.create(model="whisper-1", file=f)
print(t.text)
```

**TTS (OpenAI TTS or ElevenLabs):** get an API key and use the provider's endpoint:

```python
from openai import OpenAI
client = OpenAI()
resp = client.audio.speech.create(model="tts-1", voice="alloy", input="Hello!")
resp.stream_to_file("out.mp3")
```

## Best practices

- **Clean audio**: reduce background noise for better Whisper accuracy.
- **Timestamps**: use `--word_timestamps True` for precise segments.
- **Language**: specify the language for Whisper to avoid misdetection.
- **Voice cloning**: only for personal/authorized use; respect consent laws.

## What's next

- Feed transcriptions into a [RAG assistant](roadmap-rag.html) for searchable meeting notes.
- Pair TTS with an [agent](roadmap-agents.html) that talks back.

## Theory needed (read separately)

- [Whisper ASR](/multimodal/whisper.html)
- [Bark audio generation](/multimodal/bark.html)
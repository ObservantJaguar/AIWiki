---
title: Start using an LLM chat
layout: default
parent: Roadmaps
grand_parent: Practice
nav_order: 1
---

# Roadmap: start using an LLM chat

**Goal:** today, without installing anything, get a useful AI assistant working and learn to prompt it well.

This is the beginner path. No terminal, no GPU. When you want to run models yourself, move on to the [local LLM roadmap](roadmap-local-llm.html).

## Step 1 — Pick how you'll use it

You have two choices. Most people start with a chat product; developers often use an API.

| Option | What it is | Best for | Cost |
|---|---|---|---|
| Chat product | Website/app with a chat window | Non-technical users, quick answers | Free tier or subscription |
| API | Programmatic access (OpenAI etc.) | Developers building apps | Pay per token |
| Coder IDE plugin | Code completion inside VS Code etc. | Developers writing code | Free tier or subscription |

Popular chat products (embrace the free trials first): Claude, ChatGPT, Gemini, and open chat apps like Ollama's web UI if you later self-host.

## Step 2 — Sign up and ask your first question

1. Open the provider's site (e.g. claude.ai, chatgpt.com, gemini.google.com).
2. Create a free account.
3. Type a real question in the box, e.g. *"Explain quantum computing to me as if I were 12."*
4. Read the answer. Ask a follow-up to go deeper.

You now have a working AI assistant. That's the whole install step.

## Step 3 — Learn to write effective prompts

A good prompt is specific. Compare:

- Weak: *"Help me with my resume."*
- Strong: *"Rewrite this resume bullet for a software engineer job: 'Worked on databases.' Make it action-oriented, one line, and add a measurable result. Resume: [paste]."*

Rules of thumb:

- **Give context**: who you are, what you need, for whom.
- **Be specific about format**: "as a list", "in 3 sentences", "with code".
- **Provide examples**: show one good answer so it matches the style.
- **Iterate**: treat it as a conversation, correct and refine.
- **Set constraints**: length, tone, level of detail.

## Step 4 — Know its limits

- **It can hallucinate**: invented facts and citations. Verify important claims.
- **No memory between sessions** (unless the app stores history).
- **Knowledge cutoff**: it does not know events after training.
- **Privacy**: everything you type may be stored/training data — do not paste secrets.

## Step 5 — Level up

Once the chat product feels limited, the natural next step is running a model on your own machine. Start with the [local LLM roadmap](roadmap-local-llm.html).

## Theory needed (read separately)

- [What an LLM is](/theory/model-families/llm-vlm.html)
- [Model families](/theory/model-families/architecture.html)
- [Hallucination and how to address it](/theory/safety/hallucination.html)
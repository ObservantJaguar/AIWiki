---
title: Fine-tune a model with LoRA
layout: default
parent: Guides
grand_parent: Practice
nav_order: 4
---

# Fine-tune a model with LoRA

This guide fine-tunes an open language model using LoRA (low-rank adaptation) on your own dataset, on a single consumer GPU. The concept extends to QLoRA (4-bit) for limited VRAM.

## Prerequisites

- An NVIDIA GPU; 16 GB VRAM comfortably handles a 7B model with QLoRA.
- Python 3.10+.
- A small instruction dataset in JSON/JSONL format.

## Step 1 — Prepare your dataset

Create a file `data.jsonl` with instruction examples:

```json
{"instruction": "What is the capital of France?", "output": "Paris."}
{"instruction": "Translate 'hello' to Spanish:", "output": "Hola."}
```

Keep it small to start — a few hundred examples is enough to learn the mechanics.

## Step 2 — Install dependencies

```bash
pip install transformers datasets peft trl accelerate bitsandbytes
```

## Step 3 — Run the fine-tune with TRL's SFTTrainer

```python
from datasets import load_dataset
from transformers import AutoTokenizer, TrainingArguments, BitsAndBytesConfig
from peft import LoraConfig
from trl import SFTTrainer

model_id = "meta-llama/Llama-3.2-3B-Instruct"
dataset = load_dataset("json", data_files="data.jsonl", split="train")

tokenizer = AutoTokenizer.from_pretrained(model_id, trust_remote_code=True)
tokenizer.pad_token = tokenizer.eos_token

bnb_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_quant_type="nf4",
    bnb_4bit_compute_dtype="bfloat16",
)

lora_config = LoraConfig(
    r=16,
    lora_alpha=32,
    target_modules=["q_proj", "v_proj"],
    lora_dropout=0.05,
    bias="none",
)

trainer = SFTTrainer(
    model=model_id,
    tokenizer=tokenizer,
    train_dataset=dataset,
    args=TrainingArguments(
        output_dir="./lora-out",
        per_device_train_batch_size=1,
        gradient_accumulation_steps=4,
        num_train_epochs=1,
        logging_steps=10,
        save_steps=100,
        bf16=True,
        optim="adamw_torch",
    ),
    peft_config=lora_config,
    dataset_text_field="instruction",
    max_seq_length=512,
)

trainer.train()
```

## Step 4 — Merge and save

The result is a small adapter. Merge it back into the base model for standalone use:

```python
from peft import PeftModel
from transformers import AutoModelForCausalLM

model = AutoModelForCausalLM.from_pretrained(model_id)
model = PeftModel.from_pretrained(model, "./lora-out/checkpoint-100")
merged = model.merge_and_unload()
merged.save_pretrained("./merged-model")
tokenizer.save_pretrained("./merged-model")
```

## Step 5 — Test the result

```python
from transformers import pipeline

pipe = pipeline("text-generation", model="./merged-model", tokenizer=tokenizer)
print(pipe("What is the capital of France?", max_new_tokens=50)[0]["generated_text"])
```

## Troubleshooting

- **Out of memory**: reduce `max_seq_length`, batch size, or enable gradient checkpointing.
- **Wrong dtype**: ensure your GPU supports bf16, or switch to float16.

## What's next

- Read the [theory on LoRA](../theory/training/lora.html).
- Compare tooling on the [finetuning page](../finetuning/index.html).

## References

- [Hugging Face PEFT](https://huggingface.co/docs/peft/index)
- [TRL docs](https://huggingface.co/docs/trl/index)
- [QLoRA paper](https://arxiv.org/abs/2305.14314)
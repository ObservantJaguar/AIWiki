---
title: Experiment tracking concepts
layout: default
parent: Observability and experiment tracking
grand_parent: Tools
---

# Experiment tracking concepts

Experiment tracking is the discipline of recording, comparing and reproducing ML experiments. Because small hyperparameter changes can swing results, systematic tracking is what separates rigorous model work from guesswork.

## Core objects

- **Experiment**: a logical group of related runs (e.g. "LoRA vs full fine-tune").
- **Run**: a single execution — one training job with a specific config.
- **Parameters**: hyperparameters (`lr`, `batch_size`, `num_epochs`, dataset).
- **Metrics**: logged numbers over time (training loss, eval loss, accuracy, tokens/sec).
- **Artifacts**: files produced — checkpoints, model weights, plots, tokenizer.

## What to capture

- **Code**: Git commit hash and diff for exact reproducibility.
- **Environment**: library versions, GPU model, CUDA version, seed.
- **Dataset**: dataset version/hash and split.
- **Config**: the full run config, not just the headline hyperparameters.
- **Metrics**: both training-time and evaluation-time, at fixed cadence.

## Reproducibility

Reproducibility is the payoff: with the run's code, data, config and seed recorded, the experiment can be re-run identically. This is what makes fine-tuning loops trustworthy and debuggable.

## Open tools to use

- **MLflow**: self-hosted tracking server (see [MLflow](mlflow.html)).
- **TensorBoard**: lightweight, framework-native metric dashboards.
- **Weights & Biases**: polished proprietary SaaS; open-source alternatives exist.

## Best practices

- Log every run automatically via framework auto-logging.
- Fix random seeds and record them.
- Track data and model versions, not just numbers.
- Compare runs in a shared dashboard, not screenshots.

## Resources

- [MLflow docs](https://mlflow.org/docs/latest/index.html)
- [Hugging Face Trainer logging](https://huggingface.co/docs/transformers/main_classes/callback)
- [TensorBoard](https://www.tensorflow.org/tensorboard)
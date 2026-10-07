---
title: MLflow
layout: default
parent: Observability and experiment tracking
grand_parent: Tools
---

# MLflow

MLflow is an open-source platform for the machine learning lifecycle — experiment tracking, model packaging, model registry and serving. It is the de-facto standard self-hosted experiment tracker.

## Overview

- **Language**: Python (REST API, CLI)
- **License**: Apache 2.0
- **Developer**: Databricks (open source, LF project)
- **Status**: mature, widely deployed

## Key features

- **Tracking**: log runs, parameters, metrics and artifacts to a server you host.
- **UI**: compare runs with charts, tables and Git diffs.
- **Model Registry**: version, annotate and stage models.
- **Serving**: deploy tracked models behind a REST endpoint.
- **Auto-logging**: Integrates with the Hugging Face `Trainer`, PyTorch, and more.
- **Self-hosted**: a single server binary; database-backed.

## Best for

- Recording and comparing fine-tuning and training runs.
- Reproducible, versioned, deployable model artifacts.
- Teams that want an open alternative to proprietary trackers.

## Resources

- [MLflow website](https://mlflow.org/)
- [MLflow GitHub](https://github.com/mlflow/mlflow)
- [MLflow docs: Tracking](https://mlflow.org/docs/latest/tracking.html)
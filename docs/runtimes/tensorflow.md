---
title: TensorFlow
layout: default
parent: Runtimes and frameworks
grand_parent: Tools
---

# TensorFlow

TensorFlow is Google's deep learning framework, historically the most used in production ML, with a large legacy ecosystem. Although PyTorch dominates modern LLM work, TensorFlow remains relevant for deployed models, TFX pipelines and Keras users.

## Overview

- **Language**: Python (with a C++ core)
- **License**: Apache 2.0
- **Developer**: Google
- **Status**: mature, large installed base, slower-moving for new models

## Key features

- **Eager execution** now the default, alongside graph-based `tf.function` for performance.
- **TensorFlow Serving**: production model serving with gRPC and REST.
- **TFX**: end-to-end production ML pipelines.
- **Keras**: high-level, now the standard TF user API.
- **Keras applications**: pretrained models for computer vision and more.
- **TPU support**: first-class TPU training.

## Best for

- Existing production Python/C++/Java/Go ML stacks.
- Teams standardized on Keras for tabular or vision models.
- Deploying and serving stable models at scale.

## Resources

- [TensorFlow website](https://www.tensorflow.org/)
- [TensorFlow GitHub](https://github.com/tensorflow/tensorflow)
- [TensorFlow Serving](https://www.tensorflow.org/tfx/guide/serving)
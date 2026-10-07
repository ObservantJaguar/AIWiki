---
title: Bias
layout: default
parent: Ethics and safety
grand_parent: Theory
---

# Bias

Models trained on human-created data absorb statistical patterns from that data, including stereotypes and representational biases. Bias in AI is a factual, measurable phenomenon that practitioners must understand and mitigate.

## Where bias comes from

- **Training data**: text corpora reflect historical and social patterns, including stereotypes about gender, race, profession and more.
- **Labeling bias**: human annotators and reward models bring their own judgments.
- **Deployment context**: even unbiased base behavior can amplify bias when applied in unequal ways.

## Kinds of bias

- **Representational**: the model associates certain roles or attributes with certain groups.
- **Selection bias**: some groups are underrepresented in the training data, degrading performance for them.
- **Language bias**: favoring or defaulting to high-resource languages.
- **Evaluation bias**: tests that reward majority patterns over generalization.

## How to measure

- Bias benchmark datasets and probes (e.g. Winogender, StereoSet).
- Differential performance measurement across demographic groups.
- Audits of outputs for stereotypical associations.

## Mitigations

- **Data curation**: rebalancing and filtering training corpora.
- **Debiasing fine-tuning**: training or RLHF that reduces stereotypical associations.
- **Evaluation gates**: requiring bias checks before deployment.
- **Process controls**: human review, transparency about model limits, application-specific guardrails.

## Key features

- Bias is a property of the data and training, not an accidental glitch.
- It cannot be eliminated entirely; it is managed with data, training and process.
- Measurement and disclosure are the foundations of responsible deployment.

## Resources

- [Winogender / WinoBias benchmarks](https://huggingface.co/datasets/winovae/winogender)
- [Mitigating Gender Bias in Captioning Systems](https://arxiv.org/abs/1906.01209)
- [Reporting Guidelines for the Gender of People](https://arxiv.org/abs/2106.07863)
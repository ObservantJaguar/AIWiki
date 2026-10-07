---
title: The learning pipeline
layout: default
parent: ML/DL fundamentals
grand_parent: Theory
---

# The learning pipeline

Training a neural network is a repeatable pipeline of data loading, forward pass, loss computation, backpropagation and parameter update. Understanding the pipeline makes the rest of the wiki concrete.

## The pipeline steps

1. **Dataset split**: partition data into train, validation and test sets. The model never learns from the test set.
2. **Batching**: shuffle the data and feed it in mini-batches of a chosen size.
3. **Forward pass**: propagate each batch through the network to produce predictions.
4. **Loss computation**: compare predictions with labels using a loss function (cross-entropy for classification, MSE for regression).
5. **Backpropagation**: compute the gradient of the loss with respect to every parameter.
6. **Optimizer step**: update parameters (e.g. with Adam or SGD).
7. **Epoch**: one full pass over the training set; repeat for many epochs.

## Overfitting and regularization

Overfitting means the model memorizes the training data instead of generalizing. Common countermeasures:

- **Dropout**: randomly zero out neurons during training.
- **Weight decay**: penalize large weights (L2 regularization).
- **Early stopping**: stop when validation loss stops improving.
- **Data augmentation**: increase data variety, common in vision.
- **Cross-validation**: more robust estimates of generalization.

## Training, validation, test

- **Training set**: adjusts the parameters.
- **Validation set**: tuning hyperparameters and detecting overfitting.
- **Test set**: final, unbiased evaluation of generalization.

## Key features

- Iterative and empirical: much of deep learning practice is tuning this loop.
- Distributed variants (data parallelism, pipeline parallelism) scale it across GPUs.

## Resources

- [PyTorch: Training a classifier](https://pytorch.org/tutorials/beginner/blitz/cifar10_tutorial.html)
- [Scikit-learn: Train/Test/Validation](https://scikit-learn.org/stable/modules/cross_validation.html)
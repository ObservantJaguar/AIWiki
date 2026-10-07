---
title: Neurons and layers
layout: default
parent: ML/DL fundamentals
grand_parent: Theory
---

# Neurons and layers

A neural network is a composition of simple computational units called **neurons**, organized into **layers**. Each neuron computes a weighted sum of its inputs and applies a non-linearity before passing the result onward.

## Key concepts

- **Perceptron**: the simplest neuron — a weighted sum of inputs plus a bias, passed through a step function. The basis of early single-layer classifiers.
- **Weights and biases**: the trainable parameters of the network. Weight `w_i` scales input `x_i`; the bias shifts the decision boundary.
- **Layers**: an input layer, one or more hidden layers, and an output layer. Each layer is a collection of neurons.
- **Fully connected (dense) layer**: every neuron connects to every neuron of the previous layer.
- **Depth**: the number of hidden layers. "Deep" learning refers to networks with many layers, which can learn hierarchical features.

## Forward pass

For a neuron with inputs `x = (x_1, ..., x_n)`, weights `w`, bias `b` and activation `f`:

```text
z = (w_1 * x_1) + (w_2 * x_2) + ... + (w_n * x_n) + b
a = f(z)
```

## Why non-linearity matters

If layers were only weighted sums, the whole network would collapse into a single linear function regardless of depth. Non-linear activations give the network the ability to approximate arbitrary functions — the universal approximation property.

## Key features

- Composable: any number of layers, any connection pattern.
- Parameters are learned end-to-end via backpropagation.
- Modern architectures add specialized layers: convolutional, attention, normalization.

## Resources

- [3Blue1Brown: But what is a neural network?](https://www.3blue1brown.com/lessons/neural-networks)
- [Deep Learning (Goodfellow et al.), chapter 6](https://www.deeplearningbook.org/)
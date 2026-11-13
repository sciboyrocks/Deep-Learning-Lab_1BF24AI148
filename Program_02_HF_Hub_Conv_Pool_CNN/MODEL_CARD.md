---
datasets:
- uoft-cs/cifar10
language: en
library_name: pytorch
license: mit
metrics:
- accuracy
tags:
- image-classification
- cnn
- cifar10
- deep-learning-lab
model-index:
- name: cifar10-basic-cnn
  results:
  - task:
      type: image-classification
      name: Image Classification
    dataset:
      name: CIFAR-10
      type: uoft-cs/cifar10
      split: test
    metrics:
    - type: accuracy
      value: 0.8755
      name: Test accuracy
---

# cifar10-basic-cnn

A small VGG-style convolutional neural network (815,018 parameters) trained from scratch on CIFAR-10
as part of Deep Learning Lab Program 2.

## Model description
Three blocks of `[Conv3x3 → BatchNorm → ReLU] x2 → MaxPool2 → Dropout(0.25)` with 32 / 64 / 128 channels,
followed by `Linear(2048, 256) → ReLU → Dropout(0.5) → Linear(256, 10)`. All convolutions use stride 1 and padding 1.

## Intended uses & limitations
* **Intended use:** teaching / demonstration of CNN fundamentals on 32×32 images of the 10 CIFAR-10 classes.
* **Not intended for:** real-world deployment. It only knows 10 classes, expects 32×32 RGB inputs normalised with
  the CIFAR-10 statistics, and will confidently mis-classify anything outside those classes.

## Training data
`uoft-cs/cifar10` from the Hugging Face Hub — 50,000 training images. Inputs normalised with per-channel
mean [0.49140000343322754, 0.4821999967098236, 0.4465000033378601] and std [0.24699999392032623, 0.2434999942779541, 0.26159998774528503].
Augmentation: random 32×32 crop from a 4-pixel reflect-padded image, random horizontal flip.

## Training procedure
* Epochs: 15, batch size 128
* Optimiser: SGD (momentum 0.9, Nesterov, weight decay 5e-4), One-Cycle LR schedule with max LR 0.1
* Loss: cross-entropy with label smoothing 0.1
* Hardware: `mps`, training time 4.9 min

## Evaluation results
Test accuracy on the 10,000-image CIFAR-10 test split: **87.55%**

| Class | Accuracy |
|---|---|
| airplane | 88.6% |
| automobile | 95.0% |
| bird | 78.3% |
| cat | 69.6% |
| deer | 87.5% |
| dog | 84.3% |
| frog | 95.6% |
| horse | 89.8% |
| ship | 93.6% |
| truck | 93.2% |

## Bias, risks and limitations
CIFAR-10 is small, low-resolution and drawn from a narrow distribution of web images; the confusion matrix shows the
model mixes up visually similar classes (e.g. cat/dog, automobile/truck). Results should not be generalised beyond this benchmark.

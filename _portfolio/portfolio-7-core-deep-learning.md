---
title: "Core Deep Learning -- Foundations to Generative Models"
excerpt: >-
  An inspectable PyTorch collection covering neural-network behavior,
  attention-based sequence modeling, BERT extractive question answering, and
  CIFAR-10 image generation with three adversarial objectives.
collection: portfolio
permalink: /portfolio/core-deep-learning/
order: 7
---

Core Deep Learning is a four-part collection that traces model development from
small neural networks and optimization analysis through sequence modeling,
transfer learning, and adversarial image generation. The implementations expose
the training logic and evaluation choices directly, making the collection
useful for studying how architecture, optimization, capacity, and objective
design change model behavior.

<p>
  <a class="btn btn--primary" href="https://github.com/codemith/Deep_Learning">GitHub</a>
  <a class="btn" href="#project-modules">Project Modules</a>
  <a class="btn" href="#recorded-results-and-scope">Results &amp; Scope</a>
</p>

## Project Modules

### 1. Neural Network Foundations

Controlled experiments explore depth and width under similar parameter budgets,
function approximation, MNIST classification, optimization trajectories,
gradient norms, curvature, random-label memorization, model capacity, and
training sensitivity. The notebooks connect observed behavior to PCA
projections of parameter trajectories and Hessian-based curvature analysis.

### 2. Attention-Based Video Captioning

A PyTorch encoder-decoder implementation compresses frame-level video features,
models their temporal sequence with an LSTM, applies learned attention, and
generates captions with an LSTM decoder and scheduled sampling. Separate
training and inference paths cover vocabulary construction, variable-length
caption batches, state-dictionary checkpoints, and caption export.

### 3. BERT Extractive Question Answering

A `bert-base-uncased` model is fine-tuned on Spoken-SQuAD using sliding context
windows, token-to-character span alignment, mixed-precision training, linear
learning-rate scheduling, and extractive answer decoding. The notebook includes
custom Exact Match and token-F1 evaluation plus a standalone inference example.

### 4. CIFAR-10 Generative Modeling

Three notebooks explore complementary adversarial objectives on CIFAR-10:

- Deep Convolutional GAN (DCGAN) with a convolutional generator and
  discriminator
- Auxiliary Classifier GAN (ACGAN) for class-conditioned image generation
- Weight-clipped Wasserstein GAN (WGAN) with multiple critic updates per
  generator step

The experiments expose generated-sample, adversarial-loss, and FID workflows
while illustrating stability tradeoffs among the objectives.

## Technical Highlights

- PyTorch model construction and custom training loops
- MLPs, CNNs, recurrent encoder-decoder models, attention, and transformers
- Function approximation, MNIST classification, and optimization analysis
- PCA parameter-trajectory projections, gradient tracking, and Hessian analysis
- Spoken-SQuAD preprocessing and BERT span prediction
- Conditional and unconditional CIFAR-10 image generation
- Adversarial training with BCE, auxiliary classification, and Wasserstein
  losses

## Recorded Results and Scope

- The notebooks are inspectable experiment artifacts. Their stale execution
  state was removed during repository cleanup, and they were not retrained as
  part of that cleanup.
- The recorded Spoken-SQuAD run processed 37,130 training windows and 5,376
  validation windows over three epochs. Its custom notebook scorer reported
  final Exact Match of 0.5506 and token F1 of 0.6962; these are
  notebook-specific measurements, not official benchmark scores.
- The video-captioning module is retained as a historical implementation. Its
  original dataset, checkpoint, and BLEU helper were not included, so no
  current captioning-performance claim is made.
- The GAN experiments are not presented as a model leaderboard because their
  historical FID implementations and sample counts differ and have not been
  rerun under one corrected protocol.

## Repository Organization

- [Neural Network Foundations](https://github.com/codemith/Deep_Learning/tree/main/01-neural-network-foundations)
- [Attention-Based Video Captioning](https://github.com/codemith/Deep_Learning/tree/main/02-video-captioning-seq2seq)
- [Spoken-SQuAD Extractive QA](https://github.com/codemith/Deep_Learning/tree/main/03-spoken-squad-extractive-qa)
- [CIFAR-10 GAN Experiments](https://github.com/codemith/Deep_Learning/tree/main/04-cifar10-gan-experiments)

---
layout: page
title: Normalized Routing Limits for Pruned Neural Networks
description: NNGP and NTK across density regimes under local retained-fan-in scaling. Forthcoming in PMLR at LoG 2026.
importance: 1
category: Research
related_publications: true
---

### Overview

Pruning removes selected synaptic connections from a neural network, modifying its effective biadjacency structure. As wide neural networks are pruned more aggressively, retained connection density vanishes ($p_n \to 0$). Under standard dense graph limit formulations, raw step graphons collapse to zero in $L^1$, failing to capture that individual neurons continue to aggregate growing, structured neighborhoods.

This work establishes a parameterization-faithful continuum limit for width-growing sparse neural networks under local retained-fan-in scaling ($1/\sqrt{d_i}$). Under this scaling, the network does not see raw adjacency mass; instead, it observes the **row-Markov routing operator** $P = D^{-1}M$, which records the relative allocation of retained inputs entering each neuron.

### Theoretical Contributions

- **Deterministic NNGP & NTK Limits**: For two-hidden-layer networks with independent row-constrained block masks and minimum fan-in growing faster than logarithmically ($k_{\min, n}/\log n \to \infty$), we derive explicit finite-dimensional recursions for the limiting Neural Network Gaussian Process (NNGP) covariance $\Sigma_{\text{NR}}$ and initialization-time Neural Tangent Kernel (NTK) $\Theta_{\text{NR}}$.
- **Forward vs. Backward Transport**: Forward covariance is transported by limiting block routing matrices $B^{(\ell)}$, whereas backward sensitivity is transported by their block-mass adjoints $B^{(\ell)\dagger} = \frac{1}{\pi^{(1)}_b} \sum_a \pi^{(2)}_a B^{(2)}_{ab} U_a$. This orientation difference reflects that forward message passing averages incoming sources, while backpropagation aggregates the load sent from targets back to sources.
- **Gaussian-Conditioning Decoupling**: We resolve the long-standing forward-backward weight reuse problem without invoking heuristic "gradient independence" assumptions. By conditioning second-layer Gaussian weights on the subspace revealed during the forward pass, we prove that sensitivity error is strictly bounded by $\mathcal{O}(m / d_{\min, n}^{(2)})$, identifying $m / d_{\min, n}^{(2)} \to 0$ as the natural scale governing weight reuse as dataset size $m$ grows.
- **Density Invariance**: We prove that mask sequences with matched routing and block proportions yield identical limiting NNGP and NTK objects, regardless of whether density is fixed ($0.2n$), polynomial ($n^{3/4}$), or polylogarithmic ($2(\log n)^2$).

### Empirical Findings

- **Controlled Density Interventions**: With smooth error-function ($\text{erf}$) activations across widths up to $n = 4096$, empirical NNGP and NTK errors approach the predicted population limit with log-log decay slopes near $-1/2$, exhibiting overlapping curves across all density regimes.
- **Routing-Driven Spectral Acceleration**: Holding density, degree, data, and initialization seeds fixed while altering only source allocation shifts the label-relevant NTK gain $\tilde{g}_y$ from $1.35$ (noise-favoring) to $2.61$ (signal-favoring), directly predicting early gradient-flow optimization speed.
- **Stress Tests**: Replicated under unbounded ReLU activations, analyzed finite-fan-in crossover thresholds ($k \ge 16$), and evaluated task-selected saliency masks from Fashion-MNIST SNIP, revealing how learned masks introduce mask-initialization coupling beyond pure routing.

*Accepted to the full proceedings track of the **Learning on Graphs Conference (LoG 2026)**; forthcoming in PMLR (Oct 2026). Preliminary ongoing research presented orally at the **NetSci 2026** NSIA Satellite.*

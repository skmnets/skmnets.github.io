---
layout: page
title: Normalized Routing Limits for Pruned Neural Networks
description: NNGP and NTK limits across density regimes under local retained-fan-in scaling. Forthcoming in PMLR at LoG 2026.
importance: 1
category: Research
related_publications: true
---

### Research Question

When a wide neural network is pruned so aggressively that connection density vanishes ($p_n \to 0$), standard dense graph limits (step graphons) collapse to zero in $L^1$, failing to reflect that individual neurons continue to aggregate growing, structured inputs. What continuum object captures this limiting behavior, and how does pruning govern kernel behavior across density regimes?

### Approach

Under local retained-fan-in normalization ($1/\sqrt{d_i}$), the network does not see raw adjacency mass; instead, it observes a **row-Markov routing operator** $P = D^{-1}M$, which records the relative allocation of retained inputs entering each neuron. The problem is addressed by analyzing two-hidden-layer networks under independent row-constrained block masks with minimum fan-in growing faster than logarithmically ($k_{\min, n}/\log n \to \infty$).

### Main Results

- **Deterministic NNGP and NTK Limits**: We derive finite-dimensional recursions for the limiting Neural Network Gaussian Process (NNGP) covariance $\Sigma_{\text{NR}}$ and initialization-time Neural Tangent Kernel (NTK) $\Theta_{\text{NR}}$, establishing density invariance across fixed ($0.2n$), polynomial ($n^{3/4}$), and polylogarithmic ($2(\log n)^2$) regimes when routing and block proportions are matched.
- **Forward vs. Backward Transport Asymmetry**: Forward covariance is transported by limiting block routing matrices $B^{(\ell)}$, whereas backward sensitivity is governed by block-mass adjoints $B^{(\ell)\dagger} = \frac{1}{\pi^{(1)}_b} \sum_a \pi^{(2)}_a B^{(2)}_{ab} U_a$, reflecting that forward passes average incoming sources while backpropagation aggregates load sent from targets.
- **Gaussian-Conditioning Decoupling**: Conditioning second-layer Gaussian weights on the forward-pass subspace bounds sensitivity error by $\mathcal{O}(m / d_{\min, n}^{(2)})$, establishing that weight-reuse effects vanish as width and dataset size $m$ grow.
- **Spectral Acceleration via Routing**: Altering source allocation while holding density, degree, data, and initialization seeds fixed shifts the label-relevant NTK gain $\tilde{g}_y$ from $1.35$ to $2.61$, directly predicting gradient-flow convergence speed.

### Publication / Status

Accepted at the **Learning on Graphs Conference (LoG 2026)**; forthcoming in the *Proceedings of Machine Learning Research (PMLR)*. Preliminary research presented as a contributed oral talk at the **NetSci 2026** NSIA Satellite.

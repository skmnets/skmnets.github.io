---
layout: page
title: Learning Where to Communicate in GNNs
description: Task-conditioned edge scores, activation-gated adjoints, and cross-size transfer via graph limits. Under review at ICLR 2027.
importance: 3
category: Research
related_publications: true
---

### Overview

Graph neural networks (GNNs) solve problems by communicating along edges. However, standard message-passing architectures treat all structural connections uniformly, which can suppress relevant variation, introduce spurious correlations, or wash out essential task distinctions. Feature similarity and attention weights measure forward representation similarity or aggregation weighting, but neither indicates the signed local change in task loss when a communication route is perturbed.

This project introduces a **task-conditioned edge score** that evaluates whether strengthening or weakening a route locally improves the downstream task objective, and provides a continuous population coordinate system via graph limits to compare and transfer these scores across different graph sizes.

### Theoretical Contributions

- **Explicit Task-Conditioned Score ($S_W$)**: For nonlinear residual message passing with symmetric mean-normalized difference aggregation, we derive the exact task derivative:
  $$S_W(u, v) = \frac{\Delta \tau}{2} \sum_{\ell=0}^{L-1} \underbrace{[h^\ell(u) - h^\ell(v)]^\top}_{\text{forward difference}} \underbrace{[r^\ell(u) - r^\ell(v)]}_{\text{gated task sensitivity}}$$
  where $r^\ell = B_1^\top D\sigma(z^\ell)^\top p^{\ell+1}$ is the backward adjoint sensitivity gated by activation derivatives.
- **Task Alignment Favors Heterophily**: We show that dissimilar populations can usefully exchange information whenever their representation differences align with backward task differences. The score isolates which distinctions serve the task, demonstrating that useful communication is not restricted to homophilous neighbors.
- **Conversion to Population Coordinates**: When embedding discrete matrices $A \in \mathbb{R}^{n \times n}$ into continuous graphons $W_A(u, v)$ over equal-width cells of mass $n^{-2}$, we prove the exact coordinate conversion:
  $$\nabla_A^F J_n(A) = \frac{1}{n^2} G^{(n)}(A)$$
  This factor of $n^2$ converts unscaled entrywise derivatives into a size-invariant population gradient density.
- **Finite-Horizon Topology-Learning Consistency**: We prove that the task-conditioned chain is Lipschitz continuous in $L^2$ norms and that correctly scaled finite topology updates track the continuum population dynamics over fixed horizons, whereas unscaled Euclidean updates vanish at order $\mathcal{O}(n^{-2})$.

### Empirical Findings

- **Gating & Heterophily Controls**: Experiments confirm the exactness of the adjoint gradient (worst-case relative error $8.48 \times 10^{-16}$) and verify that activation saturation ($D\sigma$) attenuates sensitivity. On a constructed relational task where target classes share zero cross-covariance with source features, the score correctly identifies and strengthens heterophilous source-target routes (reducing test MSE from $0.992$ to $0.396$).
- **Cross-Resolution Transfer on METR-LA**: On the 207-sensor METR-LA traffic forecasting benchmark, lifted edge scores computed from independently trained smaller models ($n = 64$ and $n = 128$) guide effective one-step topology interventions on a larger frozen 207-sensor predictor, achieving $83.9\%$ and $90.4\%$ of the native model's gain.
- **Survival Under Budget Constraints**: To test whether the score merely reduces destructive mixing, we evaluate interventions under strict total-mass conservation ($\sum_{i < j} \Delta A_{ij} = 0$) and sensor row-sum conservation ($\sum_{j \neq i} \Delta A_{ij} = 0$). Score-guided interventions consistently outperform distance-stratified nulls and uniform shrinkage across all seeds and constraints, confirming that the score accurately identifies *where* to route information under fixed communication budgets.

*Under review as a conference paper at **ICLR 2027**.*

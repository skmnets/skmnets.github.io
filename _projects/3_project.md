---
layout: page
title: Learning Where to Communicate in GNNs
description: Task-conditioned edge scores, activation-gated adjoints, and cross-size transfer via graph limits. Under review at ICLR 2027.
importance: 3
category: Research
related_publications: true
---

### Question

Given that message-passing architectures treat structural connections uniformly, which communication routes actually reduce downstream task loss, and can edge usefulness be compared or transferred across different graph sizes?

### Key Idea

We define a task-conditioned edge score by differentiating the task loss with respect to continuous message-passing weights, decomposing it into forward representation differences and activation-gated backward adjoint sensitivities, and lift the formulation to graphons as a common population coordinate system.

### Main Results

- **Explicit Task-Conditioned Score ($S_W$)**: For nonlinear residual message passing with symmetric mean-normalized difference aggregation, we derive the exact task derivative:
  $$S_W(u, v) = \frac{\Delta \tau}{2} \sum_{\ell=0}^{L-1} \underbrace{[h^\ell(u) - h^\ell(v)]^\top}_{\text{forward difference}} \underbrace{[r^\ell(u) - r^\ell(v)]}_{\text{gated task sensitivity}}$$
  where $r^\ell = B_1^\top D\sigma(z^\ell)^\top p^{\ell+1}$ is the backward adjoint sensitivity gated by activation derivatives.
- **Task Alignment Favors Heterophily**: Dissimilar populations can usefully exchange information whenever representation differences align with backward task differences, demonstrating that useful communication is not limited to homophilous neighbors.
- **Conversion to Population Coordinates**: Embedding discrete adjacency matrices into continuous graphons over cells of mass $n^{-2}$ yields the exact coordinate conversion:
  $$\nabla_A^F J_n(A) = \frac{1}{n^2} G^{(n)}(A)$$
  This factor converts unscaled entrywise derivatives into a size-invariant population gradient density. We prove finite-horizon consistency of topology learning in $L^2$.
- **Cross-Resolution Transfer on METR-LA**: On the 207-sensor METR-LA traffic forecasting benchmark, lifted edge scores computed from independently trained smaller models ($n = 64$ and $n = 128$) guide effective one-step topology interventions on a larger frozen 207-sensor predictor, achieving $83.9\%$ and $90.4\%$ of native model improvements under strict mass-conservation constraints.

### Publication and Status

*Manuscript under review at ICLR 2027.*

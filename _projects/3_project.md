---
layout: page
title: Learning Where to Communicate in GNNs
description: Task-conditioned edge scores, activation-gated adjoints, and cross-size transfer via graph limits. Under review at ICLR 2027.
importance: 3
category: Research
related_publications: true
---

### Research Question

Graph neural networks move information along edges, but which communication routes actually improve a particular task? A second question is whether such route-level information can be meaningfully compared or transferred across graphs of different resolutions.

### Approach

The problem is addressed through a task-conditioned edge sensitivity derived from the downstream objective. Graph limits provide a common population coordinate system in which these sensitivities can be compared across resolutions.

### Main Results

For nonlinear residual message passing, the edge score is obtained exactly through an adjoint formulation and decomposes into a coupling between forward representation differences and backward task sensitivities. Finite-resolution topology updates are then shown to track the corresponding population dynamics over fixed horizons under the appropriate scaling. Controlled experiments verify the gradient construction, activation gating, and cross-resolution transfer, including interventions on the METR-LA traffic network.

- **Explicit Task-Conditioned Score ($S_W$)**: For nonlinear residual message passing with symmetric mean-normalized difference aggregation, we derive the exact task derivative:
  $$S_W(u, v) = \frac{\Delta \tau}{2} \sum_{\ell=0}^{L-1} \underbrace{[h^\ell(u) - h^\ell(v)]^\top}_{\text{forward difference}} \underbrace{[r^\ell(u) - r^\ell(v)]}_{\text{gated task sensitivity}}$$
  where $r^\ell = B_1^\top D\sigma(z^\ell)^\top p^{\ell+1}$ is the backward adjoint sensitivity gated by activation derivatives.
- **Task Alignment Favors Heterophily**: Dissimilar populations can usefully exchange information whenever representation differences align with backward task differences, demonstrating that useful communication is not limited to homophilous neighbors.
- **Conversion to Population Coordinates**: Embedding discrete adjacency matrices into continuous graphons over cells of mass $n^{-2}$ yields the exact coordinate conversion:
  $$\nabla_A^F J_n(A) = \frac{1}{n^2} G^{(n)}(A)$$
  This factor converts unscaled entrywise derivatives into a size-invariant population gradient density. The analysis proves finite-horizon consistency of topology learning in $L^2$.
- **Cross-Resolution Transfer on METR-LA**: On the 207-sensor METR-LA traffic forecasting benchmark, lifted edge scores computed from independently trained smaller models ($n = 64$ and $n = 128$) guide effective one-step topology interventions on a larger frozen 207-sensor predictor, achieving $83.9\%$ and $90.4\%$ of native model improvements under strict mass-conservation constraints.

### Publication / Status

Manuscript under review at ICLR 2027.

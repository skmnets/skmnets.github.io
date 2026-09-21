---
layout: page
title: Community Information Horizons in Discrete Graph Diffusion
description: Graphon analysis of spectral contraction, size-aware SNR coordinates, and the alignment switch. Forthcoming in PMLR at LoG 2026.
importance: 2
category: Research
related_publications: true
---

### Question

At what noise level does a graph corrupted by discrete edge diffusion cease to identify the community structure that generated it, and how does this recovery boundary depend on graph size versus diffusion time?

### Key Idea

Dense probability graphons provide a continuous state space for discrete binary edge refresh. Under this continuum formulation, structural recoverability is governed by a size-aware signal-to-noise ratio rather than diffusion step alone, connecting discrete Markov corruption directly to population spectral contraction.

### Main Results

- **Exact Graphon Affine Trajectory and Mode Contraction**: Under independent binary edge refresh with schedule $\beta_s$, every dense probability graphon follows the exact affine continuum trajectory $W_t = \rho + \bar{\alpha}_t(W_0 - \rho)$, where $\bar{\alpha}_t = \prod_{s=1}^t (1 - \beta_s)$. Graphon eigenvalues contract as $K_t = \bar{\alpha}_t K_0$ without eigenfunction rotation.
- **Structural Signal-to-Noise Ratio ($z_t$)**: For balanced two-block stochastic block models, we derive the size-aware structural SNR coordinate $z_t = \frac{\bar{\alpha}_t \Delta \sqrt{n}}{\sqrt{p_t(1 - p_t)}}$. This coordinate separates three recovery regimes:
  1. *Weak-detectability horizon ($z_t = 1$)*: Non-trivial partition overlap with the source becomes statistically achievable.
  2. *Consistency boundary ($z_t \to \infty$)*: Normalized probability matrix and oracle-coordinate posterior errors vanish.
  3. *Exact-recovery horizon ($z_t^2 \asymp \log n$)*: Zero misclassified vertices with high probability.
- **Cross-Size Invariance**: Source-partition recovery curves across training sizes $n \in \{128, 256, 512\}$ and test size $n = 1024$ collapse when plotted against $\log z_t$, reducing pairwise interpolation variance by $76.4\%$ compared to indexing by diffusion time.
- **The Alignment Switch**: Above the horizon ($z_t \ge 2$), reverse diffusion chains reconstruct the planted source partition. Near and below $z_t \le 1$, reverse chains lose correlation with the source partition but synthesize self-consistent community block modes from the learned population prior.

### Publication and Status

Accepted at the **Learning on Graphs Conference (LoG 2026)**; forthcoming in the *Proceedings of Machine Learning Research (PMLR)*.

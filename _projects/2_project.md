---
layout: page
title: Community Information Horizons in Discrete Graph Diffusion
description: Graphon analysis of spectral contraction, size-aware SNR coordinates, and the alignment switch. Forthcoming in PMLR at LoG 2026.
importance: 2
category: Research
related_publications: true
---

### Overview

At what noise level does a corrupted graph stop identifying the community structure that generated it? In discrete graph diffusion, graphs are corrupted by categorical Markov transitions (such as binary edge refresh) and reconstructed by a learned reverse chain. While the forward corruption process is straightforward to simulate, determining what collective structural information remains for the reverse model to exploit has remained an open challenge.

We show that this question cannot be answered by diffusion time alone: residual structure hidden by sampling noise in small graphs becomes statistically visible after aggregation in larger graphs. Using continuous graphons as a state space, we connect discrete edge corruption to population-level dynamics and establish a size-aware account of structural recoverability.

### Theoretical Contributions

- **Exact Graphon Affine Trajectory**: Under independent binary edge refresh with schedule $\beta_s$, every dense probability graphon follows the exact affine continuum trajectory:
  $$W_t = \rho + \bar{\alpha}_t(W_0 - \rho), \quad \text{where} \quad \bar{\alpha}_t = \prod_{s=1}^t (1 - \beta_s)$$
  We prove exact mode contraction $K_t = \bar{\alpha}_t K_0$, showing that forward diffusion contracts eigenvalue amplitudes without rotating eigenfunctions.
- **Structural Signal-to-Noise Ratio ($z_t$)**: For balanced two-block stochastic block models (SBMs), we derive the size-aware structural SNR coordinate:
  $$z_t = \frac{\bar{\alpha}_t \Delta \sqrt{n}}{\sqrt{p_t(1 - p_t)}}$$
  This single coordinate separates three distinct recovery scales:
  1. *Weak-detectability horizon ($z_t = 1$)*: Non-trivial partition overlap with the source becomes statistically achievable.
  2. *Consistency boundary ($z_t \to \infty$)*: Normalized probability matrix and oracle-coordinate posterior errors vanish.
  3. *Exact-recovery horizon ($z_t^2 \asymp \log n$)*: Zero misclassified vertices with high probability.
- **Fixed-$K$ Mode-Wise Horizons**: We extend this analysis mode by mode to general $K$-block graphons, establishing individual spectral thresholds $z_{k, t} = \frac{\bar{\alpha}_t \sqrt{n} |\lambda_k|}{\sqrt{v_t}}$ and a necessary condition for pairwise block distinction.

### Empirical Findings & The Alignment Switch

- **Cross-Size Collapse**: Source-partition recovery curves across training sizes $n \in \{128, 256, 512\}$ and zero-shot test size $n = 1024$ collapse tightly when plotted against $\log z_t$, reducing pairwise interpolation variance by $76.4\%$ compared to indexing by raw diffusion time.
- **The Alignment Switch**: Evaluating 576 complete reverse trajectories using a spectrally assisted denoiser exposes a fundamental behavioral transition:
  - *Above the horizon ($z \ge 2$)*: Reverse chains reconstruct the planted source community partition, increasing source overlap on $100\%$ of paths.
  - *Near and below the horizon ($z \le 1$)*: Source-partition alignment becomes statistically unavailable, dropping to finite-$n$ chance levels. However, rather than failing, the reverse chain locks onto a persistent, self-inferred partition and synthesizes fresh, coherent community block modes from the learned population prior.
- **Hierarchical Mode Loss**: In four-block experiments with eigenvalues $\{0.15, 0.10, 0.05\}$, the reverse chain loses fine-grained block distinctions at the exact successive times ($t = 20, 37, 47$) predicted by their respective mode horizons, while maintaining coarse community structure.

*Accepted to the full proceedings track of the **Learning on Graphs Conference (LoG 2026)**; forthcoming in PMLR (Oct 2026).*

---
layout: page
title: 'MoCDiff: Efficient Motif-Constrained Discrete Diffusion'
description: Motif-aware serialization (mSENT) and optimized constrained sampling for molecular graph generation. ICML 2026 Workshop.
importance: 4
category: Collaborative Research
related_publications: true
---

### Research Question

How can discrete masked diffusion models generate molecular graphs while maintaining chemical validity, diversity, and computational efficiency within practical sampling budgets?

### Approach

Standard string tokenizations decouple chemically coupled atoms in rings and scaffolds across distant sequence positions, while standard constrained sampling incurs computational overhead on early noisy states. This direction addresses both challenges through motif-aware graph serialization and multi-stage constrained sampling.

### Main Results

- **Motif-Aware SENT Tokenization (mSENT)**: The framework introduces a motif-biased traversal policy that prioritizes chemically coherent substructures (rings, aromatic cores, multiple bonds). Traversing within-motif neighbors first keeps rigid molecular scaffolds contiguous in sequence space while preserving exact graph decodability.
- **Optimized Constrained Diffusion Sampler**: Sampling efficiency is improved through four coordinated algorithmic components: inexact Augmented Lagrangian updates, conditionally adaptive penalties for actively violated constraints, lazy constraint enforcement (skipping projections during noisy early steps $\rho_s < 0.2$), and cached decode verification.
- **Empirical Evaluation on QM9 & MOSES**: Under matched Transformer denoisers, mSENT raises QM9 validity from $85.3\%$ to $90.5\%$ and uniqueness from $75.0\%$ to $97.7\%$ over standard SENT. The optimized sampler achieves a $1.62\times$ candidate generation speedup and $1.7\times$ higher accepted throughput over baseline Constrained Discrete Diffusion. On MOSES, it achieves $92.0\%$ validity and $99.7\%$ novelty.

### Publication / Status

Accepted at the **ICML 2026 Workshop on Generative and Agentic AI for Biology**.

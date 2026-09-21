---
layout: page
title: 'MoCDiff: Efficient Motif-Constrained Discrete Diffusion'
description: Motif-aware serialization (mSENT) and optimized constrained sampling for molecular graph generation. ICML 2026 Workshop.
importance: 4
category: Research
related_publications: true
---

### Overview

Generating realistic molecular graphs using generative models requires navigating vast discrete chemical spaces while producing valid, novel, and diverse compounds within practical computational budgets. Serializing molecular graphs into discrete token sequences allows leveraging scalable masked language modeling (MDLM) frameworks, but introduces two critical challenges:

1. **The Token-Order Problem**: Standard string formats (SMILES, SELFIES, SENT) order atoms based on syntax or depth-first graph traversal rather than chemical locality. Consequently, chemically coupled atoms within rigid ring systems or aromatic cores are scattered across distant sequence positions, forcing models to learn local chemical constraints through long-range token dependencies.
2. **The Constraint-Enforcement Problem**: Verifying chemical validity and uniqueness requires discrete decoding and RDKit sanitization. Existing frameworks like Constrained Discrete Diffusion (CDD) project token probabilities toward feasible sets at every reverse diffusion step, resulting in prohibitive wall-clock runtimes and redundant corrections on highly noisy intermediate states.

### Core Innovations

- **Motif-Aware SENT Tokenization (mSENT)**: We introduce a motif-biased traversal policy that prioritizes chemically coherent substructures—specifically ring systems, aromatic cores, and multiple bonds. By traversing within-motif neighbors first ($\alpha = 2.0$), mSENT ensures that rigid molecular scaffolds remain contiguous in the serialized sequence. Importantly, because mSENT modifies only the traversal policy without changing the SENT grammar or emission rules, exact graph decodability is preserved.
- **Optimized Constrained Diffusion Sampler**: We reduce sampling overhead through four coordinated algorithmic enhancements:
  - *Inexact Augmented Lagrangian (ALM) Solves*: Stops inner optimization when relaxed constraint improvements plateau, avoiding over-solving early noisy states.
  - *Conditionally Adaptive Penalty Updates (CAPU)*: Increases penalty weights only for actively violated constraints after discrete decoding, preventing optimization stiffness.
  - *Lazy Constraint Enforcement*: Skips projection during the first 20% of noisiest diffusion steps ($\rho_s < 0.2$), applies periodic checks during intermediate denoising, and concentrates feasibility enforcement near final decoded molecules ($\rho_s \ge 0.7$).
  - *Cached Decode Verification*: Avoids redundant sanitization checks for static token spans.

### Empirical Findings

- **Generation Quality (QM9)**: Under a matched 4-layer, 8-head MDLM Transformer denoiser and identical training budgets, mSENT substantially outperforms standard SENT serialization, increasing validity from $85.3\%$ to $90.5\%$, uniqueness from $75.0\%$ to $97.7\%$, and atom stability from $88.7\%$ to $94.7\%$.
- **Exploration & Diversity (MOSES)**: On the drug-like MOSES benchmark, unconstrained mSENT achieves $92.0\%$ validity, $99.7\%$ novelty, and an average QED drug-likeness of $0.83$, confirming that motif-aware tokenization fosters broad chemical exploration.
- **Sampling Efficiency**: On QM9, the optimized MoCDiff sampler reduces candidate generation time from $621.3\text{ s}$ to $383.4\text{ s}$ ($1.62\times$ speedup) and improves accepted-sample throughput from $0.72$ to $1.23\text{ molecules/s}$ over baseline CDD. On MOSES, it achieves a $1.38\times$ speedup with $91.0\%$ acceptance.

*Accepted to the **ICML 2026 Workshop on Generative and Agentic AI for Biology**.*

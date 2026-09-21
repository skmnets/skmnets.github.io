---
layout: page
title: Exact Set Discovery in Gene Regulatory Networks
description: Reframing GRN inference from pairwise edge classification to exact combinatorial regulator team discovery. ICLR 2026 Workshops.
importance: 5
category: Collaborative Research
related_publications: true
---

### Question

Because transcription factors often regulate targets cooperatively in multi-protein complexes, how can gene regulatory network inference be formulated to discover complete, cooperative regulator sets rather than isolated pairwise edges?

### Key Idea

We reframe regulatory inference as exact combinatorial regulator set discovery using a two-stage filter-and-refine pipeline: context-aware attention retrieval filters candidate regulators, followed by a residual set architecture that combines pairwise baselines with non-additive set interactions.

### Main Results

- **Two-Stage Architecture**:
  1. *Context-Aware Candidate Retrieval*: A target-conditioned attention pooler scores candidate regulators against target profiles within single-cell expression data, filtering the combinatorial space down to a high-recall candidate pool $P_t$.
  2. *Combinatorial Set Scoring (Residual HOS2)*: Evaluates candidate regulator subsets $S \subseteq P_t$ via $\text{Score}(S, t) = \sum_{r \in S} \phi_{\text{pair}}(r, t) + \psi_{\text{set}}(S, t)$, where a decomposable pairwise base $\phi_{\text{pair}}$ captures marginal associations and a Set Transformer $\psi_{\text{set}}$ captures non-additive cooperative logic.
- **Attention Retrieval on SERGIO**: On the SERGIO single-cell benchmark (1,200 genes, 2,700 cells across 9 cell types), context-aware retrieval improves Recall@80 over pairwise dot-product scoring across regulator team sizes ($R=2, 3, 4$).
- **Combinatorial Exact Set Recovery**: Residual HOS2 improves unconditional exact match over decomposable baselines (raising exact recovery from $0.222$ to $0.342$ for $R=3$ and $0.140$ to $0.193$ for $R=4$). Under oracle candidate injection ($R=4$), set-based modeling yields a $3.5\times$ exact-recovery gain over pairwise baselines.

### Publication and Status

Presented across workshops at **ICLR 2026** (*Gen²* and *MLGenX*).

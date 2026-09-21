---
layout: page
title: Exact Set Discovery in Gene Regulatory Networks
description: Reframing GRN inference from pairwise edge classification to exact combinatorial regulator team discovery. ICLR 2026 Workshops.
importance: 5
category: Research
related_publications: true
---

### Overview

Computational gene regulatory network (GRN) inference has traditionally been formulated as a pairwise link prediction problem: given transcriptomic data, an algorithm scores or ranks candidate regulator–target pairs $(r \to t)$ using metrics such as AUROC, AUPRC, or edge recall. However, biological gene regulation is intrinsically combinatorial. Transcription factors operate cooperatively within multi-protein complexes and enhanceosomes; a target gene may only activate or repress when a specific *team* of regulators $\{A, B, C\}$ acts jointly.

Evaluating individual edges in isolation can reward models for identifying isolated marginal associations while completely failing to identify the true regulatory mechanism. This project reframes the inference task as **Exact Regulator Set Recovery**: evaluating whether an algorithm successfully discovers the complete, unpartitioned regulator team $R^\star(t)$ controlling each target gene.

### The Two-Stage Filter-and-Refine Framework

Because combinatorial subset search over all possible regulator teams of size $R$ across $G$ genes scales as $\mathcal{O}(|G|^R)$, exhaustive scoring is computationally intractable. We design a two-stage architecture that decouples candidate generation from higher-order set evaluation:

1. **Stage 1 (Candidate Retrieval — Context-Aware Attention Pooler)**:
   - Encodes gene expression profiles $x_g$ into normalized latent representations $z_g$.
   - Computes a target-conditioned context vector $c_t$ by attending from the target embedding to all candidate gene embeddings.
   - Scores candidate regulators using an MLP over concatenated features: $\phi(z_r, z_t, c_t) = [z_r; z_t; c_t; z_r \odot z_t; z_r \odot c_t; z_t \odot c_t]$.
   - Filters the candidate pool down to a high-recall candidate set $P_t$, overcoming the initial combinatorial bottleneck.
2. **Stage 2 (Combinatorial Set Scoring — Residual HOS2)**:
   - Scores candidate regulator subsets $S \subseteq P_t$ using a residual high-order architecture:
     $$\text{Score}(S, t) = \sum_{r \in S} \phi_{\text{pair}}(r, t) + \psi_{\text{set}}(S, t)$$
   - The decomposable pairwise base $\phi_{\text{pair}}$ captures robust marginal associations.
   - The non-additive residual $\psi_{\text{set}}$ utilizes a Set Transformer encoder operating on a target-conditioned `[CLS]` token and regulator embeddings to learn permutation-invariant higher-order cooperative logic.
   - Zero-initialized residual heads ensure stable training dynamics in sparse single-cell settings.

### Empirical Findings

- **Synthetic DAG Diagnostic**: Evaluated across synthetic directed acyclic graph benchmarks ranging from additive/pairwise to purely combinatorial regulation. In pure higher-order settings where pairwise models fail ($0\%$ exact match), set-based scoring successfully learns partial overlap (improving Jaccard similarity and recall) and achieves top-1 ranking during training.
- **SERGIO DS3 Single-Cell Benchmark**: On the SERGIO single-cell benchmark (1,200 genes, 2,700 cells across 9 cell types), the context-aware attention retriever dramatically outperforms pairwise dot-product retrieval, improving Recall@80 from $0.649$ to $0.895$ for $R=2$, $0.718$ to $0.872$ for $R=3$, and $0.842$ to $1.000$ for $R=4$.
- **Exact Set Recovery Gains**: Residual HOS2 achieves superior unconditional exact match over decomposable baselines (raising exact recovery from $0.222$ to $0.342$ for $R=3$ and $0.140$ to $0.193$ for $R=4$).
- **Oracle Injection Proof of Mechanism**: When true regulators are guaranteed to be present in the candidate pool via oracle injection, Residual HOS2 achieves $0.368$ exact recovery for $R=4$ versus $0.105$ for Deep PairS2 (a $3.5\times$ improvement), confirming that explicit modeling of non-additive interactions is structurally required for combinatorial gene regulation.

*Presented across workshops at **ICLR 2026** (Gen² and MLGenX).*

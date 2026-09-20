---
layout: page
title: Normalized Routing Limits for Sparse Neural Networks
description: Graph-limit theory for width-growing sparse networks and neural tangent kernel recursions under vanishing density.
img: assets/img/12.jpg
importance: 1
category: Research
related_publications: true
---

### Overview

When neural networks grow in width while sparsifying (e.g., pruning regimes), ordinary adjacency graphons collapse to zero under vanishing connection density. This project develops a graph-limit framework showing that **normalized routing operators** retain rich, nontrivial mathematical structure even after raw graphons collapse.

### Key Contributions
- **Limiting NNGP & NTK Recursions**: Derived exact covariance recursions for structured sparse masks, including architectures reusing weights across forward and backward propagation without requiring artificial gradient-independence assumptions.
- **Sparse Block & Graphlet Preservation**: Proved that normalized graphlet operators preserve meaningful community block and spectral structure in sparse stochastic-block and random-pruning regimes.
- **Pruning Disentanglement**: Benchmarked random, magnitude, SNIP, and SynFlow pruning alongside degree-preserving null models to cleanly disentangle mask topology from mask–weight alignment.

*Accepted to the full proceedings track of **Learning on Graphs (LoG 2026)**; forthcoming in PMLR.*

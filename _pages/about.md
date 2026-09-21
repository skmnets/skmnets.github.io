---
layout: about
title: about
permalink: /
subtitle: Doctoral Researcher in Industrial Engineering & Management Systems, University of Central Florida

profile:
  align: right
  more_info: >
    <p>Complex Adaptive Systems Laboratory (CASL)</p>
    <p>University of Central Florida</p>
    <p>Orlando, FL</p>

selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: true # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
---

I am a Doctoral Researcher in Industrial Engineering and Management Systems at the **University of Central Florida (UCF)** and a Graduate Research Assistant in the **[Complex Adaptive Systems Laboratory (CASL)](https://biomind-eng.github.io/biomind/labs/casl.html)**, advised by **[Prof. Ivan Garibay](https://www.cecs.ucf.edu/faculty/ivan-garibay/)**.

Previously, I earned an **MS in Mathematics** from UCF (2022–2025) supported by the **UCF Dean's Fellowship**, and a **BS–MS Dual Degree in Mathematical Sciences** from the **[Indian Institute of Science Education and Research (IISER) Kolkata](https://www.iiserkol.ac.in/)** (2016–2021) supported by the **INSPIRE Fellowship** from the Department of Science and Technology, Government of India.

My research lies at the intersection of **theoretical machine learning, graph limits, network science, and generative modeling**, focusing on continuous formulations that explain and guide learning on discrete, sparse, and multi-scale network structures.

### Research Themes

- **Task-Conditioned Communication & Graph Limits in GNNs**: Investigating which communication routes actually benefit a graph neural network solving a downstream task. I derive explicit, activation-gated task derivatives for population-level communication ($S_W$), demonstrating that task alignment can favor heterophilous as well as homophilous communication. By viewing graphons as population coordinate systems, I prove finite-horizon consistency of topology learning across resolutions and show that scores from smaller models guide effective topology interventions on larger, frozen predictors (evaluated on synthetic relational tasks and traffic networks like METR-LA).
- **Normalized Routing Limits for Pruned Neural Networks**: Developing parameterization-faithful continuum limits for width-growing sparse neural networks under aggressive pruning. While raw adjacency graphons collapse in $L^1$ under vanishing edge density, local retained-fan-in scaling exposes a stable row-Markov routing operator ($P = D^{-1}M$). For two-hidden-layer networks, I establish deterministic finite-dimensional NNGP covariance and NTK limits across fixed- and vanishing-density regimes, prove density invariance, identify block-mass adjoints ($B^{(2)\dagger}$) governing backward sensitivity, and resolve forward–backward weight reuse through a Gaussian-conditioning decoupling argument.
- **Community Information Horizons in Discrete Graph Diffusion**: Establishing exact continuous graphon trajectories ($W_t = \rho + \bar{\alpha}_t(W_0 - \rho)$) and mode-contraction dynamics under discrete binary edge refresh. By introducing a size-aware structural signal-to-noise ratio ($z_t = \frac{\bar{\alpha}_t \Delta \sqrt{n}}{\sqrt{p_t(1 - p_t)}}$), I characterize three fundamental recovery regimes—weak detection ($z_t = 1$), consistency ($z_t \to \infty$), and exact recovery ($z_t^2 \asymp \log n$). This analysis reveals an *alignment switch*, where reverse diffusion chains cross the source-information horizon, lose alignment with the original source partition, and synthesize fresh, coherent population-level community modes.
- **Combinatorial Gene Regulation via Exact Set Discovery**: Reframing gene regulatory network (GRN) inference from traditional pairwise edge prediction into an exact combinatorial regulator set discovery problem. I developed a two-stage filter-and-refine pipeline using context-aware attention retrieval followed by Residual HOS2—a residual high-order set model that captures non-additive transcription factor interactions on top of a decomposable pairwise base.
- **Motif-Constrained Molecular Diffusion (MoCDiff)**: Addressing tokenization and sampling bottlenecks in discrete molecular diffusion. We develop mSENT, a motif-aware graph-to-sequence serialization policy that preserves rigid chemical substructures (rings, aromatic cores) as contiguous token spans while maintaining full exact graph decodability, paired with an optimized constrained diffusion sampler (inexact ALM, lazy projection) to drastically improve sampling throughput.

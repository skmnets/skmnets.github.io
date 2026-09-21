---
layout: about
title: about
permalink: /
subtitle: "PhD Student at UCF · Graph Machine Learning · Graph Limits · Network Science"

profile:
  align: right
  image: prof_pic.png
  image_circular: false
  more_info: >
    <p>Complex Adaptive Systems Laboratory (CASL)</p>
    <p>University of Central Florida</p>
    <p>Orlando, Florida</p>

selected_papers: false # rendered manually below as "Selected Research"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: false # rendered manually below as "News"
  scrollable: true
  limit: 5

latest_posts:
  enabled: false
---

I am a PhD student in Industrial Engineering and Management Systems at the [University of Central Florida (UCF)](https://www.ucf.edu/) and a Graduate Research Assistant in the [Complex Adaptive Systems Laboratory (CASL)](https://biomind-eng.github.io/biomind/labs/casl.html), advised by [Prof. Ivan Garibay](https://www.cecs.ucf.edu/faculty/ivan-garibay/).

My research lies at the intersection of graph machine learning, graph limits, network science, and mathematical machine learning. I am particularly interested in mathematical and population-level descriptions of how information is routed, transformed, and recovered in learning systems defined on networks.

Before joining UCF IEMS, I completed an M.S. in Mathematical Science at UCF, where I was a recipient of the UCF Dean's Fellowship, and a BS–MS Dual Degree in Mathematical Sciences at [IISER Kolkata](https://www.iiserkol.ac.in/), supported by the INSPIRE Scholarship for Higher Education (INSPIRE-SHE) from the Department of Science and Technology, Government of India.

### Research

#### Graph Limits for Task-Conditioned Communication
Graph neural networks communicate along edges, but the usefulness of a communication route depends on the task being solved. We study how message-passing structure should adapt to a downstream objective and how task-dependent communication patterns can be compared across graph resolutions. This is addressed through graph-limit representations that provide a common population coordinate system, together with task-conditioned edge sensitivities that identify whether strengthening or weakening a route locally improves the objective.

#### Sparse Neural Routing and Kernel Limits
What mathematical structure survives when neural networks become increasingly sparse as their width grows? This work develops continuum limits for pruned neural networks and shows that normalized routing structure, rather than raw connection density, governs meaningful NNGP and NTK behavior across sparsity regimes. The analysis provides a way to characterize when sparse architectures with very different densities induce the same limiting computation.

#### Information Horizons in Graph Diffusion
How much structural information remains recoverable as a graph is progressively corrupted by a diffusion process? We study this question using graphons, spectral structure, and size-aware signal-to-noise coordinates. The resulting analysis identifies distinct information horizons for detection, consistency, and exact recovery, and characterizes how reverse diffusion changes after information about the original source structure is no longer statistically identifiable.

#### Collaborative Research
Collaborative work also considers problems in generative modeling and computational biology, including motif-aware discrete diffusion for molecular generation and higher-order set models for combinatorial gene-regulatory inference.

## [News]({{ '/news/' | relative_url }})
{% include news.liquid limit=true %}

## [Selected Research]({{ '/publications/' | relative_url }})
{% include selected_papers.liquid %}

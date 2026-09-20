---
layout: page
title: Task-Conditioned Communication in GNNs
description: Developing adjoint-based task edge sensitivities and population-level coordinates for topology interventions.
img: assets/img/3.jpg
importance: 3
category: Research
related_publications: false
---

### Overview

Standard message-passing neural networks (MPNNs) pass messages indiscriminately across structural edges, often leading to over-smoothing or bottlenecking. This project investigates how to quantify and guide communication specifically aligned with downstream task objectives.

### Key Contributions
- **Adjoint Edge Sensitivity**: Formulated edge sensitivity as the functional derivative of task loss with respect to a continuous communication kernel using an adjoint recursion, relating productive information exchange to interactions between forward activations and backward task gradients.
- **Population Coordinate Systems**: Leveraged graph limits to place edge sensitivities learned at disparate graph resolutions into a common population coordinate system.
- **Topology Interventions**: Evaluated cross-resolution transfer and topology interventions across synthetic graph models and real-world infrastructure benchmarks (METR-LA traffic network).

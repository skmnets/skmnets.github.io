---
layout: page
permalink: /publications/
title: publications
description: Publications, manuscripts, and selected presentations in graph machine learning, graph limits, network science, generative modeling, and computational biology.
nav: true
nav_order: 1
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->
{% include bib_search.liquid %}

<div class="publications">

<h2 class="category">Peer-Reviewed Conference Proceedings</h2>
{% bibliography --group_by none --query @*[category=conference] %}

<h2 class="category">Manuscripts and Preprints</h2>
{% bibliography --group_by none --query @*[category=manuscript] %}

<h2 class="category">Workshop Papers</h2>
{% bibliography --group_by none --query @*[category=workshop] %}

<h2 class="category">Selected Talks and Presentations</h2>
{% bibliography --group_by none --query @*[category=talk] %}

</div>

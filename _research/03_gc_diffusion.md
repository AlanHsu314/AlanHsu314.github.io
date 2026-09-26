---
layout: page
title: GC Diffusion
description: Score-based Conditional Diffusion Models for Galaxy Cluster Dark Matter + Gas Reconstruction
img: assets/img/research/gc_diffusion/sample_dm.jpg
importance: 2
category: past                 
related_publications: Hsu_2025_diffusion   # bibtex keys from _bibliography/papers.bib
---

<!-- An image or gif. A .gif animates automatically through figure.html. -->
<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/research/gc_diffusion/sde_diagram.png" title="" class="img-fluid rounded z-depth-1 w-100" %}
  </div>
</div>
<div class="caption">
  SDE Diagram of our score-based conditional diffusion model
</div>

## Description



## Results

Below we show the posterior mean reconstructions of the projected dark matter and gas maps of a galaxy cluster conditioned on the SZ and X-ray observables.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/research/gc_diffusion/halo_log_lin.jpg" title="" class="img-fluid rounded z-depth-1 w-100" %}
  </div>
</div>
<div class="caption">
  Dark matter and gas reconstruction
</div>
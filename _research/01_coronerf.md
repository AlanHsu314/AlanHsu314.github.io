---
layout: page
title: CoroNeRF
description: Differentiable Neural Tomography Framework for Joint Density-Temperature Inversion
img: assets/img/research/coronerf/tilted_orbit_emission_total_gt.gif
importance: 1
category: current                 
related_publications: Hsu_2026_coronerf   # bibtex keys from _bibliography/papers.bib
---

<!-- An image or gif. A .gif animates automatically through figure.html. -->
<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/research/coronerf/tilted_orbit_emission_total_both.gif" title="" class="img-fluid rounded z-depth-1 w-100" %}
  </div>
</div>
<div class="caption">
  Tilted orbit of GT and reconstructed corona.
</div>

## Description

Inverting the latent thermodynamic state of the corona from line intensity images is a highly ill-posed problem: there are not only geometric LOS degeneracies (emissivities redistributed along the LOS can generate the indistinguishable observations), but also plasma thermodynamic degeneracies (multiple density-temperature pairs can produce the same emissivity response). We develop CoroNeRF to jointly optimize 3D electron density and temperature fields directly from multiview, multiline intensities through a differentiable atomic-emission renderer.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/research/coronerf/coronerf_diagram.png" title="" class="img-fluid rounded z-depth-1 w-100 white-bg" %}
  </div>
</div>
<div class="caption">
  Diagram of CoroNeRF. Mutiview, multiline observations of four spectral channels (Fe XIII 1075/1080 nm, Si IX 2585/3935 nm) are used to fit a multiresolution hash-grid neural plasma field through a differentiable renderer by minimizing an image loss. The fitted neural field yields jointly recovered 3D density and temperature fields.
</div>

## Results

Below we show sample joint reconstructions of density (top) and temperature (bottom), by showing latitude-longitude (flattened-shell) plots sweeping through 1.1-4.0 solar radii.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/research/coronerf/shell_sweep_ne_temp.gif" title="" class="img-fluid rounded z-depth-1 w-100" %}
  </div>
</div>
<div class="caption">
  Joint density-temperature reconstruction at 1.1-4.0 solar radii.
</div>
---
layout: page
title: CORSAIR
description: Probabilistic Calibration of the CORSAIR Polarimeter
img: assets/img/research/corsair/pol_focus_lens.jpg
importance: 2
category: current                 
related_publications: Hsu_2026_polcal   # bibtex keys from _bibliography/papers.bib
---

## Description

The Coronal Spectropolarimeter for Airborne Infrared Research (CORSAIR) is a balloon-borne coronagraph + spectropolarimeter that will make long-duration measurements of NIR solar coronal emisssion lines. I've worked on many parts of this instrument throughout my undergraduate and graduate studies under the guidance of my PI Jenna Samra, and I'm happy to see that it successfully launched during its qualification flight in Fall 2026!

My work primarily revolves around calibrating the polarimeter, the portion of the instrument that encodes the incoming light into a modulated intensity signal that can be inverted in post-processing to obtain the polarization, and thus coronal magnetic field diagnostics.

## Results

Calibrating the polarimeter requires us to generate known polarization inputs, measure the output modulation signal, and fit the free parameters in the optical pipeline. We represent the polarimeter as a probabilitic Mueller matrix model with a joint prior on the unknown parameters in the matrices. We then calibrate the distribution with the data to learn a joint posterior, and propagate the learned calibration uncertainty to downstream science tasks. 

<!-- An image or gif. A .gif animates automatically through figure.html. -->
<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/research/corsair/hardware_diagram_labeled.png" title="" class="img-fluid rounded z-depth-1 w-100 white-bg" %}
  </div>
</div>
<div class="caption">
  Diagram of the CORSAIR polarimeter calibration. To calibrate the polarimeter (yellow), we place a source + calibration unit (red + green) to generate known polarization inputs, record the modulated intensity with an IR detector (blue), which is then used to calibrate our probabilistic model.  
</div>

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/research/corsair/demod_ppd_diagram.png" title="" class="img-fluid rounded z-depth-1 w-100 white-bg" %}
  </div>
</div>
<div class="caption">
  Example of propagated calibration uncertainty. We can construct a posterior predictive distribution of the demodulation matrix, the main tool used for spectropolarimetric inversion during deployment. These calibration uncertainties can further be propagated to the recovered Stokes vector on RHS of the equation.  
</div>
 
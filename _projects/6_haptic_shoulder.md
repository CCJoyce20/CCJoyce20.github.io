---
layout: page
title: Haptic Shoulder
description: "A phantom shoulder so robots can practice on something other than a person: ICRA 2025 (co-first author), provisional patent"
img: assets/img/projects/haptic_shoulder.jpg
importance: 6
category: research
---

Robots that reposition, dress, or rescue people have to move human limbs, but developing those behaviors means testing them on humans, which is slow, risky, and hard to repeat. Medical training has an answer for this: the phantom, a stand-in body you can practice on. We built the robotics equivalent for the shoulder.

{% include figure.liquid loading="eager" path="assets/img/projects/haptic_shoulder.jpg" title="Haptic Shoulder device" class="img-fluid rounded z-depth-1" %}

### Why the shoulder is hard

The shoulder isn't a simple ball joint. Its reachable range depends on the configuration you're already in, how far you can rotate the arm changes with how far it's raised, and the limits are *coupled* across axes. A device that renders fixed per-axis limits doesn't feel like a shoulder.

{% include figure.liquid loading="lazy" path="assets/img/projects/hs_limits.jpg" title="Complex coupled joint limits" class="img-fluid rounded z-depth-1" %}
<div class="caption">Shoulder joint limits are coupled: the reachable range on one axis depends on where the others are.</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/hs_human_range.png" title="Human shoulder configuration space" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The human shoulder's reachable configuration space.</div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/hs_device_range.png" title="Device configuration space" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The device's mechanical range exceeds the human one, so the rendered limits, not the mechanism, define the boundary.</div>
    </div>
</div>

{% include figure.liquid loading="lazy" path="assets/img/projects/hs_coupling.jpg" title="Coupled joint limits" class="img-fluid rounded z-depth-1" %}
<div class="caption">The rendered range of motion shifts with humeral rotation, reproducing the coupling that makes a real shoulder feel like a shoulder.</div>

### The mechanism

An inverted U-joint arrangement gives the device its anatomically-shaped workspace, with one motor-encoder module per anatomical degree of freedom, so actuator space maps directly onto shoulder joint space, and there's no kinematic solving between what the motors do and what the joint does.

{% include figure.liquid loading="lazy" path="assets/img/projects/hs_renderreal.jpg" title="Singular joint center" class="img-fluid rounded z-depth-1" %}
<div class="caption">The inverted U-joint places all rotation axes through a single joint center that matches the human shoulder's, in CAD and in the built device.</div>

### Testing robots on it

{% include figure.liquid loading="lazy" path="assets/img/projects/hs_experiment.png" title="Robot interaction experiment" class="img-fluid rounded z-depth-1" %}
<div class="caption">A robot manipulating the phantom arm, pHRI planning tested and deployed on real hardware without a human subject in the loop.</div>

Published at [ICRA 2025](https://ieeexplore.ieee.org/document/11127862) (co-first author). Provisional patent in progress.

<iframe src="https://www.youtube.com/embed/MKJiqIRkErY" style="width:100%;aspect-ratio:16/9;border:0;border-radius:8px;" allowfullscreen title="Haptic Shoulder video"></iframe>

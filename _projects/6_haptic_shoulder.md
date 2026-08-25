---
layout: page
title: Haptic Shoulder
description: "Biomechanically accurate shoulder phantom for pHRI — ICRA 2025 (co-first author), provisional patent"
img: assets/img/projects/haptic_shoulder.jpg
importance: 6
category: research
---

Testing physical human–robot interaction on people is slow and risky, so we built the robot a patient: a shoulder phantom that reproduces human joint center, coupled kinematics, and configuration-dependent range of motion, the way a medical phantom stands in for anatomy. One motor-encoder module per anatomical degree of freedom gives a direct mapping between actuator space and shoulder joint space, enabling real-time pHRI testing and deployment onto physical robots without human subjects.

Published at [ICRA 2025](https://arxiv.org/abs/2409.13905) (co-first author). Provisional patent in progress.

<iframe src="https://www.youtube.com/embed/MKJiqIRkErY" style="width:100%;aspect-ratio:16/9;border:0;border-radius:8px;" allowfullscreen title="Haptic Shoulder video"></iframe>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/haptic_coupling.jpg" title="Coupled joint limits" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The rendered range of motion changes with humeral rotation, reproducing the coupled joint limits of the human shoulder.</div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/haptic_cspace.jpg" title="Configuration space" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The device's mechanical configuration space exceeds the human shoulder's, so the rendered limits — not the mechanism — define the boundary.</div>
    </div>
</div>

<!-- TODO: add cover image (Cover_new (2) - haptic shoulder paper cover) as assets/img/projects/haptic_shoulder.jpg, then uncomment img: in front matter -->

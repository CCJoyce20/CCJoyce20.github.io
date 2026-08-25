---
layout: page
title: ARCSnake
description: "Amphibious screw-propelled snake robot with NASA JPL — IROS 2026, ISRR 2024, ICRA 2023"
img: assets/img/projects/arcsnake.jpg
importance: 7
category: other robotics
---

Four years on an amphibious, screw-propelled snake robot developed with NASA JPL, spanning my first paper to a full-system publication at [IROS 2026](https://arxiv.org/abs/2511.11970). Screw propulsion is one of the few locomotion methods that works across sand, water, gravel, and mud without changing hardware — which is why it was proposed for exploring the subsurface ocean of Saturn's moon Enceladus.

{% include figure.liquid loading="eager" path="assets/img/projects/arcsnake.jpg" title="ARCSnake amphibious testing" class="img-fluid rounded z-depth-1" %}

### System design improvements

Across ARCSnake V2's development I worked on the propulsion system, **increasing screw output torque by 40%**. The gains came from three places: raising the torque ratio, aligning the belt drive, and cutting parasitic friction — shortening the whole drive stack and relieving surfaces that were rubbing. I built a physical testbed to validate each change rather than trusting the CAD.

{% include figure.liquid loading="lazy" path="assets/img/projects/screw_shell.jpg" title="Screw shell design" class="img-fluid rounded z-depth-1" %}
<div class="caption">Screw block redesign — a shorter, cleaner stack with less rubbing surface.</div>

### Screw characterization testbed — ICRA 2023

To find out which screw parameters actually matter, I engineered a mobile testbed that isolates a single screw sub-unit and measures its performance across media: constrained axial measurement with a 6-DOF force-torque sensor, a swappable bottom module so different screw configurations drop straight in, built-in electronics bays and wiring paths, and SolidWorks FEA validation before fabrication. It is portable enough to run in real terrain rather than only in a lab.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/screw_testbed.jpg" title="Experimental mobile screw locomotion testbed" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/screw_testbed_fea.png" title="SolidWorks FEA of the testbed" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The resulting characterization across gravel, grass, sand, wood chips, dirt, and concrete became [Mobility Analysis of Screw-Based Locomotion and Propulsion in Various Media](https://arxiv.org/abs/2301.10878) (co-first author, ICRA 2023).

### NASU — ISRR 2024

[NASU (Novel Actuating Screw Unit)](https://arxiv.org/abs/2310.00184) is the first Archimedes-screw locomotion design with a **dynamically reconfigurable angle of attack**, letting one screw retune its pitch for the medium it is currently in rather than compromising across all of them. The mechanism is origami-inspired: a Kresling unit produces the coupled rotation and translation that changes the screw pitch (first author, ISRR 2024).

{% include figure.liquid loading="lazy" path="assets/img/projects/nasu_mech.jpg" title="NASU mechanism overview" class="img-fluid rounded z-depth-1" %}
<div class="caption">NASU mechanism overview.</div>

{% include figure.liquid loading="lazy" path="assets/img/projects/nasu_media.png" title="NASU across media: gravel, sand, rocks, grass, mulch" class="img-fluid rounded z-depth-1" %}

<video controls preload="metadata" style="width:100%;border-radius:8px;">
    <source src="/assets/video/isrr2024_nasu.mp4" type="video/mp4">
</video>
<div class="caption">NASU — ISRR 2024 video</div>

### The Voodoo Doll

A 10-DOF joint-matching teleoperation controller I built to command ARCSnake V2's joint positions — lockable U-joints with magnetic encoders, so an operator poses the controller and the robot mirrors it.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/voodoo_full.jpg" title="The full 10-DOF Voodoo Doll controller" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/voodoo_hanging.jpg" title="Voodoo Doll on its rig" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/voodoo_doll.jpg" title="A single Voodoo Doll joint module" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

I also led electrical and mechanical integration for validating the full robot in underwater testing.

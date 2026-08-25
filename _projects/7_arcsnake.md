---
layout: page
title: ARCSnake
description: "Amphibious screw-propelled snake robot with NASA JPL: IROS 2026, ISRR 2024, ICRA 2023"
img: assets/img/projects/arcsnake.jpg
importance: 7
category: research
---

Four years on an amphibious, screw-propelled snake robot developed with NASA JPL, spanning my first paper to a full-system publication at [IROS 2026](https://arxiv.org/abs/2511.11970). Screw propulsion is one of the few locomotion methods that works across sand, water, gravel, and mud without changing hardware, which is why it was proposed for exploring the subsurface ocean of Saturn's moon Enceladus.

{% include figure.liquid loading="eager" path="assets/img/projects/arcsnake.jpg" title="ARCSnake amphibious testing" class="img-fluid rounded z-depth-1" %}

<div class="row justify-content-center">
    <div class="col-sm-6">
        {% include figure.liquid loading="lazy" path="assets/img/projects/arcsnake_system.jpg" title="ARCSnake V2 full system" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The full ARCSnake V2 system: screw-propelled segments joined by actuated joints, so the robot both crawls and swims.</div>
    </div>
</div>

I also led electrical and mechanical integration for validating the full robot in underwater testing.

### System design improvements

Across ARCSnake V2's development I worked on the propulsion system, **increasing screw output torque by 40%**. The gains came from three places: raising the torque ratio, aligning the belt drive, and cutting parasitic friction, shortening the whole drive stack and relieving surfaces that were rubbing. I built a physical testbed to validate each change rather than trusting the CAD.

<div class="row justify-content-center">
    <div class="col-sm-9">
        {% include figure.liquid loading="lazy" path="assets/img/projects/belt_drive.png" title="Screw block belt drive" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The screw block drive: the belt (green) transmits motor torque to the screw. Aligning this drive and shortening the stack around it is where the torque gains came from.</div>
    </div>
</div>

### The screw testbed --- *Mobility Analysis of Screw-Based Locomotion and Propulsion in Various Media*

To find out which screw parameters actually matter, I engineered a mobile testbed that isolates a single screw sub-unit and measures its performance across media: constrained axial measurement with a 6-DOF force-torque sensor, a swappable bottom module so different screw configurations drop straight in, built-in electronics bays and wiring paths, and SolidWorks FEA validation before fabrication. It is portable enough to run in real terrain rather than only in a lab.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/screw_testbed_real.jpg" title="Experimental mobile screw locomotion testbed" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/screw_testbed_fea.png" title="SolidWorks FEA of the testbed" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Screws were characterized across gravel, grass, sand, wood chips, dirt, and concrete, in single and paired configurations. That characterization became [Mobility Analysis of Screw-Based Locomotion and Propulsion in Various Media](https://ieeexplore.ieee.org/document/10160777) (co-first author, ICRA 2023). The testbed has since been reused by the lab for further screw-locomotion studies beyond that paper.

### NASU: ISRR 2024

[NASU (Novel Actuating Screw Unit)](https://arxiv.org/abs/2310.00184) is the first Archimedes-screw locomotion design with a **dynamically reconfigurable angle of attack**, letting one screw retune its pitch for the medium it is currently in rather than compromising across all of them. The mechanism is origami-inspired: a Kresling unit produces the coupled rotation and translation that changes the screw pitch (first author, ISRR 2024).

<div class="row justify-content-center">
    <div class="col-sm-6">
        {% include figure.liquid loading="lazy" path="assets/img/projects/nasu_mech.jpg" title="NASU mechanism overview" class="img-fluid rounded z-depth-1" %}
        <div class="caption">NASU mechanism overview.</div>
    </div>
</div>

{% include figure.liquid loading="lazy" path="assets/img/projects/nasu_media.png" title="NASU across media: gravel, sand, rocks, grass, mulch" class="img-fluid rounded z-depth-1" %}

<video controls preload="metadata" style="width:100%;border-radius:8px;">
    <source src="/assets/video/isrr2024_nasu.mp4" type="video/mp4">
</video>
<div class="caption">NASU, ISRR 2024 video (<a href="https://www.youtube.com/watch?v=6ElKiwgMTSA">also on YouTube</a>)</div>

### The Voodoo Doll

A 10-DOF joint-matching teleoperation controller I built to command ARCSnake V2's joint positions, lockable U-joints with magnetic encoders, so an operator poses the controller and the robot mirrors it.

{% include figure.liquid loading="lazy" path="assets/img/projects/voodoo_full_rot.jpg" title="The full 10-DOF Voodoo Doll controller" class="img-fluid rounded z-depth-1" %}
<div class="caption">The full 10-DOF controller laid out.</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/voodoo_hanging.jpg" title="Voodoo Doll on its rig" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/voodoo_doll.jpg" title="A single joint module" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

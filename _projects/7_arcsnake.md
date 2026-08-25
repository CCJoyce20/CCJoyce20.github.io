---
layout: page
title: ARCSnake
description: "Amphibious screw-propelled snake robot with NASA JPL — IROS 2026, ISRR 2024, ICRA 2023"
img: assets/img/projects/arcsnake.jpg
importance: 7
category: other robotics
---

Four years on an amphibious, screw-propelled snake robot developed with NASA JPL, spanning my first paper to a full-system publication at [IROS 2026](https://arxiv.org/abs/2511.11970).

{% include figure.liquid loading="eager" path="assets/img/projects/arcsnake.jpg" title="ARCSnake amphibious testing" class="img-fluid rounded z-depth-1" %}

**My contributions:** increased propulsion-screw output torque 40% by building a testbed that isolated friction and alignment losses ([co-first author, ICRA 2023](https://arxiv.org/abs/2301.10878)); designed [NASU](https://arxiv.org/abs/2310.00184), the first Archimedes-screw locomotion unit with a dynamically reconfigurable angle of attack for sand, water, and dirt (first author, ISRR 2024); built the "Voodoo Doll," a 10-DOF teleoperation controller with lockable U-joints and magnetic encoders; and led electrical/mechanical integration for underwater testing.

**The Voodoo Doll**: a 10-DOF joint-matching teleoperation controller — lockable U-joints with magnetic encoders command ARCSnake V2's joint positions.

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

**The screw testbed** (ICRA 2023): constrained axial measurement with a 6-DOF force-torque sensor at the screw sub-unit level, structurally validated in SolidWorks FEA before fabrication.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/screw_testbed.jpg" title="Experimental mobile screw locomotion testbed" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/screw_testbed_fea.png" title="SolidWorks FEA of the testbed" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

**NASU** (ISRR 2024): a reconfigurable-pitch Archimedes screw, tested across gravel, sand, rocks, grass, and mulch.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/screw_shell.jpg" title="Screw shell design" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Screw shell improvements I designed for the propulsion unit.</div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/nasu_mech.jpg" title="NASU mechanism overview" class="img-fluid rounded z-depth-1" %}
        <div class="caption">NASU mechanism overview.</div>
    </div>
</div>

{% include figure.liquid loading="lazy" path="assets/img/projects/nasu_media.png" title="NASU across media: gravel, sand, rocks, grass, mulch" class="img-fluid rounded z-depth-1" %}

<video controls preload="metadata" style="width:100%;border-radius:8px;">
    <source src="/assets/video/isrr2024_nasu.mp4" type="video/mp4">
</video>
<div class="caption">NASU — ISRR 2024 video</div>

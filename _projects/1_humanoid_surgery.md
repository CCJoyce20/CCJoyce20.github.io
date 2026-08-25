---
layout: page
title: Humanoids for Medicine
description: "Can general-purpose humanoids do clinical work? Three studies, ending in Nature 2026."
img: assets/img/projects/nature_surgery.webp
date_range: 2024 to 2026
importance: 1
category: research
---

Purpose-built surgical robots cost millions and do one thing. A general-purpose humanoid is cheaper, mobile, and already shaped like the people whose tools and workspaces hospitals are built around. Can it actually do clinical work? Our lab spent three studies answering that, and I built the hardware that let a humanoid hold a surgeon's instruments in all of them.

---

### 1. Humanoids in Hospitals: can a humanoid use medical tools at all?

The [first study](https://arxiv.org/abs/2503.12725) (arXiv 2025, co-second author) asked the prerequisite question: can a humanoid surrogate perform dexterous medical interventions using the equipment clinicians already use? It characterized humanoid capability against the demands of real clinical tasks.

{% include figure.liquid loading="lazy" path="assets/img/projects/humanoids_tasks.jpg" title="Humanoid medical task study" class="img-fluid rounded z-depth-1" %}
<div class="caption">The medical interventions evaluated in the study, ultrasound, physical exam, bag-valve-mask ventilation, airway management, obstetric delivery, suturing, and oxygen delivery, performed by a humanoid on manikins and simulators.</div>

**My contribution:** I designed the mount system that lets a humanoid operate standard medical tools, optimizing mass and center of mass, verifying rigidity under load, and validating it in bench and simulation studies. That mount is the piece of hardware the next two papers are built on.

### 2. LapSurgie: teleoperated handheld laparoscopy

[LapSurgie](https://arxiv.org/abs/2510.03529) (ICRA 2026) took the platform into laparoscopy: a humanoid holding handheld laparoscopic instruments under teleoperation, with the remote-center-of-motion constraint enforced at the port. I contributed mechanical work to this version and helped present it at ICRA 2026.

### 3. In vivo feasibility: *Nature*, 2026

The [*Nature* study](https://doi.org/10.1038/s41586-026-10796-x) is the full evaluation: benchtop characterization, dry-lab user studies across surgical experience levels, and **in vivo porcine surgeries**.

{% include figure.liquid loading="eager" path="assets/img/projects/nature_surgery.webp" title="In vivo porcine surgery" class="img-fluid rounded z-depth-1" %}
<div class="caption">Two Unitree G1 humanoids at the operating table during in vivo porcine surgery, teleoperated from a stereo console; laparoscopic views show tissue handling through standard ports.</div>

A surgeon drives the humanoid from a da Vinci-style console (stereo headset, MTM manipulators, clutch pedal) over ROS, while the robot holds standard laparoscopic instruments through mounts that enforce the RCM constraint at the port.

{% include figure.liquid loading="lazy" path="assets/img/projects/nature_system.webp" title="Teleoperation system and tool mounts" class="img-fluid rounded z-depth-1" %}
<div class="caption">The operating console, the G1 with endoscope and wristed instruments at their RCM points, and the tool-mount hardware actuating the instruments' handles.</div>

<div class="row justify-content-center">
    <div class="col-sm-9">
        {% include figure.liquid loading="lazy" path="assets/img/projects/nature_tool_kinematics.webp" title="Instrument kinematics" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Mapping operator commands through the instrument's handle degrees of freedom about the RCM.</div>
    </div>
</div>

<div class="row justify-content-center">
    <div class="col-sm-7">
        {% include figure.liquid loading="lazy" path="assets/img/projects/nature_workspace.webp" title="Workspace analysis" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Simulated hand and instrument workspaces across RCM placements, benchmarked against the dVRK, with tracking-accuracy validation.</div>
    </div>
</div>

Participants from novices to senior surgeons performed peg-transfer and FLS-style tasks on the humanoid, the dVRK/da Vinci, and manual laparoscopy, followed by the in vivo procedures. The results locate humanoid teleoperation between manual laparoscopy and purpose-built surgical robots on accuracy and workload measures.

{% include figure.liquid loading="lazy" path="assets/img/projects/nature_benchtop.webp" title="Benchtop and user-study results" class="img-fluid rounded z-depth-1" %}
<div class="caption">Dry-lab tasks and results across the humanoid, dVRK/da Vinci Xi, and manual laparoscopy.</div>

**My contribution:** the tool-mount system that lets the humanoid actuate standard medical instruments, mechanical setup for every surgical session, and coordinating our 10-person robot–clinician team through the live surgeries, turning surgeon feedback into hardware revisions between sessions.

<iframe src="https://www.youtube.com/embed/QrHq9Xr1Bxk" style="width:100%;aspect-ratio:16/9;border:0;border-radius:8px;" allowfullscreen title="Humanoids in Hospitals / Surgie video"></iframe>

<div class="caption">Figures from the papers; © the authors.</div>

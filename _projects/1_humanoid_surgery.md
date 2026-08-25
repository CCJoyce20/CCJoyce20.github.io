---
layout: page
title: Humanoid Surgery
description: "In vivo feasibility of humanoid robots in laparoscopic surgery — Nature, 2026"
img: assets/img/projects/nature_surgery.webp
importance: 1
category: medical robotics
---

Can a general-purpose humanoid meet the precision, control, and safety bar of minimally invasive surgery? Our lab's answer, published in [*Nature* (2026)](https://doi.org/10.1038/s41586-026-10796-x), is a systematic evaluation of humanoid teleoperation for laparoscopic surgery: benchtop characterization, dry-lab user studies across surgical experience levels, and in vivo porcine surgeries.

{% include figure.liquid loading="eager" path="assets/img/projects/nature_surgery.webp" title="In vivo porcine surgery" class="img-fluid rounded z-depth-1" %}
<div class="caption">Two Unitree G1 humanoids at the operating table during in vivo porcine surgery, teleoperated from a stereo console; laparoscopic views show tissue handling through standard ports.</div>

**The system**: a surgeon drives the G1 from a da Vinci-style console (stereo headset, MTM manipulators, clutch pedal) over ROS, while the humanoid holds standard laparoscopic instruments through mounts that enforce the remote-center-of-motion constraint at the port. This is where my work lives: I designed the tool-mount system that lets the humanoid actuate standard medical tools, optimized for mass and center of mass with bench- and simulation-validated rigidity, and I ran mechanical setup for every surgical session.

{% include figure.liquid loading="lazy" path="assets/img/projects/nature_system.webp" title="Teleoperation system and tool mounts" class="img-fluid rounded z-depth-1" %}
<div class="caption">The operating console, the G1 with endoscope and wristed instruments at their RCM points, and the tool-mount hardware actuating the instruments' handles.</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/nature_tool_kinematics.webp" title="Instrument kinematics" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Mapping operator commands through the instrument's handle degrees of freedom about the RCM.</div>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/projects/nature_workspace.webp" title="Workspace analysis" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Simulated hand and instrument workspaces across RCM placements, benchmarked against the dVRK, with tracking-accuracy validation.</div>
    </div>
</div>

**The study**: participants from novices to senior surgeons performed peg-transfer and FLS-style tasks on the humanoid, the dVRK/da Vinci, and manual laparoscopy, followed by the in vivo procedures. The team's results locate humanoid teleoperation between manual laparoscopy and purpose-built surgical robots on accuracy and workload measures.

{% include figure.liquid loading="lazy" path="assets/img/projects/nature_benchtop.webp" title="Benchtop and user-study results" class="img-fluid rounded z-depth-1" %}
<div class="caption">Dry-lab tasks and results across the humanoid, dVRK/da Vinci Xi, and manual laparoscopy.</div>

Beyond the hardware, I coordinated our 10-person robot-clinician team through the live surgeries, turning surgeon feedback into hardware revisions between sessions. This work builds on our earlier [Humanoids in Hospitals](https://arxiv.org/abs/2503.12725) study and [LapSurgie](https://arxiv.org/abs/2510.03529) (ICRA 2026).

<iframe src="https://www.youtube.com/embed/QrHq9Xr1Bxk" style="width:100%;aspect-ratio:16/9;border:0;border-radius:8px;" allowfullscreen title="Humanoids in Hospitals / Surgie video"></iframe>

<div class="caption">Figures from the paper; © the authors.</div>

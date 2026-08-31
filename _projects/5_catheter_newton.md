---
layout: page
title: Autonomous Catheter Navigation
description: "Learned low-level control for steering a catheter through real patient anatomy (ARPA-H & DARPA project)"
# img: assets/img/projects/catheter.jpg  # TODO: add cover frame
date_range: Jul 2026 to present
importance: 5
category: research
---

> **This project is in active development.** Results below are qualitative by design: the physics baseline is currently being re-measured (see "What broke" further down).

Endovascular procedures mean steering a flexible catheter through branching vasculature under imaging, and outcomes depend heavily on operator experience. The long-term goal is autonomy that makes the procedure repeatable.

<video controls preload="metadata" style="width:100%;border-radius:8px;">
    <source src="/assets/video/catheter_nav.webm" type="video/webm">
</video>
<div class="caption">A learned policy steering a catheter through vasculature in NVIDIA's Isaac for Healthcare endoluminal simulator.</div>

### What I build

Navigation splits across two levels: a high-level policy picks waypoints through the vascular tree, and a low-level control policy drives the catheter tip to each one. I build the low-level policy; a teammate works on the high level. The low-level problem is where contact physics, tortuous geometry, and the catheter's own compliance make naive control fail.

I train these policies with PPO and domain randomization in GPU-accelerated physics, working in NVIDIA's **Isaac for Healthcare (i4h)** endoluminal simulator. The task is framed around waypoints rather than a single goal point so it sits properly underneath a planner, with the reward reworked so the policy stops being paid for progress made in the wrong vessel, and contact safety anchored to measured tissue perforation forces rather than an inherited number.

### Getting to real anatomy

The environment now runs on patient anatomy rather than idealized tubes. I built the pipeline end to end: segmented mesh, centerline and radii extraction, joined vessel tree, trimmed and flared junctions, baked lumen, trainable geometry. It takes a single command to intake an arbitrary mesh, which is what makes a physical phantom study possible later this year.

### What broke, and how we found it

Moving onto real anatomy exposed a failure that had been invisible until then: the catheter folded at essentially the same location on almost every femoral route.

We ruled out the device, the anatomy, the drive, a support sheath, stiffness, segment length, and the alternate containment mode, all with data, before finding the cause was our own containment layer. Containment was implemented as a hard position projection, so node positions were shoved around while the rod's internal frames stayed put. The bend constraint never saw the deformation. Inside a vessel, the catheter had been behaving as a geometric tube-follower with **no elastic response at all**.

That also explained a longer-running mystery, that shaft stiffness appeared to change nothing: a zero position Jacobian in the vendored solver's bend constraint meant what we had been reading as rigidity was really just tip-actuator gain. Not our bug, but it changes what the parameter means.

The honest cost: every score collected before this was measured on a rod with no working elasticity, so the baseline is being re-run from scratch. That is why this page currently carries no numbers. The last stretch of work bought correctness rather than scores, and for the first time the rod inside the anatomy is actually elastic.

### Perception, and a robot that could not see

Measurement also showed the policy was effectively blind to the bifurcation ahead of it: a uniformly distributed ray sensor cannot see down a pipe. I re-encoded the rays forward and goal-directed. Alongside that, I built a **simulated C-arm** that renders an X-ray view from a real CT volume, which is the groundwork for image-based perception and for matching what the physical phantom rig will actually show.

### Making the rig run itself

Training runs take about four hours, so I built a guarded job queue with a watchdog that restarts stalls, resumable training, and shared evaluator settings so the scalar and batched code paths cannot silently drift apart again. Fold and overstretch are now logged every iteration, so a physics regression shows up during training instead of at scoring time.

I also contributed three catheter simulation demos to [Newton](https://github.com/newton-physics/newton), the open-source physics engine from NVIDIA, Google DeepMind, and Disney Research.

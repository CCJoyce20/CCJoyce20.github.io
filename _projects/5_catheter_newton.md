---
layout: page
title: Autonomous Catheter Navigation
description: "In progress — RL for endovascular robotics (ARPA-H & DARPA project)"
# img: assets/img/projects/catheter.jpg  # TODO: add cover frame
importance: 5
category: research
---

> **This project is in active development.** It started in July 2026; this page will grow as results mature.

Endovascular procedures mean steering a catheter through branching vasculature under imaging, and the skill ceiling is high enough that outcomes depend heavily on operator experience. The long-term goal is autonomy that makes the procedure repeatable.

<video controls preload="metadata" style="width:100%;border-radius:8px;">
    <source src="/assets/video/catheter_nav.webm" type="video/webm">
</video>
<div class="caption">A learned policy steering a catheter through vasculature in NVIDIA's Isaac for Healthcare endoluminal simulator.</div>

### What I'm building

The architecture splits navigation across two levels: a **high-level policy** picks waypoints through the vascular tree, and a **low-level control policy** drives the catheter tip to each one. I build the low-level policy; a teammate works on the high level. The low-level problem is where contact physics, tortuous geometry, and the catheter's own compliance make naive control fail.

I train these policies with PPO and domain randomization in GPU-accelerated physics simulation of patient-derived vasculature, working in NVIDIA's **Isaac for Healthcare (i4h)** endoluminal simulator. I also made sampling-based MPC tractable in simulation by building state snapshot/restore for the GPU catheter-physics solver, and contributed three catheter simulation demos to [Newton](https://github.com/newton-physics/newton), the open-source physics engine from NVIDIA, Google DeepMind, and Disney Research.

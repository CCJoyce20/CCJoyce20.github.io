---
layout: page
title: Autonomous Catheter Navigation
description: "RL for endovascular robotics — ARPA-H & DARPA project, with open-source contributions to Newton"
# img: assets/img/projects/catheter.jpg  # TODO: add cover image
importance: 5
category: medical robotics
---

An early-stage project on autonomous catheter steering for endovascular procedures. In GPU-physics simulation of patient-derived vasculature, I train PPO policies with domain randomization; early policies outperform the project's prior baseline. I also made sampling-based MPC tractable in simulation by building state snapshot/restore for the GPU catheter-physics solver.

Along the way I built three catheter simulation demos for [Newton](https://github.com/newton-physics/newton), the open-source physics engine from NVIDIA, Google DeepMind, and Disney Research.

<!-- TODO: add media - sim renders of catheter in aorta, Newton demo GIF -->

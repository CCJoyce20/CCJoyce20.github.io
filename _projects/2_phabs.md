---
layout: page
title: PHABS
description: "Portable Haptic Assisted Bimanual System — force-rich demonstrations for imitation learning (project lead; first author, ICRA 2027 submission)"
# img: assets/img/projects/phabs.jpg  # TODO: add cover image
importance: 2
category: medical robotics
---

Video, simulation, and position-only teleoperation data are all force-blind, yet contact force is exactly what decides whether two hands crush, drop, or tear the object between them. PHABS is a handheld bimanual bilateral teleoperation device that fixes this: it renders both per-hand pinching force and, uniquely, the **internal force between the two hands on a shared object** — to our knowledge the first handheld device to render this signal as a dedicated haptic channel.

**What I built:** capstan-driven pinch actuators paired with a gimbal-motor squeeze stage; a bilateral loop on an Anvil OpenArm dual-arm robot that maps gravity-compensated joint effort through the manipulator Jacobian into pinch and inter-hand force channels; and force-rendering verified against a reference load cell. We're now training ACT policies on matched haptic vs. no-haptic demonstrations across contact-rich bimanual tasks.

Patent in preparation. First-author paper targeted at ICRA 2027.

<!-- TODO: add photos - device hero shot, capstan detail, teleop in action -->

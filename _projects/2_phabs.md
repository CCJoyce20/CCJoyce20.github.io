---
layout: page
title: PHABS
description: "Portable Haptic Assisted Bimanual System: teaching robots the forces that video can't record (project lead; first author, ICRA 2027)"
img: assets/img/projects/phabs.jpg
importance: 2
category: research
---

Manipulation policies are trained on data that is blind to force. Human video carries no force signal, simulation invents it from designer-chosen contact parameters, and teleoperation usually withholds it from the demonstrator. For tasks where success is set by *how hard* you press, peeling a seal, opening a bag, handling something fragile, the demonstrations we train on are missing the variable that decides the outcome.

PHABS is my answer to that: a handheld bimanual teleoperation device built specifically to produce **force-annotated demonstrations** for imitation learning. It renders per-hand pinch force and, uniquely, the **internal force between the two hands** on a shared object, the signal that distinguishes crushing an object from merely supporting it, which no handheld bimanual device had rendered before.

> **This project is in active development.** The paper is targeted at ICRA 2027 and the figures below show work in progress, not a finished system.

{% include figure.liquid loading="eager" path="assets/img/projects/phabs.jpg" title="PHABS prototype with the Anvil OpenArm follower" class="img-fluid rounded z-depth-1" %}
<div class="caption">Left: the Anvil OpenArm dual-arm follower. Right: an early PHABS prototype held in both hands, the two pincher assemblies coupled through the gimbal rings and shared rails that carry the inter-hand squeeze channel (shown before electronics and actuators were installed).</div>

**Leading the project, I work from the data requirements backwards.** What the learning pipeline needs determines the design: which channels are worth rendering, what has to be logged and at what rate, and which hardware compromises are acceptable because they don't degrade the resulting dataset.

**The software:**
- **Bilateral control loop** on an Anvil OpenArm dual-arm robot: contact wrenches estimated from gravity-compensated joint effort (recursive Newton–Euler), mapped through the manipulator Jacobian, and rendered back to the operator as pinch and signed inter-hand force.
- **Data pipeline** capturing synchronized device-frame, robot-frame, and object-pose streams into a schema shared across collection, training, and deployment, so demonstrations are directly trainable rather than needing post-hoc reconstruction.
- **Policy learning**: ACT policies trained on matched haptic vs. no-haptic demonstrations across contact-rich bimanual tasks, an ablation designed to isolate what felt force at collection time is actually worth to the resulting policy.

**The hardware**, in one line: capstan-driven pinch actuators and a gimbal-motor squeeze stage, with force rendering verified against a reference load cell so the numbers in the dataset mean something.



Patent in preparation. First-author paper targeted at ICRA 2027.

<!-- TODO: add photos - device hero shot, teleop in action, force trace plot -->

---
layout: page
title: PHABS
description: "Portable Haptic Assisted Bimanual System — teaching robots the forces that video can't record (project lead; first author, ICRA 2027)"
# img: assets/img/projects/phabs.jpg  # TODO: add cover image
importance: 2
category: medical robotics
---

Manipulation policies are trained on data that is blind to force. Human video carries no force signal, simulation invents it from designer-chosen contact parameters, and teleoperation usually withholds it from the demonstrator. For tasks where success is set by *how hard* you press — peeling a seal, opening a bag, handling something fragile — the demonstrations we train on are missing the variable that decides the outcome.

PHABS is my answer to that: a handheld bimanual teleoperation device built specifically to produce **force-annotated demonstrations** for imitation learning. It renders per-hand pinch force and, uniquely, the **internal force between the two hands** on a shared object — the signal that distinguishes crushing an object from merely supporting it, which no handheld bimanual device had rendered before.

**Leading the project, I work from the data requirements backwards.** What the learning pipeline needs determines the design: which channels are worth rendering, what has to be logged and at what rate, and which hardware compromises are acceptable because they don't degrade the resulting dataset.

**The software:**
- **Bilateral control loop** on an Anvil OpenArm dual-arm robot: contact wrenches estimated from gravity-compensated joint effort (recursive Newton–Euler), mapped through the manipulator Jacobian, and rendered back to the operator as pinch and signed inter-hand force.
- **Data pipeline** capturing synchronized device-frame, robot-frame, and object-pose streams into a schema shared across collection, training, and deployment, so demonstrations are directly trainable rather than needing post-hoc reconstruction.
- **Policy learning**: ACT policies trained on matched haptic vs. no-haptic demonstrations across contact-rich bimanual tasks — an ablation designed to isolate what felt force at collection time is actually worth to the resulting policy.

**The hardware**, in one line: capstan-driven pinch actuators and a gimbal-motor squeeze stage, with force rendering verified against a reference load cell so the numbers in the dataset mean something.

Patent in preparation. First-author paper targeted at ICRA 2027.

<!-- TODO: add photos - device hero shot, teleop in action, force trace plot -->

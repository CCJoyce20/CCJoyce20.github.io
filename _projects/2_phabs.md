---
layout: page
title: PHABS
description: "Portable Haptic Assisted Bimanual System: letting a teleoperator feel the force between their two hands (project lead; first author, submitted to ICRA 2027)"
img: assets/img/projects/phabs_device.jpg
date_range: 2025 to present
importance: 2
category: research
---

Manipulation policies are trained on data that is blind to force. Human video carries no force signal, simulation invents it from designer-chosen contact parameters, and teleoperation usually withholds it from the demonstrator, who ends up judging contact by eye and over-gripping. For tasks where success is set by *how hard* you press, the demonstrations we train on are missing the variable that decides the outcome.

PHABS is a handheld bimanual teleoperation device built to produce **force-annotated demonstrations**. It renders per-hand pinch force and, uniquely, the **internal force between the two hands** on a shared object. That internal force is what separates crushing an object from merely supporting it, and per-hand feedback cannot convey it: a per-hand force reads the same whether your hands are squeezing the object or just holding up its weight.

> The first paper is submitted to ICRA 2027, and the project is ongoing.

<div class="row justify-content-center">
    <div class="col-sm-9">
        {% include figure.liquid loading="eager" path="assets/img/projects/phabs_device.jpg" title="The PHABS device held in both hands" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Two pincher handles share one rail. Each hand feels its own pinch force, and the rail between them renders the squeeze-in or push-out force the hands exert on each other through the object.</div>
    </div>
</div>

### How it works

**Portable by design.** The inter-hand force is reacted from one hand to the other through the device's own frame, the same way a real object balances the forces you apply to it. The mechanism plays the role of the object, so the device needs no table or grounding, and the operator can carry it (1.94 kg) and move around to follow the robot.

**Characterized, not assumed.** Both channels were measured against a reference load cell. Rendered pinch force tracks the reference to 0.13 N RMS error, and its trial-to-trial variation sits below the smallest force difference a human fingertip can detect.

**Bilateral teleoperation.** The device drives a dual-arm follower. The follower's contact forces are split into each gripper's squeeze and the internal force along the axis between the hands, then rendered back through the matching channel, so compression and separation feel like distinct, directional cues. For the study, the follower was simulated, which gives ground-truth contact force and identical conditions for every participant; the force-estimation path for the physical dual-arm robot is implemented but was not part of this evaluation. Every episode is logged in a format that goes straight into training.

### What the user study showed

Ten participants and 247 recorded trials, on two tasks built so that success depends on applied force: an egg hand-off, which loads the pinch channel, and a vase lifted only by squeezing it between the hands, which loads the inter-hand channel.

<div class="row justify-content-center">
    <div class="col-12">
        {% include figure.liquid loading="lazy" path="assets/img/projects/phabs_study.png" title="User study results" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">Each grey dot is one participant's median, and bars are the median across participants. N: no feedback, I: inter-hand only, P: pinch only, B: both channels. Panel (e) is the safety margin, peak force as a fraction of the object's crush limit.</div>
    </div>
</div>

- **Pinch feedback cut egg grip crushes from 33% to 6%** of trials and grip force by about two-thirds (1.65 to 0.47 N), lower for all ten participants.
- **The inter-hand channel nearly halved the squeeze on the vase** (5.81 to 3.02 N) and cut press crushes on the egg from 18% to 2%.
- **Demonstrations stayed roughly twice as far from the crush limit**, and force was steadier, with no cost in completion time, path length, or smoothness.
- **Operators felt it**: median confidence on the vase rose from 4 to 7.5 out of 10 with the inter-hand channel.

A demonstration inherits the force profile the operator produced, so less over-squeeze means better force annotations for whatever policy is trained on them.

### What didn't work

The inter-hand channel made the egg transfer itself less reliable: the hand-off succeeded in 39% of trials with both channels, against 62% with pinch alone. At the gain we used, the channel likely pushed on the operator's hands while both held the egg, disturbing the grip instead of informing it. The fix is a gain tuned per task and per phase rather than one hand-tuned value. Vertical motion is also estimated by double-integrating the IMUs, which drifts from stroke to stroke; operators corrected it by eye, but an external position reference would remove the problem.

Patent in preparation.

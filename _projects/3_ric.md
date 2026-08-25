---
layout: page
title: "RIC: Can Robots Handle Infants?"
description: "Robotic Infant Care: the first framework for robots that physically handle babies (project lead; first author, ICRA 2027)"
img: assets/img/projects/ric_pickup.jpg
importance: 3
category: research
---

Roughly **500,000 US infants** are admitted to a neonatal intensive care unit each year, into care that is among the most physically and cognitively demanding in medicine, and among the least automated. The World Health Organization projects a shortage of **11 million healthcare workers by 2030**, and in the NICU specifically, burnout reaches **37%**.

Our clinical partners have already started asking when they can have a humanoid robot of their own. So we asked the prerequisite question: **can current robots physically handle an infant safely enough to help?**

> **This project is in active development.** The paper is targeted at ICRA 2027; the results and figures below are work in progress.

### Why nobody had answered it

Existing automation in infant care monitors babies or passively soothes them. Nothing touches them. The obstacle isn't the motion, it's the tolerances. A neonate withstands a fraction of the mechanical load an adult can, and the head must stay within a narrow angular range throughout a lift or the airway is compromised. Those limits are clinically specified and unforgiving, and they are the reason infant handling has stayed manual.

We picked the two interventions that matter most:

**Bimanual pickup.** Infants in the NICU are handled for roughly **2.5 hours every day**, and a pickup bookends nearly every one of those episodes: weighing, feeding, imaging, line management, and repositioning all begin and end with the infant being lifted.

**CPAP nasal-mask repositioning.** CPAP is the first-line noninvasive therapy for preterm infants in respiratory distress, and nasal masks need frequent nurse-initiated repositioning (our clinical partners reported up to **50 times a day**) to preserve the seal. Each adjustment is a force balance: too little and the seal leaks; too much and contact pressure causes nasal skin breakdown, which affects a majority of infants on long-duration support.

The two fail in completely different ways: inertial and postural on one side, sustained contact pressure on the other. That is exactly why a safety methodology for infant handling has to generalize beyond a single task.

<div class="row justify-content-center">
    <div class="col-sm-9">
        {% include figure.liquid loading="eager" path="assets/img/projects/ric_pickup.jpg" title="Safe and unsafe pickup" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Top: head–torso pitch beyond the clinical limit, compromising the airway. Bottom: a lift within limits, the hand supporting both neck and back.</div>
    </div>
</div>

### Turning clinical judgment into numbers

I worked with **four neonatal clinicians** (a NICU nurse, a NICU physician, and two neonatal respiratory therapists) plus the literature they pointed us to, converting "safe handling" into quantities you can measure continuously during a trial:

- **Pickup:** cervical pitch (the head–torso angle that governs airway patency) and head acceleration.
- **CPAP:** interface pressure at the nasal bridge and philtrum, geometric exclusion zones around the eyes and mouth, and a hard time budget on PEEP interruption, since even brief losses of positive pressure risk lung de-recruitment.

### Measuring what a robot actually does

We benchmark three ways of performing each task, **direct human handling, teleoperation, and an autonomous learned policy (ACT)**, on a Unitree G1 humanoid, using an instrumented infant manikin tracked by OptiTrack, and a Fisher & Paykel nasal mask I rebuilt with embedded force sensors to read interface pressure at the contact points clinicians actually worry about. Every trial is verified against the thresholds above, so "safe" is a measurement rather than an impression.

<div class="row justify-content-center">
    <div class="col-sm-9">
        {% include figure.liquid loading="lazy" path="assets/img/projects/ric_pipeline.png" title="RIC system pipeline" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The pipeline: OptiTrack tracks the manikin and computes the safety quantities; teleoperated demonstrations become training data; the learned policy runs on the humanoid and is scored against the same thresholds.</div>
    </div>
</div>

{% include figure.liquid loading="lazy" path="assets/img/projects/ric_mask.jpg" title="Instrumented CPAP mask and facial safety zones" class="img-fluid rounded z-depth-1" %}
<div class="caption">Left: the molded nasal mask, green marking the three embedded force sensors. Right: the safety map on the face, with red exclusion zones over the eyes and mouth, yellow pressure-sensitive areas, and the green nasal target the mask must reach.</div>

Project lead and first author; targeted at ICRA 2027.

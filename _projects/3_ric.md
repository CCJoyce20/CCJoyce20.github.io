---
layout: page
title: "CRIB: Can Robots Handle Infants?"
description: "Clinical Robotics for the Infant Bedside: benchmarking robots against the clinical safety limits for handling babies (project lead; first author, submitted to ICRA 2027)"
img: assets/img/projects/ric_pickup.jpg
date_range: 2024 to 2026
importance: 3
category: research
---

Roughly **500,000 US infants** are admitted to a neonatal intensive care unit each year, into care that is among the most physically and cognitively demanding in medicine, and among the least automated. The World Health Organization projects a shortage of **11 million healthcare workers by 2030**, and in the NICU specifically, burnout reaches **37%**.

Our clinical partners have already started asking when they can have a humanoid robot of their own. So we asked the prerequisite question: **can current robots physically handle an infant safely enough to help?**

> The paper is submitted to ICRA 2027.

### Why nobody had answered it

Existing automation in infant care monitors babies or passively soothes them. Nothing touches them. The obstacle isn't the motion, it's the tolerances. A neonate withstands a fraction of the mechanical load an adult can, and the head must stay within a narrow angular range throughout a lift or the airway is compromised. Those limits are clinically specified and unforgiving, and no robot had ever been measured against them.

We picked two interventions that fail in completely different ways:

**Bimanual pickup.** Infants in the NICU are handled for roughly **2.5 hours every day**, and a pickup bookends nearly every one of those interactions. The risk is inertial and postural.

**CPAP nasal-mask repositioning.** CPAP is the first-line noninvasive therapy for preterm infants in respiratory distress, and nasal masks need frequent repositioning (our clinical partners reported up to **50 times a day**) to keep the seal. Each adjustment is a force balance: too little and the seal leaks, too much and contact pressure causes the nasal skin breakdown seen in 20 to 60% of preterm infants on long-duration support.

<div class="row justify-content-center">
    <div class="col-sm-9">
        {% include figure.liquid loading="eager" path="assets/img/projects/ric_pickup.jpg" title="Safe and unsafe pickup" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Top: head–torso pitch beyond the clinical limit, compromising the airway. Bottom: a lift within limits, the hand supporting both neck and back.</div>
    </div>
</div>

### Turning clinical judgment into numbers

**CRIB** stands for Clinical Robotics for the Infant Bedside. I worked with **four neonatal clinicians** (a NICU physician, a NICU nurse, and two neonatal respiratory therapists) plus the literature they pointed us to, converting "safe handling" into quantities measured continuously on the infant rather than on the robot. That choice is what lets the same scoring apply to a human, a teleoperated robot, and a learned policy alike.

- **Pickup:** head–torso pitch (which governs whether the airway stays open) and head acceleration, both checked throughout the lift, not just at the end.
- **CPAP:** contact force at each of three sites on the nose (the bridge and both sides of the base), capped at a bound drawn from measurements of NICU staff; exclusion zones around the eyes and mouth; and a 15-second deadline to reseat the mask, the tolerance clinicians work to before lost pressure risks lung injury.

<div class="row justify-content-center">
    <div class="col-sm-4">
        {% include figure.liquid loading="lazy" path="assets/img/projects/ric_cpap_setup.jpg" title="CPAP repositioning setup" class="img-fluid rounded z-depth-1" %}
        <div class="caption">Top: the CPAP mask on the infant manikin. Bottom: the arm-mounted mask approaching the instrumented face.</div>
    </div>
    <div class="col-sm-4">
        {% include figure.liquid loading="lazy" path="assets/img/projects/ric_zones.jpg" title="Facial safety zones" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The safety map: red exclusion zones over the eyes and mouth, and the nasal target the mask must reach.</div>
    </div>
</div>

### Measuring what a robot actually does

Pickup runs on a **Unitree G1 humanoid**, chosen because a two-handed lift needs a bimanual form factor, and CPAP on one arm of an **OpenArm**, whose backdrivable actuation suits sustained force control. Both share one platform: a 3D-printed infant manikin tracked by OptiTrack (registration verified to 0.33 mm), one teleoperation interface, and one record format.

For CPAP, I rebuilt a clinical infant nasal mask so it could measure what it does to the face. A real silicone cushion seals by deforming, so springs reproduce that compliance, and a force sensor at each of the three nasal sites reads the load the mask applies.

<div class="row justify-content-center">
    <div class="col-sm-8">
        {% include figure.liquid loading="lazy" path="assets/img/projects/ric_mask_force.jpg" title="Instrumented mask, safe vs. excessive force" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The instrumented mask seated with a safe level of force (left) and pressing too hard (right).</div>
    </div>
</div>

We benchmarked four ways of doing each task: **direct human handling** (ten caregivers), **expert and novice teleoperation**, and an **autonomous learned policy (ACT)** trained on the expert's demonstrations. Every one of the 641 instrumented trials is scored against the same clinical limits, so "safe" is a measurement rather than an impression.

<div class="row justify-content-center">
    <div class="col-sm-9">
        {% include figure.liquid loading="lazy" path="assets/img/projects/ric_pipeline.png" title="CRIB system pipeline" class="img-fluid rounded z-depth-1" %}
        <div class="caption">The pipeline: OptiTrack tracks the manikin and computes the safety quantities; teleoperated demonstrations become training data; the learned policy runs on the robot and is scored against the same limits.</div>
    </div>
</div>

### What we found

| | Pickup success | CPAP success |
|:--|:--:|:--:|
| Direct human handling | 100% | 1.7% |
| Expert teleoperation | 91% | 61% |
| Novice teleoperation | 87% | 5.6% |
| Learned policy (ACT) | 83% | 32% |
{: .table .table-sm}

**On pickup, humans win.** The limits there are ones a caregiver senses directly, and people met them on every completed trial. The three robot conditions don't differ statistically from one another, and the policy performs within range of the expert it learned from, so the gap is already present in expert teleoperation: the barrier is the robot's body, not the policy. Head acceleration almost never mattered (2 of 288 pickups exceeded it); posture did. About three-quarters of every robot trial is spent just getting its hands underneath the infant.

**On CPAP, the ordering reverses.** People seat the mask quickly and easily, but press far too hard: a median of 20.9 kPa against the 12.9 kPa bound, because contact pressure is almost impossible to judge by hand, and people press harder to be sure. The expert teleoperator stayed inside the bound 61% of the time. The policy's usual failure was different: it stopped short, holding the mask against the face without ever loading all three sites.

<div class="row justify-content-center">
    <div class="col-sm-10">
        {% include figure.liquid loading="lazy" path="assets/img/projects/ric_traces.jpg" title="Single-trial safety traces" class="img-fluid rounded z-depth-1" zoomable=true %}
        <div class="caption">One safety quantity per panel. (a) A novice-teleoperated pickup crossing the neck-angle limit within a second of load transfer. (b) A pickup crossing the acceleration limit. (c) The policy's characteristic CPAP failure, one nasal site overloaded while the opposite barely makes contact, against (d) a safe expert placement.</div>
    </div>
</div>

Across both tasks the lesson is the same: **the remaining problem is sustaining force regulation through contact**. The handler, human or robot, works without contact information. That points the next steps at tactile and force sensing on the robot, and at enforcing the clinical bound during demonstration collection, and it is the same gap PHABS attacks from the teleoperation side.

### What went wrong, and what it taught us

The first hands we tried failed in a way that turned out to be one of the most informative results of the project. A person lifting an infant works their fingers underneath and wiggles them to free the bedding, reaching a supporting position under the head and back before any weight transfers. Our candidate robot hands could not do this: they lacked the degrees of freedom, and their fingers caught on the bedding.

We replaced them with smooth, rigid plastic hands, trading dexterity for reliable entry. That forced a scoop strategy rather than pre-shaping around the infant, which leaves the head and back less supported at the moment of load transfer, and it explains why posture, not acceleration, is the binding limit. The failures are not caused by jerky motion; they are caused by the configuration the robot can reach before the lift begins.

Project lead and first author.

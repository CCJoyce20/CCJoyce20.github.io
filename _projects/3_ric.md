---
layout: page
title: "RIC: Can Robots Handle Infants?"
description: "Robotic Infant Care — the first framework for robots that physically handle babies (project lead; first author, ICRA 2027)"
# img: assets/img/projects/ric.jpg  # TODO: add cover image
importance: 3
category: medical robotics
---

**Can a robot safely pick up a baby?** Nobody had asked that question in a way you could answer with numbers, so we built the framework to answer it.

NICU nurses face 37% burnout, yet infant care is one of the least automated corners of healthcare, because a neonate tolerates a fraction of adult mechanical loads and no robot has ever been evaluated against the clinical bar. RIC targets the NICU's most frequent physical interventions: **bimanual infant pickup** and **CPAP nasal-mask repositioning**.

**What I built:** working with four NICU clinicians, we formalized safety as continuously measurable thresholds — cervical pitch and head acceleration for pickup; contact pressure, eye/mouth exclusion zones, and a PEEP-interruption time budget for CPAP. On a Unitree G1 humanoid, we benchmark direct-human, teleoperated, and autonomous (ACT) execution using a REMI-manikin OptiTrack pipeline and a pressure-sensing molded CPAP mask, verifying every trial against the thresholds.

First-author paper targeted at ICRA 2027.

<!-- TODO: add photos - G1 lifting REMI, CPAP mask with FSRs, OptiTrack setup -->

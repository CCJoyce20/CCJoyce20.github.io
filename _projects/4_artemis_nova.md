---
layout: page
title: NICU Camera Mount → NOVA Trial
description: "ArtemisAI Labs: from consumer phone holder to hospital-deployable hardware, now fielding a Phase II neonatal trial"
img: assets/img/projects/artemis_mount.jpg
importance: 4
category: product development
---

ArtemisAI's NOVA trial needs a camera looking into an incubator, held steady, for hours, at the bedside of the most fragile patients in the hospital. Version zero was a consumer gooseneck phone holder. My job was turning that into hardware a hospital can actually deploy.

<div class="row justify-content-center">
    <div class="col-sm-7">
        {% include figure.liquid loading="eager" path="assets/img/projects/artemis_mount.jpg" title="Camera mount over a NICU incubator" class="img-fluid rounded z-depth-1" %}
        <div class="caption">An earlier version of the mount positioned over an incubator, holding the camera that feeds ArtemisAI's pose-tracking model, here running on a training manikin rather than a patient.</div>
    </div>
</div>

### Three constraints that shaped everything

The requirements that came back from the clinical side were blunt, and each one drove real design decisions:

1. **It cannot fall on the baby.** Mass cantilevered high on an IV pole is what creates tip risk, so weight belongs low and the clamp has to genuinely grip.
2. **The phone cannot be stolen.** A consumer phone at an unattended bedside walks away; retention had to be designed in, not assumed.
3. **The whole screen has to stay usable.** Staff need to touch it, so no bracket or clip can cross the display, and the charge port must stay reachable without disassembly.

A fourth, self-imposed: **as few custom parts as possible.** Every custom part is tooling, lead time, and another thing to re-qualify.

### The real design driver isn't the payload

The phone, machined case, and hardware come to roughly half a kilogram, trivial to hold up. What actually sizes the design is **what a person can do to it**: a caregiver snagging a cable, bumping the arm, or leaning on the phone applies 10–25 lbf without trying, and a deliberate pull exceeds 50. On an 18-inch arm, a 15 lbf snag becomes ~30 N·m at the pole clamp.

And the failure mode that matters isn't the clamp breaking. It's the clamp **rotating or sliding down the pole**, which silently ruins the camera framing the trial depends on, and in the worst case swings mass over the infant. So grip, not strength, became the spec to chase. For rough-handling loads I benchmarked against the IEC 60601-1 instability push test, which gave a defensible number to hold manufacturers to.

### From one part to three specifications

I split the integrated consumer unit into three independently specifiable parts, **IV pole clamp, gooseneck arm, phone-holder interface**, so each could be quoted, rated, and upgraded on its own. Then I wrote what each had to meet:

- **Clamp:** capture 7/8″–1.25″ poles (hospital poles vary), no rotation or vertical slip at ≥30 N·m, survive a 50 lbf pull without releasing, anodized aluminum or stainless.
- **Gooseneck:** ≥2 lb rating at full horizontal extension, no visible droop over 24 hours under load, and, the requirement vendors never publish, **≥10,000 reposition cycles retaining ≥80% stiffness**, sized from ~10 adjustments a day over a two-year service life. Goosenecks don't snap; they sag, and a sagging arm is a dead trial.
- **Interface:** a rear-mounted threaded boss machined integral to the case, so the charge port stays clear, the arm stays out of the camera's sightline, and there's no bonded joint to degrade.

Because payload margin on an 18″ arm is only ~1.6× with a machined case, I set a mass budget for the case rather than discovering the droop later.

### Designing for infection control

The mount is wiped with hydrogen peroxide daily and between patients, and **no disassembly is permitted for cleaning**. That single constraint propagated everywhere: it ruled out the 3D-printed route I'd otherwise have prototyped in (layer lines and grooves trap soil and can't be reliably wiped), and it set the rules for everything else, no fabric or porous materials, no deep crevices or trapped seams, fasteners flush, every external surface reachable with a wipe, and mechanical fastening preferred over adhesives that go tacky under repeated peroxide exposure.

### Making it buildable

I ran two tracks in parallel, a fast off-the-shelf assembly and a branded custom build, so the program could trade cost, lead time, and appearance with real numbers instead of guesses. For the build itself I wrote the assembly protocol and bill of materials so labor could be quoted separately from parts: eight steps, roughly 30 minutes a unit, no soldering or adhesives, plus a per-unit functional checklist (phone retained without rattle, cameras unobstructed, charge port reachable, clamp holds against a firm sideways push, no sharp edges anywhere).

That mount now fields the cameras for **NOVA (Neonatal AI Vision Assessment)**, ArtemisAI's Phase II multi-center clinical trial of computer-vision neurological monitoring of newborns, running at Mount Sinai. I'm currently qualifying assembly partners to kit and ship units to hospitals purchasing the device.

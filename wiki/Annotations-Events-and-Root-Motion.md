# Annotations, Events & Root Motion

Animations are more than poses. Skyrim runtime systems often need exact-frame metadata for footsteps, attacks, interaction events, root motion and paired behavior.

---

## Annotation authoring tools

### Skyrim Annotation Blender Add-on
https://github.com/skypia0147-dev/blender-skyrim-annotation

Best for authoring/managing Skyrim animation markers directly in Blender, especially when ordinary marker-name limits make long event strings awkward.

### HKXC Anno GUI 2.0
https://www.nexusmods.com/skyrimspecialedition/mods/166435

Modern standalone annotation workflow for LE/SSE HKX, including paired-animation support. Preferred over older hkanno64/HKANNO GUI chains for new work.

### PyNifly
https://github.com/BadDogSkyrim/PyNifly

Its animation workflow can map HKX annotations to/from Blender timeline markers, making round-trip event inspection possible.

---

## What annotations can represent

Depending on the runtime/framework:
- footsteps
- hit/attack windows
- gameplay animation events
- paired events
- Precision-related markers
- AMR movement commands
- Payload Interpreter payloads
- framework-specific event commands

Treat annotation spelling, timing and target framework as part of the animation's API contract.

---

# Root motion: three different things

## 1. Visual body translation
The skeleton/root/pelvis visibly moves relative to the actor.

## 2. Havok/extracted motion data
Animation-format-level motion/reference-frame data.

## 3. Skyrim actor-world displacement
The actor's game-world transform changes.

Do not assume one automatically gives you the others.

---

## Animation Motion Revolution (AMR)

https://www.nexusmods.com/skyrimspecialedition/mods/50258

Use when the actor must physically translate/rotate through the world in sync with the animation.

Typical workflow concept:
1. author the visual motion
2. define intended world displacement/rotation
3. encode the runtime motion annotations
4. verify frame timing
5. test in isolation
6. test again under combat/interaction frameworks

---

## Animation Motion Fix

https://www.nexusmods.com/skyrimspecialedition/mods/145100

A current 2026 runtime fix worth testing when root motion becomes reduced, stuck or behaves differently under combat/runtime conditions.

If motion works out of combat but not during combat, that is a strong clue to investigate runtime handling before re-exporting the HKX.

---

## Apply Impulse

https://www.nexusmods.com/skyrimspecialedition/mods/181584

2026 specialist utility for exact-frame engine impulse or timed actor rotation through animation annotation payloads.

Use when an animation should impart physical force/rotation at a specific moment.

**Do not confuse engine impulse with authored root motion.** They solve different problems.

---

## Payload Interpreter

https://www.nexusmods.com/skyrimspecialedition/mods/65089

Source:
https://github.com/D7ry/PayloadInterpreter

Powerful for animation-event payload logic in supported setups.

### 2026 compatibility caution
Current user reports around Skyrim **1.6.1170** are mixed across files/configurations. Validate:
- exact Skyrim runtime
- exact SKSE
- exact Payload Interpreter file/DLL
- dependent framework versions

Do not make it a hard dependency until that exact combination is proven.

---

## Paired/combat events

For paired events:
- [Paired Animation Improvements](https://www.nexusmods.com/skyrimspecialedition/mods/99621)

For advanced annotation-driven combat/paired triggers:
- [Trigger Combat Behaviour](https://www.nexusmods.com/skyrimspecialedition/mods/167256)

For collision timing:
- [Precision](https://www.nexusmods.com/skyrimspecialedition/mods/72347)

---

## Event verification workflow

1. Inspect intended event list before export.
2. Export HKX.
3. Dump/reopen annotations from the finished HKX.
4. Compare event text and timestamp/frame.
5. Test the animation without advanced runtime logic first.
6. Enable one runtime system at a time.
7. Record which system consumes each event.

---

## Root-motion acceptance checklist

- [ ] visual root/body translation is correct
- [ ] actor-world travel is explicitly intended
- [ ] annotation text verified after export
- [ ] translation/rotation timing matches visual motion
- [ ] works in minimal runtime test
- [ ] works under combat/interaction framework if applicable
- [ ] no double-motion from two systems moving the actor simultaneously

Next: **[OAR & Runtime Deployment](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/OAR-and-Runtime-Deployment)**.
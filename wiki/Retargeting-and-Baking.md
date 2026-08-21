# Retargeting & Baking

The goal of retargeting is not to preserve the source rig. It is to produce a **self-contained Skyrim target animation** that reproduces the trusted evaluated source.

---

## Choose one target rig family

### Coach's Enhanced Blender Animation Rigs
https://www.nexusmods.com/skyrimspecialedition/mods/148736

Strong for:
- first person / third person
- IK/FK controls
- Skyrim-oriented annotation/root-motion helpers
- bulk workflows

### NickNak Blender Animation Rigs
https://www.nexusmods.com/skyrimspecialedition/mods/118525

Strong current Blender 5 XP32/paired authoring family.

### RigifyRig by Bogdan
https://www.nexusmods.com/skyrimspecialedition/mods/180970

Strong current Rigify-oriented option.

### Generic retarget helper
[Retarget for Blender 5+](https://github.com/KBSBAUDRICE/Retarget) includes an MMD preset and root-motion tools.

### Optional Cascadeur polish
https://cascadeur.com/download

Skyrim rigs: https://www.nexusmods.com/skyrimspecialedition/mods/121536

Use Cascadeur only when its physics/posing tools materially improve the motion; every extra DCC boundary is another transform/resampling risk.

---

## Keep one authoritative export skeleton

You may use a control rig, but the final output path should have **one clear deform/export skeleton**.

Avoid:
- duplicate Skyrim armatures
- target bones driven by multiple competing constraint systems
- exporting control bones that the game skeleton does not contain
- accidentally targeting a different skeleton than your deployed game setup

---

## Retarget map design

### Anatomical mapping
Map:
- spine chain
- neck/head
- clavicles/arms/hands
- legs/feet/toes
- fingers where supported/needed

### MMD body controls
Treat separately:
- Center
- Groove
- Mother
- Waist/lower-body
- IK controllers

The final mapping depends on the target rig, but the principle is constant: **transfer evaluated motion semantics, not only matching bone names.**

---

## Coordinate / rest-pose issues

Before blaming motion curves, confirm:
- rest pose alignment
- scale
- axis orientation
- target skeleton rest transforms
- left/right bone mapping
- parent hierarchy

A correct animation applied to the wrong rest-pose assumptions will look broken even if every keyframe is present.

---

## Visual bake procedure

1. Complete the constraint/retarget setup.
2. Scrub reference frames and compare with source.
3. Set the intended scene FPS.
4. Bake the **evaluated visual target** over the full range.
5. Include location where required and rotation for animated bones.
6. Use per-frame sampling when the source depends on IK/constraints/interpolation that must be made deterministic.
7. Disable source constraints.
8. Hide/remove the source armature from the playback test.
9. Compare again.

### Why visual/evaluated baking matters

Raw source F-curves do not necessarily represent:
- final IK result
- constraint evaluation
- layered MMD Center/Groove result
- retarget offsets
- target rest-pose correction

The game needs the **finished target transform**, not your Blender dependency graph.

---

## FPS / timing

30 FPS is the normal Skyrim/Havok animation baseline in this research.

Before and after bake, record:
- frame start/end
- scene FPS
- duration in seconds
- event frames

Never silently change duration while resampling.

---

## Bake acceptance test

Disable/remove:
- copy transforms
- IK retarget constraints
- source drivers
- source-parent relationships not part of the actual export skeleton

Then verify:
- no visible pose change
- same bounce extrema
- same foot contacts
- same hand targets
- same turns
- same duration

If anything changes, fix the bake before HKX export.

---

## Root placement strategy

Separate three concepts:

1. **Pose motion** — limb/body rotation.
2. **Visual body translation** — pelvis/root/COM moves within the animation.
3. **Actor-world displacement** — Skyrim moves the actor object through the game world.

The first two are authoring/bake concerns. The third is a runtime/root-motion concern and may require AMR or other intentional integration.

---

## Common retarget failures

| Failure | Likely reason |
|---|---|
| animation changes after constraints off | incomplete visual bake |
| feet slide | source IK mismatch or retarget/root translation issue |
| body floats | Center/Groove translation routed incorrectly |
| turns lean/offset | rest-pose/axis/parent mismatch |
| one side mirrors wrong | left/right map error |
| correct Blender motion but broken HKX | skeleton/export stage, not retarget stage |

Next: **[Skyrim Skeletons & HKX](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Skyrim-Skeletons-and-HKX)**.
# MMD Motion Fidelity — Center, Groove, Mother, IK & the “Missing Bounce” Problem

A VMD can look mostly correct while losing the exact motion that makes it feel alive. The classic symptom is:

> **The dance/pose survives, but vertical body bounce, sway or travel disappears.**

That is usually a **source-control-layer problem**, not an HKX problem.

---

## Why MMD motion is easy to misread

MMD rigs often simulate layered motion using multiple bones/controllers rather than one conventional game-engine root hierarchy.

Important controls include:

### Center `センター`
A major body-position controller. Translation here can carry large portions of body travel/bounce.

### Groove `グルーブ`
Often layered above/beside Center to add extra vertical/positional motion.

### Mother / All Parent `全ての親`
A higher-level whole-model transform. Some motions use it more heavily than others.

### Waist / lower-body controls
Can contribute body orientation and local offsets that are easy to flatten incorrectly.

### Leg-D / IK controllers
MMD leg/foot contact can depend on solver behavior that does not match Blender automatically.

---

## Why an old FBX path can lose bounce

A workflow such as:

`VMD → old Blender → FBX → 3ds Max → Havok`

can preserve many bone rotations while losing or reinterpreting layered controller translation.

The resulting motion may still look like the same dance while its vertical center-of-mass character is gone.

The fix is **not** to randomly add pelvis keys later. The fix is to identify where the intended motion exists in the evaluated source and transfer that result deliberately.

---

## Diagnostic procedure

### 1. Choose unmistakable frames
Find:
- highest bounce
- lowest bounce
- largest whole-body shift
- large turn
- clear foot plant

### 2. Inspect controller transforms
At those frames inspect:
- Center
- Groove
- Mother
- Waist/lower body
- pelvis/hips
- leg IK

### 3. Compare evaluated world position
The important question is not only “does this bone have keys?” but:

**Where is the body after the full MMD hierarchy and IK have evaluated?**

### 4. Compare Blender with trusted MMD playback
If Blender differs before Skyrim retargeting, use [MMDBridge](https://github.com/rintrint/mmdbridge) or another source-side fidelity solution.

---

## Correct transfer strategy

### Bad strategy
`MMD hips → Skyrim pelvis`

### Better strategy
1. Evaluate the full MMD hierarchy.
2. Transfer anatomical rotations normally.
3. Combine/route Center/Groove/Mother/body translation intentionally into the Skyrim target/root/pelvis system appropriate to that rig.
4. Bake the final **visual target pose every frame**.
5. Disable source constraints and compare.

[Blender VMD Retargeting](https://github.com/butaixianran/Blender-Vmd-Retargeting) is useful reference material because it explicitly treats Center/Groove/Waist as layered motion and supports evaluated-frame retargeting methodology.

---

## When to use source repair tools

| Symptom | Tool worth testing |
|---|---|
| Unsure which controls are used | Finekit VMD Checker |
| Mother/Center usage is problematic | Finekit VMDTMS / MMD MotionSupporter |
| Leg IK differs | Finekit VMD Bake / MMDBridge |
| Model proportions differ strongly | Finekit VMD Retarget / VMD Sizing |
| Layer/interpolation semantics keep collapsing | MikuMikuMoving `Integrate Layer` fallback |
| Blender IK/physics differs from MMD | MMDBridge |

Finekit: https://www.finekit.co.jp/base/index2e.html

MotionSupporter: https://bowlroll.net/file/233713

VMD Sizing: https://github.com/miu200521358/vmd_sizing

MikuMikuMoving: https://sites.google.com/site/mikumikumovingeng/

---

## Bake evaluated results, not raw assumptions

The final Skyrim target should contain ordinary transform keys that reproduce the intended evaluated pose without depending on the MMD rig.

After baking:

1. disable all retarget constraints
2. hide the source rig
3. scrub the entire timeline
4. compare high/low frames
5. compare feet/hands
6. compare motion arcs

If the target changes when constraints are disabled, it is not finished.

---

## Visual bounce vs actual actor movement

Preserving Center/Groove motion may restore **visible body translation**. That does not automatically make Skyrim's actor object move through the world.

For intentional actor-world displacement, see **[Annotations, Events & Root Motion](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Annotations-Events-and-Root-Motion)**.

---

## Fidelity checklist

- [ ] Original VMD is preserved.
- [ ] Center/Groove/Mother channels inspected.
- [ ] Blender result compared to trusted source.
- [ ] IK/physics difference resolved before Skyrim mapping.
- [ ] Whole evaluated body motion transferred intentionally.
- [ ] Target baked visually every frame.
- [ ] Target survives removal of source constraints.
- [ ] Highest/lowest bounce still matches.

Next: **[Retargeting & Baking](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Retargeting-and-Baking)**.
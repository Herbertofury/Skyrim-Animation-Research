# VMD / MMD Source Preparation

The best Skyrim export cannot recover motion that was already lost before retargeting. This page keeps the **MMD source authoritative** until its motion is fully understood.

## Preserve the source

Keep untouched copies of:
- `.vmd`
- `.pmx` / `.pmd`
- textures and model dependencies
- any source notes about FPS or intended model

Create a separate working copy for every destructive bake/repair experiment.

---

## Preflight before Blender

### Finekit VMD Checker
https://www.finekit.co.jp/base/index2e.html

Use it to identify which bones/morphs the VMD actually uses.

Pay special attention to:
- Center `センター`
- Groove `グルーブ`
- Mother / All Parent `全ての親`
- Waist / lower-body controllers
- Leg-D
- foot/leg IK
- arm/hand IK where present
- camera/light/morph channels if relevant

Create a short list of reference frames where each important motion component is obvious.

---

## Import with MMD Tools

Official extension:
https://extensions.blender.org/add-ons/mmd-tools/

Source:
https://github.com/MMD-Blender/blender_mmd_tools

Current research snapshot:
- MMD Tools **4.5.13**
- current v4.x README explicitly documents Blender **4.2–5.1**
- Blender 5.2 LTS is newer, but do not call 5.2 officially documented for MMD Tools until the project does

### Import discipline

- Keep original MMD bone names during diagnosis.
- Do not delete helper/control bones immediately.
- Do not start Skyrim retargeting until the imported MMD motion is proven.
- Match source FPS/timing before comparing frames.

---

## Compare source vs Blender

Use a frame comparison table while diagnosing:

| Frame | What to inspect | Source | Blender | Match? |
|---|---|---|---|---|
| highest vertical bounce | Center/Groove/body height |  |  |  |
| lowest bounce | Center/Groove/body height |  |  |  |
| left foot plant | leg IK/foot location |  |  |  |
| right foot plant | leg IK/foot location |  |  |  |
| large turn | Mother/Center/body yaw |  |  |  |
| hand contact | arm/hand target |  |  |  |

If the source and Blender differ here, **do not blame Skyrim**.

---

## Source repair tools — use only when justified

### Finekit VMDTMS
https://www.finekit.co.jp/base/index2e.html

Useful for:
- Mother → Center mixing
- twist separation
- Leg-D-related processing
- vertical/up-down correction
- motion optimization

### Finekit VMD Retarget
https://www.finekit.co.jp/base/index2e.html

Useful when source/target MMD characters have different:
- bone angles
- proportions
- leg-IK geometry

### Finekit VMD Bake
https://www.finekit.co.jp/base/index2e.html

Useful when leg IK is the unstable part of the conversion and you want a more deterministic baked result.

### MMD MotionSupporter
https://bowlroll.net/file/233713

Use for specialist repairs such as:
- Mother / All-Parent transfer
- leg FK → IK conversion

### VMD Sizing
https://github.com/miu200521358/vmd_sizing

Useful for strong proportion differences before the Skyrim retarget stage.

### MikuMikuMoving `Integrate Layer`
https://sites.google.com/site/mikumikumovingeng/

A legacy but uniquely useful fallback when layered/interpolated motion keeps collapsing downstream. Dense per-frame motion can make the intended result explicit.

---

## MMDBridge fidelity fallback

Maintained fork:
https://github.com/rintrint/mmdbridge

MMD Tools documentation warns that Blender's IK solver differs from MMD. If the imported pose/motion differs because of solver/physics behavior, use MMD-native evaluation rather than hand-correcting symptoms in the Skyrim target.

---

## Optional MMD editing helpers

- MMD Tools Append: https://github.com/MMD-Blender/blender_mmd_tools_append
- MikuMikuRig rewrite: https://github.com/XiaoFFGe/MikuMikuRig
- Blender VMD Retargeting: https://github.com/butaixianran/Blender-Vmd-Retargeting
- Retarget for Blender 5+: https://github.com/KBSBAUDRICE/Retarget

These improve editing/retarget workflows, but none replaces the need to prove source fidelity first.

---

## Source-prep acceptance gate

Do not continue until:

- [ ] timing matches the source
- [ ] highest/lowest body movement matches
- [ ] foot plants match
- [ ] important turns match
- [ ] IK differences are understood
- [ ] Center/Groove/Mother usage is known
- [ ] any repair/bake was intentional and compared against an untouched source

Next: **[MMD Motion Fidelity](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/MMD-Motion-Fidelity)**.
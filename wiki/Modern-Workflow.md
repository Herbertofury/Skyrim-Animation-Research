# Modern 2026 VMD / MMD → Skyrim HKX Workflow

This is the recommended end-to-end path. Each stage has a **proof gate**; do not move forward with a broken upstream result.

> **Fast path:** `VMD/MMD → verify → MMD Tools → diagnose layered controls → evaluated retarget → Skyrim skeleton.hkx → visual bake → direct HKX export → fresh re-import → annotations → OAR`

---

## Phase 0 — Define the target

Before touching the source, record:

- Skyrim LE / SE / AE / VR
- exact game runtime if SKSE plugins are involved
- target skeleton: vanilla / XPMSSE / custom
- first-person / third-person / paired / creature / cinematic
- replacement vs new behavior
- visual motion vs true actor-world displacement

This prevents later format/skeleton/runtime ambiguity.

---

## Phase 1 — Preserve and prove the source

### 1. Preserve untouched originals
Keep the original VMD, PMX/PMD and any source model/config files unchanged.

### 2. Preflight the VMD
Use [Finekit VMD Checker](https://www.finekit.co.jp/base/index2e.html) and/or inspect the source rig directly.

Check:
- Center `センター`
- Groove `グルーブ`
- Waist / lower-body controls
- Mother / All Parent `全ての親`
- Leg-D
- IK bones
- morphs

Do not assume the visible bounce or travel lives on a hip/pelvis bone.

### 3. Import using a current MMD stack
Use [MMD Tools 4.5.13](https://extensions.blender.org/add-ons/mmd-tools/).

Its current README explicitly documents Blender **4.2–5.1** for the current v4.x line. Blender 5.2 LTS is current and PyNifly supports it, but MMD Tools does not yet explicitly document 5.2.

Keep Japanese/original MMD bone names during diagnosis.

### 4. Compare against the original
Pick reference frames:
- highest bounce
- lowest bounce
- left/right foot contacts
- large turns
- hand targets
- physics-heavy frames

If Blender already differs, **stop here**.

### 5. Fix source evaluation only if proven necessary
If Blender's MMD result differs from the source:

- [MMDBridge maintained fork](https://github.com/rintrint/mmdbridge) — MMD-native IK/physics fidelity fallback.
- [Finekit VMDTMS](https://www.finekit.co.jp/base/index2e.html) — Mother/Center, twist and motion cleanup.
- [Finekit VMD Retarget](https://www.finekit.co.jp/base/index2e.html) — proportion/bone-angle/IK compensation.
- [Finekit VMD Bake](https://www.finekit.co.jp/base/index2e.html) — unstable leg-IK baking.
- [MMD MotionSupporter](https://bowlroll.net/file/233713) — specialist Mother/All-Parent transfer and FK→IK repair.
- [MikuMikuMoving](https://sites.google.com/site/mikumikumovingeng/) — `Integrate Layer` dense-bake fallback.

**Do not blindly flatten every VMD.** Correct only the proven failure.

### ✅ Gate A — Source fidelity
The evaluated source must visually match the intended MMD motion before retargeting.

---

## Phase 2 — Establish the Skyrim target

### 6. Choose a deliberate sample rate
Normally use **30 FPS** for Skyrim/Havok animation workflows unless the project intentionally requires another rate.

Record:
- source FPS
- source frame count
- duration
- final target frame count

### 7. Import the real `skeleton.hkx`
Use [PyNifly](https://github.com/BadDogSkyrim/PyNifly) and follow its [animation guide](https://github.com/BadDogSkyrim/PyNifly/blob/main/ANIMATIONS.md).

For animation binding, `skeleton.hkx` is authoritative. Do not rely on `skeleton.nif` alone.

### 8. Choose one control-rig family
Good current options:

- [Coach's Enhanced Blender Animation Rigs](https://www.nexusmods.com/skyrimspecialedition/mods/148736)
- [NickNak Blender Animation Rigs](https://www.nexusmods.com/skyrimspecialedition/mods/118525)
- [RigifyRig by Bogdan](https://www.nexusmods.com/skyrimspecialedition/mods/180970)

Use one authoritative deform/export skeleton. Avoid multiple competing Skyrim armatures in the final export path.

### 9. Confirm edition and skeleton identity
Before retargeting, verify:
- LE vs SE/AE format expectations
- exact bone count/order
- vanilla vs XPMSSE/custom tracks
- first/third-person skeleton choice

For custom-skeleton trouble, see [Skyrim Skeletons & HKX](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Skyrim-Skeletons-and-HKX).

---

## Phase 3 — Retarget evaluated motion

### 10. Build an explicit mapping
Map anatomical bones normally, but treat MMD layered motion intentionally.

Do **not** reduce:

`Center + Groove + Waist + Mother → Skyrim pelvis`

into a single naive copy unless you have proven that is what the source requires.

Useful references:
- [Blender VMD Retargeting](https://github.com/butaixianran/Blender-Vmd-Retargeting) — evaluated-frame and Center/Groove/Waist methodology.
- [Retarget for Blender 5+](https://github.com/KBSBAUDRICE/Retarget) — current generic constraint retargeter with MMD preset/root tools.

### 11. Evaluate constraints and IK
Use constraints/control rigs to make the target follow the trusted source result.

Inspect:
- feet
- knees
- hips
- hands
- spine
- head
- root/COM travel
- extreme vertical frames

### 12. Bake the target visually
Bake **evaluated/visual** transforms every frame.

Target requirement:
- location baked where needed
- rotation baked
- source constraints no longer required
- no hidden dependency on source rig/IK

### 13. Disable or remove retarget constraints
The target animation must not visibly change.

### ✅ Gate B — Independent baked target
The Skyrim target must reproduce the intended motion with the source/retarget constraints disabled.

---

## Phase 4 — Export HKX

### 14. Prefer a modern native HKX path
Recommended:

- [PyNifly](https://github.com/BadDogSkyrim/PyNifly)
- [blender-hkx current Coach/Beefclot fork](https://github.com/beefclot/blender-hkx)

For ordinary character animations, do not insert an unnecessary `HKX → KF → HKX` stage.

### 15. Match the target skeleton/edition
Export against the exact target skeleton and intended Skyrim edition/platform.

### 16. Fresh-scene round-trip
Create a **fresh Blender scene**:

1. Import the same `skeleton.hkx`.
2. Import your finished animation HKX.
3. Compare it to the baked target.

Check:
- vertical bounce extrema
- foot contacts
- hands / hips
- duration and frame timing
- root/COM movement
- event frames

### ✅ Gate C — HKX integrity
If the fresh import differs, fix the bake/export/skeleton before opening Skyrim.

---

## Phase 5 — Inspect, annotate and add motion semantics

### 17. Inspect the final HKX
Use:
- [Smooth HKX_View / HKX_Edit](https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184)
- [serde-hkx / hkxc](https://github.com/SARDONYX-sard/serde-hkx)

### 18. Add or repair annotations
Use:
- [Skyrim Annotation Blender Add-on](https://github.com/skypia0147-dev/blender-skyrim-annotation)
- [HKXC Anno GUI](https://www.nexusmods.com/skyrimspecialedition/mods/166435)

Use exact-frame metadata for footsteps, gameplay events, Precision markers, AMR, paired events or project-specific payloads.

### 19. Handle true actor displacement deliberately
Visible root/pelvis movement is not necessarily actor-world displacement.

Use [Animation Motion Revolution](https://www.nexusmods.com/skyrimspecialedition/mods/50258) when physical translation/rotation must follow the animation.

Test [Animation Motion Fix](https://www.nexusmods.com/skyrimspecialedition/mods/145100) if root motion becomes reduced/stuck under runtime conditions.

### ✅ Gate D — Semantic correctness
Annotations and physical displacement occur at the intended frames and do not alter the visual animation unexpectedly.

---

## Phase 6 — Deploy with the simplest runtime path

### 20. Test as a simple OAR replacement first
[Open Animation Replacer](https://www.nexusmods.com/skyrimspecialedition/mods/92109)

[OAR External Tool](https://github.com/skypia0147-dev/OAR-External-Tool)

If an existing animation can be replaced directly, prove the HKX in this minimal setup before adding behavior complexity.

### 21. Add behavior generation only when required
Use [Pandora Behaviour Engine Plus](https://www.nexusmods.com/skyrimspecialedition/mods/133232) only for new behavior/event types or dependencies that actually need behavior generation.

### 22. Treat paired/combat/creature/cinematic runtime as separate layers
Do not debug all systems simultaneously.

See:
- [Paired Animations & Combat](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Paired-Animations-and-Combat)
- [Creatures, Facial & Cinematics](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Creatures-Facial-and-Cinematics)

### ✅ Gate E — Runtime acceptance
The exact intended runtime flow works with no A-pose, silent replacement failure, motion loss, annotation failure or unintended behavior dependency.

---

# Final acceptance checklist

- [ ] Original MMD/source motion verified.
- [ ] Center/Groove/Mother/IK usage understood.
- [ ] Blender evaluation matches the trusted source.
- [ ] Correct Skyrim `skeleton.hkx` used.
- [ ] Target animation baked visually.
- [ ] Retarget constraints removed/disabled without changing motion.
- [ ] Exported HKX round-trips in a fresh scene.
- [ ] Event/annotation timing inspected.
- [ ] Root/world displacement is intentional and separately validated.
- [ ] OAR or intended runtime path loads the animation.
- [ ] Pandora is present only if behavior generation is actually needed.
- [ ] Paired/combat/creature/cinematic logic was tested as its own layer.

For a concrete walk-through, continue to **[Recipes & Examples](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Recipes-and-Examples)**.
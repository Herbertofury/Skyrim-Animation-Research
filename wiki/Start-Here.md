# Start Here

This page is the fastest route from **“I have an animation idea/file”** to **“I know exactly which Skyrim animation workflow to use.”**

## 1. What are you starting with?

### A. I have a VMD / PMX / PMD / MMD motion
Go to **[VMD/MMD Source Preparation](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/VMD-MMD-Source-Preparation)**.

Your default path is:

`VMD + model → verify MMD motion → diagnose Center/Groove/Mother/IK → evaluated retarget → Skyrim skeleton → bake → HKX → OAR`

### B. I want to animate directly for Skyrim in Blender
Go to **[Retargeting & Baking](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Retargeting-and-Baking)**.

Pick **one** control-rig family:
- [Coach's Enhanced Blender Animation Rigs](https://www.nexusmods.com/skyrimspecialedition/mods/148736)
- [NickNak Blender Animation Rigs](https://www.nexusmods.com/skyrimspecialedition/mods/118525)
- [RigifyRig by Bogdan](https://www.nexusmods.com/skyrimspecialedition/mods/180970)

### C. I already have an HKX and just need it in game
Start with **[HKX Export & Validation](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/HKX-Export-and-Validation)**, then **[OAR & Runtime Deployment](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/OAR-and-Runtime-Deployment)**.

### D. I need actual actor travel / root motion
Go to **[Annotations, Events & Root Motion](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Annotations-Events-and-Root-Motion)**.

### E. I am making paired, interaction, or combat animation
Go to **[Paired Animations & Combat](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Paired-Animations-and-Combat)**.

### F. I am using an ancient Blender 2.49 / 3ds Max / Havok / ConvertUI / KF tutorial
Go directly to **[Legacy Migration](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Legacy-Migration)** before spending more time on it.

---

## 2. Decide your runtime target before authoring

Record these before you begin:

- Skyrim LE, SE, AE, or VR?
- Exact game runtime and SKSE version if using SKSE plugins.
- Vanilla skeleton or XPMSSE/custom skeleton?
- Single actor, paired actors, creature, first-person, third-person, or cinematic?
- Simple replacement or entirely new behavior/event?
- Does the actor merely **look like it moves**, or must the actor physically move through the world?

These decisions affect skeleton bindings, HKX format, runtime dependencies, annotations and behavior requirements.

---

## 3. The default 2026 stack

For most VMD → Skyrim character animations:

| Stage | Recommended default |
|---|---|
| MMD source import/evaluation | [MMD Tools 4.5.13](https://extensions.blender.org/add-ons/mmd-tools/) on a documented Blender 4.2–5.1 setup |
| Source diagnostics | [Finekit VMD tools](https://www.finekit.co.jp/base/index2e.html) |
| Fidelity fallback | [MMDBridge maintained fork](https://github.com/rintrint/mmdbridge) |
| Skyrim skeleton/HKX | [PyNifly](https://github.com/BadDogSkyrim/PyNifly) |
| Control rig | Coach / NickNak / RigifyRig depending preference |
| HKX QA | [HKX_View/Edit](https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184) + [serde-hkx](https://github.com/SARDONYX-sard/serde-hkx) |
| Annotations | [Skyrim Annotation add-on](https://github.com/skypia0147-dev/blender-skyrim-annotation) or [HKXC Anno GUI](https://www.nexusmods.com/skyrimspecialedition/mods/166435) |
| Runtime replacement | [OAR](https://www.nexusmods.com/skyrimspecialedition/mods/92109) |
| New behaviors only | [Pandora](https://www.nexusmods.com/skyrimspecialedition/mods/133232) |
| True world displacement | [AMR](https://www.nexusmods.com/skyrimspecialedition/mods/50258) |

---

## 4. The five verification gates

Do not advance until each gate is green.

### Gate 1 — Source
The original motion looks correct in the source environment.

### Gate 2 — Blender/MMD evaluation
The imported/evaluated MMD result still matches the source at important frames.

### Gate 3 — Baked Skyrim target
Disable all retarget constraints. The target must not change.

### Gate 4 — HKX round-trip
Fresh Blender scene → same `skeleton.hkx` → import your exported HKX. It must still match.

### Gate 5 — Runtime
Only now test OAR, behaviors, annotations, paired logic, root motion, combat or other runtime systems.

---

## 5. Common wrong turns to avoid

- Mapping MMD hip directly to Skyrim pelvis and ignoring Center/Groove/Mother.
- Using `skeleton.nif` as the only animation skeleton reference.
- Debugging Pandora/OAR while the HKX itself fails a clean re-import.
- Treating visible pelvis translation as true Skyrim actor displacement.
- Adding Pandora to a simple replacement that OAR can handle alone.
- Converting through KF just because a 2012 tutorial did.
- Using the wrong Havok generation/platform format.
- Flattening every VMD before proving that flattening is necessary.

Next: **[Installation & Setup](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Installation-and-Setup)**.
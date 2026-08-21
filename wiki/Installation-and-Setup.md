# Installation & Setup

Build the smallest clean toolchain that supports your workflow. Do **not** install every tool in the catalog.

## Recommended Blender strategy

### Conservative one-version setup
Use **Blender 5.1** for the MMD stage because MMD Tools 4.5.13 currently documents Blender **4.2–5.1** for the current v4.x line.

- Blender releases: https://www.blender.org/download/releases/
- MMD Tools extension: https://extensions.blender.org/add-ons/mmd-tools/
- MMD Tools source: https://github.com/MMD-Blender/blender_mmd_tools

### Advanced dual-version setup
If you want the newest PyNifly/Blender features while keeping conservative MMD compatibility:

1. Use Blender **5.1** for MMD import/evaluation/cleanup.
2. Save the proven/baked target scene.
3. Open that scene in **Blender 5.2 LTS** for PyNifly/HKX work if needed.

Blender 5.2 LTS: https://www.blender.org/download/releases/5-2/

PyNifly 28.x supports Blender 5.2: https://github.com/BadDogSkyrim/PyNifly

> Do not claim MMD Tools 5.2 compatibility as officially documented until its compatibility table explicitly lists it.

---

## Core Blender add-ons

### MMD Tools
**Required when your source is PMX/PMD/VMD/VPD.**

Install: https://extensions.blender.org/add-ons/mmd-tools/

Use it to import MMD models/motions and inspect the real MMD control hierarchy before retargeting.

### PyNifly
**Recommended core Skyrim importer/exporter.**

Repository: https://github.com/BadDogSkyrim/PyNifly

Animation guide: https://github.com/BadDogSkyrim/PyNifly/blob/main/ANIMATIONS.md

Use it to import the actual Skyrim `skeleton.hkx`, optional NIF reference meshes, and export Skyrim HKX directly.

### Optional MMD helpers
- MMD Tools Append: https://github.com/MMD-Blender/blender_mmd_tools_append
- MikuMikuRig rewrite: https://github.com/XiaoFFGe/MikuMikuRig
- Blender VMD Retargeting reference/add-on: https://github.com/butaixianran/Blender-Vmd-Retargeting
- Retarget for Blender 5+: https://github.com/KBSBAUDRICE/Retarget

---

## Source-side utilities

### Finekit suite
https://www.finekit.co.jp/base/index2e.html

Recommended utilities include:
- **VMD Checker** — inspect used bones/morphs before conversion.
- **VMDTMS** — Mother/Center mixing, twist separation, motion cleanup.
- **VMD Retarget** — proportion, bone-angle and IK compensation.
- **VMD Bake** — bake leg IK when solver behavior is unstable.
- PMX helper utilities — English bone naming / relationship repair when needed.

### MMDBridge
Maintained fork: https://github.com/rintrint/mmdbridge

Use when Blender/MMD Tools evaluation differs from actual MMD IK/physics behavior.

### MMD MotionSupporter
https://bowlroll.net/file/233713

Use only when diagnosis shows Mother/All-Parent misuse or FK→IK repair is needed.

---

## Skyrim control rigs — choose one family

### Coach's Enhanced Blender Animation Rigs
https://www.nexusmods.com/skyrimspecialedition/mods/148736

Best for modern Skyrim 1P/3P control rigs, IK/FK, bulk animation work and annotation-oriented workflows.

### NickNak Blender Animation Rigs
https://www.nexusmods.com/skyrimspecialedition/mods/118525

Strong current Blender 5 XP32/paired workflow.

### RigifyRig by Bogdan
https://www.nexusmods.com/skyrimspecialedition/mods/180970

Current Rigify-oriented Skyrim animation authoring option.

### Cascadeur option
Cascadeur: https://cascadeur.com/download

Skyrim rigs: https://www.nexusmods.com/skyrimspecialedition/mods/121536

Useful when physics-based cleanup, AutoPosing or motion polish adds value. Treat it as an intentional extra DCC boundary, not a mandatory stage.

---

## HKX inspection / annotations

- HKX_View / HKX_Edit: https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184
- serde-hkx / hkxc: https://github.com/SARDONYX-sard/serde-hkx
- HKXC Anno GUI: https://www.nexusmods.com/skyrimspecialedition/mods/166435
- Skyrim Annotation Blender Add-on: https://github.com/skypia0147-dev/blender-skyrim-annotation
- Composite HKX Conversion GUI: https://www.nexusmods.com/skyrimspecialedition/mods/154237

---

## Runtime essentials

### OAR
https://www.nexusmods.com/skyrimspecialedition/mods/92109

Use for simple/conditional replacements and testing.

Offline config editor: https://github.com/skypia0147-dev/OAR-External-Tool

### Pandora
https://www.nexusmods.com/skyrimspecialedition/mods/133232

Install only when your animation actually needs behavior generation or a dependent framework requires it.

### AMR
https://www.nexusmods.com/skyrimspecialedition/mods/50258

Use when the actor must physically translate/rotate through Skyrim's world in sync with the animation.

---

## Reference skeleton / extraction tools

- XPMSSE: https://www.nexusmods.com/skyrimspecialedition/mods/1988
- BSA Browser: https://www.nexusmods.com/skyrimspecialedition/mods/1756
- NifSkope: https://github.com/niftools/nifskope
- ck-cmd: https://github.com/aerisarn/ck-cmd
- Reskeletor: https://www.nexusmods.com/skyrimspecialedition/mods/182890

Always work against the skeleton that matches your real target environment.

---

## Setup acceptance checklist

- [ ] I know my Skyrim edition/runtime.
- [ ] I know which skeleton the animation will target.
- [ ] My MMD Tools + Blender pairing is documented/known-good.
- [ ] I installed one Skyrim control-rig family, not several competing ones.
- [ ] I can import the actual target `skeleton.hkx`.
- [ ] I have an HKX round-trip/inspection method.
- [ ] I installed OAR for the simplest runtime test.
- [ ] I did **not** add Pandora/root-motion/combat frameworks until the project actually requires them.

Next: **[Recommended Stacks](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Recommended-Stacks)**.
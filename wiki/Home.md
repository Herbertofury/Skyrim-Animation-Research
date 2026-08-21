# Skyrim Animation Research Wiki

> **2026 modern workflow hub for Skyrim animation authoring, VMD/MMD conversion, HKX, Blender rigs, annotations, root motion, OAR, Pandora, paired animations, combat, creatures, cinematics, and legacy rescue.**

**Research snapshot:** August 21, 2026 · **75 tools/resources** · **69 verified source-ledger entries** · **20 troubleshooting cases**  
**Canonical sortable database:** [Open the Google Sheet](https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit)

---

## 🚀 Start here

If you are new to Skyrim animation modding, do these in order:

1. **[Start Here](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Start-Here)** — choose the right workflow for what you are making.
2. **[Installation & Setup](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Installation-and-Setup)** — build a clean 2026 toolchain.
3. **[Recommended Stacks](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Recommended-Stacks)** — install only what your project actually needs.
4. **[Modern VMD → Skyrim Workflow](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Modern-Workflow)** — the full source-to-game pipeline.
5. **[Troubleshooting](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Troubleshooting)** — isolate source, retarget, HKX, and runtime problems without guessing.

### The golden rule

**Never debug Skyrim runtime until the animation already survives a clean HKX round-trip.**

The safe order is:

`original source → MMD/Blender evaluation → baked Skyrim target → exported HKX → fresh HKX re-import → annotations → OAR/behavior/runtime`

---

## 🧭 Choose your path

| I want to… | Best starting page | Default stack |
|---|---|---|
| Convert a VMD/MMD dance or motion to Skyrim | [VMD/MMD Source Preparation](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/VMD-MMD-Source-Preparation) | MMD Tools → evaluated retarget → PyNifly → OAR |
| Preserve missing bounce / Center / Groove motion | [MMD Motion Fidelity](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/MMD-Motion-Fidelity) | Finekit diagnostics + MMD Tools + MMDBridge when needed |
| Author a Skyrim animation directly in Blender | [Retargeting & Baking](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Retargeting-and-Baking) | Coach / NickNak / RigifyRig + PyNifly or blender-hkx |
| Export or repair HKX | [HKX Export & Validation](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/HKX-Export-and-Validation) | PyNifly + HKX_View/Edit + serde-hkx |
| Add footsteps, events, AMR, payloads | [Annotations, Events & Root Motion](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Annotations-Events-and-Root-Motion) | Annotation add-on / HKXC Anno GUI + AMR |
| Make a simple replacer | [OAR & Runtime Deployment](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/OAR-and-Runtime-Deployment) | OAR; no behavior engine unless required |
| Add new behavior logic | [Behaviors with Pandora](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Behaviors-with-Pandora) | Pandora |
| Make paired / interaction / combat animations | [Paired Animations & Combat](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Paired-Animations-and-Combat) | OAR + Paired Animation Improvements + project-specific runtime tools |
| Work with creatures, facial mocap, or cameras | [Creatures, Facial & Cinematics](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Creatures-Facial-and-Cinematics) | Creature rig / Performance Capture / FreeCamera Framework |
| Rescue an old ConvertUI / KF / HCT tutorial | [Legacy Migration](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Legacy-Migration) | PyNifly / serde-hkx / Composite GUI |
| Find the best tool for a specific job | [Tool Catalog](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Tool-Catalog) | Ranked 2026 catalog |

---

## ⭐ Recommended 2026 core

### Authoring / source
- **[Blender 5.2 LTS](https://www.blender.org/download/releases/5-2/)** — current LTS DCC.
- **[MMD Tools 4.5.13](https://extensions.blender.org/add-ons/mmd-tools/)** — core PMX/PMD/VMD/VPD importer. Current README explicitly documents Blender **4.2–5.1**, so use 5.1 for the conservative MMD stage.
- **[Finekit tools](https://www.finekit.co.jp/base/index2e.html)** — excellent VMD preflight, cleanup, bake, retarget, and Center/Mother diagnostics.

### Skyrim / HKX
- **[PyNifly 28.0.0](https://github.com/BadDogSkyrim/PyNifly)** — core native Skyrim HKX/NIF Blender path; supports Blender 5.2.
- **[Coach's Enhanced Blender Animation Rigs](https://www.nexusmods.com/skyrimspecialedition/mods/148736)** / **[NickNak Rigs](https://www.nexusmods.com/skyrimspecialedition/mods/118525)** / **[RigifyRig](https://www.nexusmods.com/skyrimspecialedition/mods/180970)** — current control-rig options.
- **[HKX_View / HKX_Edit](https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184)** — modern final HKX inspection/editing.
- **[serde-hkx / hkxc](https://github.com/SARDONYX-sard/serde-hkx)** — modern low-level HKX conversion and structural debugging.

### Runtime
- **[Open Animation Replacer](https://www.nexusmods.com/skyrimspecialedition/mods/92109)** — default simple replacement/deployment layer.
- **[Pandora Behaviour Engine Plus](https://www.nexusmods.com/skyrimspecialedition/mods/133232)** — use when behavior generation is genuinely required.
- **[Animation Motion Revolution](https://www.nexusmods.com/skyrimspecialedition/mods/50258)** — intentional actor displacement/rotation from animation annotations.

---

## 🔥 Most important 2026 discoveries

- **Finekit VMD Checker / VMDTMS / VMD Retarget / VMD Bake** — source-side diagnosis before Blender/HKX work.
- **Smooth HKX_Edit / HKX_View** — modern direct HKX QA/editing and root-motion-oriented tooling.
- **serde-hkx 2.0.0 / hkxc** — modern 32/64-bit HKX conversion, XML, inspection and diffing.
- **Reskeletor** — recovery for custom-skeleton/XPMSE/3BA/SMP animation tracks.
- **Dynamic Animation Framework** — modern JSON-driven interaction animation chains.
- **Animation Motion Fix** — current root-motion runtime fix worth testing in motion-heavy setups.
- **Universal Behavior Runtime / A-Pose Fix** — runtime compatibility layer for behavior/animation issues.
- **convertSAM** — ScreenArcherMenu YAML → HKX static poses.
- **Apply Impulse** — exact-frame engine impulse/rotation from annotations.
- **Trigger Combat Behaviour** — paired/combat runtime actions from animation annotations.

See **[Latest Rescan — 2026-08-21](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Latest-Rescan-2026-08-21)**.

---

## 📚 Wiki map

### Learn the pipeline
- [Start Here](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Start-Here)
- [Installation & Setup](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Installation-and-Setup)
- [Recommended Stacks](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Recommended-Stacks)
- [Modern Workflow](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Modern-Workflow)
- [Recipes & Examples](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Recipes-and-Examples)

### Source / Blender
- [VMD/MMD Source Preparation](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/VMD-MMD-Source-Preparation)
- [MMD Motion Fidelity](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/MMD-Motion-Fidelity)
- [Retargeting & Baking](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Retargeting-and-Baking)

### Skyrim / HKX
- [Skeletons & HKX](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Skyrim-Skeletons-and-HKX)
- [HKX Export & Validation](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/HKX-Export-and-Validation)
- [Annotations, Events & Root Motion](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Annotations-Events-and-Root-Motion)

### Runtime / advanced
- [OAR & Runtime Deployment](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/OAR-and-Runtime-Deployment)
- [Behaviors with Pandora](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Behaviors-with-Pandora)
- [Paired Animations & Combat](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Paired-Animations-and-Combat)
- [Creatures, Facial & Cinematics](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Creatures-Facial-and-Cinematics)

### Reference
- [Quick Reference](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Quick-Reference)
- [Tool Catalog](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Tool-Catalog)
- [Troubleshooting](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Troubleshooting)
- [Legacy Migration](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Legacy-Migration)
- [Glossary](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Glossary)
- [Source Ledger](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Source-Ledger)

---

> **Research philosophy:** use current primary sources, prefer modern native workflows, keep legacy tools only when they solve a real compatibility problem, and verify every animation in isolation before adding runtime complexity.
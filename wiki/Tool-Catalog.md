# Tool Catalog — Ranked 2026 Skyrim Animation Ecosystem

**Canonical sortable capability matrix:** https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit

The research database contains **75 tools/resources**. This page is the guided human-readable catalog.

## Verdict legend

| Verdict | Meaning |
|---|---|
| **CORE** | Default building block for the matching workflow |
| **HIGHLY RECOMMENDED** | Strong current companion/tool with clear value |
| **SPECIALIST** | Excellent for a narrower problem; do not install blindly |
| **EXPERIMENTAL / WATCHLIST** | Promising, but not yet the default production path |
| **LEGACY / SUPERSEDED** | Retained for old assets/tutorials/compatibility only |

---

# MMD / VMD source preparation

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| Blender 5.2 LTS | CORE DCC | Main current authoring environment; PyNifly supports 5.2 | https://www.blender.org/download/releases/5-2/ |
| MMD Tools 4.5.13 | CORE | PMX/PMD/VMD/VPD import/evaluation; README currently documents Blender 4.2–5.1 | https://extensions.blender.org/add-ons/mmd-tools/ |
| MMD Tools source | CORE REFERENCE | Compatibility/docs/source | https://github.com/MMD-Blender/blender_mmd_tools |
| MMD Tools Append | HIGHLY RECOMMENDED | Rigify/MMD editing and improved humanoid/IK workflows | https://github.com/MMD-Blender/blender_mmd_tools_append |
| MikuMikuRig rewrite | HIGHLY RECOMMENDED | Modern MMD controller/physics/action workflow | https://github.com/XiaoFFGe/MikuMikuRig |
| MMDBridge maintained fork | HIGHLY RECOMMENDED | MMD-native IK/physics fidelity fallback | https://github.com/rintrint/mmdbridge |
| Blender VMD Retargeting | HIGHLY RECOMMENDED REFERENCE | Evaluated-frame retargeting and Center/Groove/Waist methodology | https://github.com/butaixianran/Blender-Vmd-Retargeting |
| Finekit VMD Checker | HIGHLY RECOMMENDED | See which bones/morphs actually carry motion | https://www.finekit.co.jp/base/index2e.html |
| Finekit VMD Retarget | HIGHLY RECOMMENDED | Bone-angle/proportion/leg-IK compensation | https://www.finekit.co.jp/base/index2e.html |
| Finekit VMDTMS | HIGHLY RECOMMENDED | Mother/Center correction, twist separation, motion cleanup | https://www.finekit.co.jp/base/index2e.html |
| Finekit VMD Bake | HIGHLY RECOMMENDED | Bake unstable leg IK before downstream retargeting | https://www.finekit.co.jp/base/index2e.html |
| Finekit PMX English Bone-name Adder | SPECIALIST | Easier multilingual retarget mapping | https://www.finekit.co.jp/base/index2e.html |
| Finekit PMX Link Corrector | SPECIALIST | Repair malformed PMX relationships | https://www.finekit.co.jp/base/index2e.html |
| VMD Sizing | SPECIALIST | Adapt VMD motion to different model proportions | https://github.com/miu200521358/vmd_sizing |
| MMD MotionSupporter | SPECIALIST | Mother/All-Parent transfer and leg FK→IK repair | https://bowlroll.net/file/233713 |
| MikuMikuMoving | SPECIALIST LEGACY | Dense `Integrate Layer` fallback | https://sites.google.com/site/mikumikumovingeng/ |
| NexGiMa | OPTIONAL | Alternate MMD-compatible evaluator | https://sites.google.com/view/nexgima/Home |
| MikuMikuDayo | EXPERIMENTAL | Modern MMD-compatible renderer/tool experiment | https://github.com/pennennennennennenem/MikuMikuDayo |
| PV2FC 1.2 | SPECIALIST INTERCHANGE | PMX/VMD→FBX automation when an external-DCC bridge is intentional | https://github.com/hatoghx/PV2FC |

---

# Retargeting / Blender authoring

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| Retarget (KBSBAUDRICE) 5.1.5 | HIGHLY RECOMMENDED | Blender 5 constraint retarget/bake with MMD preset/root tools | https://github.com/KBSBAUDRICE/Retarget |
| Coach's Enhanced Blender Animation Rigs 4.1 | HIGHLY RECOMMENDED | Skyrim 1P/3P controls, IK/FK, annotations, AMR helpers | https://www.nexusmods.com/skyrimspecialedition/mods/148736 |
| NickNak Blender Animation Rigs v5 | HIGHLY RECOMMENDED | Current Blender 5 XP32 1P/3P/paired workflow | https://www.nexusmods.com/skyrimspecialedition/mods/118525 |
| RigifyRig by Bogdan 5.1 | HIGHLY RECOMMENDED | Rigify-based Skyrim animation authoring | https://www.nexusmods.com/skyrimspecialedition/mods/180970 |
| Cascadeur | HIGHLY RECOMMENDED OPTIONAL | Physics/AI-assisted animation polish and root-motion work | https://cascadeur.com/download |
| Cascadeur Animation Rigs for Skyrim | HIGHLY RECOMMENDED | Ready Skyrim rigs for Cascadeur | https://www.nexusmods.com/skyrimspecialedition/mods/121536 |
| Blender Dragon Rig | SPECIALIST CREATURE | Current Rigify workflow for Skyrim dragons | https://www.nexusmods.com/skyrimspecialedition/mods/175903 |
| Performance Capture | SPECIALIST CINEMATIC | Webcam/MediaPipe facial mocap for Skyrim | https://www.nexusmods.com/skyrimspecialedition/mods/174030 |

---

# HKX / skeleton / conversion / validation

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| PyNifly 28.0.0 | CORE | Native Skyrim LE/SE HKX skeleton + animation workflow in Blender | https://github.com/BadDogSkyrim/PyNifly |
| PyNifly Animation Guide | CORE REFERENCE | Correct `skeleton.hkx` workflow | https://github.com/BadDogSkyrim/PyNifly/blob/main/ANIMATIONS.md |
| blender-hkx (Beefclot/Coach fork) | HIGHLY RECOMMENDED | Current HKX plugin used by modern Skyrim rigs | https://github.com/beefclot/blender-hkx |
| blender-hkx (jgernandt upstream) | SPECIALIST | Upstream/reference HKX implementation | https://github.com/jgernandt/blender-hkx |
| Smooth HKX_Edit / HKX_View | HIGHLY RECOMMENDED | Standalone HKX inspection/editing/root-motion QA | https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184 |
| serde-hkx / hkxc 2.0.0 | HIGHLY RECOMMENDED | 32/64-bit HKX conversion, XML, inspect/diff | https://github.com/SARDONYX-sard/serde-hkx |
| Composite HKX Conversion GUI 3.0 | SPECIALIST | LE/SE/XML/KF compatibility conversion | https://www.nexusmods.com/skyrimspecialedition/mods/154237 |
| Reskeletor | SPECIALIST | Normalize custom-skeleton/XPMSE/3BA/SMP HKX track layouts | https://www.nexusmods.com/skyrimspecialedition/mods/182890 |
| ck-cmd | SPECIALIST | Bone-count and Bethesda asset inspection | https://github.com/aerisarn/ck-cmd |
| NifSkope | SPECIALIST SUPPORT | NIF skeleton/model inspection | https://github.com/niftools/nifskope |
| BSA Browser | SPECIALIST SUPPORT | Extract exact skeleton/animation assets | https://www.nexusmods.com/skyrimspecialedition/mods/1756 |
| Bethesda Archive Extractor | OPTIONAL LEGACY | Older BSA/BA2 extraction | https://www.nexusmods.com/skyrimspecialedition/mods/974 |
| NifBlend | EXPERIMENTAL WATCHLIST | Modern Blender 5 clean-room NIF/KF project; do not replace PyNifly yet | https://github.com/Tzeentchnet/NifBlend |
| armaToHKX | SPECIALIST LEGACY | Environmental/non-character Havok projects | https://github.com/TackYs/armaToHKX |
| convertSAM | SPECIALIST POSE | ScreenArcherMenu YAML → standard HKX static pose | https://www.nexusmods.com/skyrimspecialedition/mods/177216 |

---

# Annotations / events / root motion

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| Skyrim Annotation Blender Add-on | HIGHLY RECOMMENDED | Long Skyrim markers/events in Blender | https://github.com/skypia0147-dev/blender-skyrim-annotation |
| HKXC Anno GUI 2.0 | HIGHLY RECOMMENDED | Standalone HKX annotation dump/update with paired support | https://www.nexusmods.com/skyrimspecialedition/mods/166435 |
| Animation Motion Revolution | CORE FOR TRUE DISPLACEMENT | Annotation-driven actor translation/rotation | https://www.nexusmods.com/skyrimspecialedition/mods/50258 |
| Animation Motion Fix 1.1.9 | HIGHLY RECOMMENDED FOR ROOT MOTION | Runtime root-motion reduction/sticking fixes | https://www.nexusmods.com/skyrimspecialedition/mods/145100 |
| Apply Impulse 1.1.0 | SPECIALIST | Exact-frame engine impulse/rotation from annotations | https://www.nexusmods.com/skyrimspecialedition/mods/181584 |
| Payload Interpreter | SPECIALIST | PIE animation payload execution; exact-runtime validation required | https://www.nexusmods.com/skyrimspecialedition/mods/65089 |
| Payload Interpreter source | SPECIALIST REFERENCE | Source code | https://github.com/D7ry/PayloadInterpreter |

---

# Runtime / deployment / interaction

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| Open Animation Replacer 3.2.0 | CORE RUNTIME | Conditional replacement without behavior edits | https://www.nexusmods.com/skyrimspecialedition/mods/92109 |
| OAR source | CORE REFERENCE | Source/docs | https://github.com/ersh1/OpenAnimationReplacer |
| OAR External Tool | HIGHLY RECOMMENDED | Offline OAR config/user.json editing | https://github.com/skypia0147-dev/OAR-External-Tool |
| OAR - IED Conditions | SPECIALIST | Equipment-placement driven OAR conditions | https://www.nexusmods.com/skyrimspecialedition/mods/98308 |
| Pandora Behaviour Engine Plus | CORE WHEN BEHAVIORS NEEDED | Modern behavior generation / creature support | https://www.nexusmods.com/skyrimspecialedition/mods/133232 |
| Dynamic Animation Framework 0.2.2 | HIGHLY RECOMMENDED FOR INTERACTIONS | JSON-driven animation chains from gameplay/UI events | https://www.nexusmods.com/skyrimspecialedition/mods/158262 |
| Effect Animation Framework 1.0.2 | SPECIALIST | Effect-driven animation triggers | https://www.nexusmods.com/skyrimspecialedition/mods/171917 |
| A-Pose Bug Fix / Universal Behavior Runtime | HIGHLY RECOMMENDED COMPATIBILITY | Runtime LE animation/behavior conversion and A-pose fixes | https://www.nexusmods.com/skyrimspecialedition/mods/168903 |
| Universal Kinematics | EXPERIMENTAL SPECIALIST | Procedural locomotion/kinematic corrections | https://www.nexusmods.com/skyrimspecialedition/mods/185777 |
| Paired Animation Improvements | HIGHLY RECOMMENDED FOR PAIRED | Make annotated events in paired animations work normally | https://www.nexusmods.com/skyrimspecialedition/mods/99621 |
| Animation Queue Fix | HIGHLY RECOMMENDED FOR LARGE OAR SETUPS | Prevent overloaded animation load queues | https://www.nexusmods.com/skyrimspecialedition/mods/82395 |
| Trigger Combat Behaviour 1.1.1a | SPECIALIST COMBAT | Paired, stagger, i-frame, snap-target, stop-time annotations | https://www.nexusmods.com/skyrimspecialedition/mods/167256 |
| Precision | SPECIALIST COMBAT | Animation-aligned melee collision | https://www.nexusmods.com/skyrimspecialedition/mods/72347 |
| BFCO 3.100.5 | SPECIALIST COMBAT | Combat animation behavior framework | https://www.nexusmods.com/skyrimspecialedition/mods/117052 |
| Offset Movement Animation resource | SPECIALIST | Movement-offset behavior for interactions | https://www.nexusmods.com/skyrimspecialedition/mods/110408 |
| FreeCamera Framework | SPECIALIST CINEMATIC | Recorded/programmatic camera timelines | https://www.nexusmods.com/skyrimspecialedition/mods/174046 |
| FreeCamera Framework source | SPECIALIST REFERENCE | Source | https://github.com/staalo18/FreeCameraFramework |

---

# Supporting resources

| Tool/resource | Verdict | Best use | Link |
|---|---|---|---|
| XP32 Maximum Skeleton Special Extended | HIGHLY RECOMMENDED RESOURCE | Common expanded Skyrim skeleton ecosystem | https://www.nexusmods.com/skyrimspecialedition/mods/1988 |
| Creation Kit | OPTIONAL SPECIALIST | Idles, records, quests/events and game-side integration | https://store.steampowered.com/app/1946180/Skyrim_Special_Edition_Creation_Kit/ |

---

# Legacy / superseded

These are documented so old tutorials/assets can be understood—not because they are recommended for new work.

| Tool/path | Status | Modern replacement / advice |
|---|---|---|
| Blender 2.49b | LEGACY | Current Blender + current MMD Tools |
| 3ds Max 2012/2014 + HCT chain | LEGACY | Blender + PyNifly/current blender-hkx |
| Havok Content Tools 2010.2 | SPECIALIST LEGACY DEPENDENCY | Use only when a specific workflow explicitly needs it |
| Havok Content Tools 2014.x for Skyrim characters | AVOID | Skyrim-targeted 2010.2-compatible/modern native workflow |
| ConvertUI | AVOID FOR NEW WORK | PyNifly / serde-hkx / Composite GUI |
| hkxcmd | LEGACY | serde-hkx / PyNifly |
| hkanno64 | SUPERSEDED | HKXC Anno GUI |
| HKANNO64 GUI | DEPRECATED | HKXC Anno GUI |
| hkxPoser | LEGACY | HKX_View/Edit |
| FNIS SE | LEGACY | Pandora for new behavior work |
| Nemesis | COMPATIBILITY ONLY | Pandora unless a project specifically requires Nemesis |
| Dynamic Animation Replacer | SUPERSEDED | OAR |
| KF intermediary by default | AVOID | Direct modern HKX path |
| `skeleton.nif`-only authoring | AVOID | use actual `skeleton.hkx` |
| blind hip→pelvis VMD mapping | AVOID | evaluated layered-motion transfer |

Full migration guidance: **[Legacy Migration](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Legacy-Migration)**.
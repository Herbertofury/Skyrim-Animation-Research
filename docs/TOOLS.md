# Skyrim Animation Tool Catalog — 2026

This page is the human-readable index. The canonical sortable capability matrix is the live Google Sheet:

https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit

The catalog currently contains **75 tools/resources**. Verdicts below are intentionally opinionated: **CORE**, **HIGHLY RECOMMENDED**, **SPECIALIST**, **EXPERIMENTAL/WATCHLIST**, or **LEGACY/SUPERSEDED**.

## MMD / VMD source preparation

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| Blender 5.2 LTS | CORE DCC | Main modern authoring environment | https://www.blender.org/download/releases/5-2/ |
| MMD Tools 4.5.13 | CORE | PMX/PMD/VMD/VPD import and MMD evaluation | https://extensions.blender.org/add-ons/mmd-tools/ |
| MMD Tools Append | HIGHLY RECOMMENDED | Rigify/MMD editing, improved humanoid/IK workflows | https://github.com/MMD-Blender/blender_mmd_tools_append |
| MikuMikuRig rewrite | HIGHLY RECOMMENDED | Modern MMD controller/physics/action workflow | https://github.com/XiaoFFGe/MikuMikuRig |
| MMDBridge maintained fork | HIGHLY RECOMMENDED | MMD-native IK/physics evaluation fallback | https://github.com/rintrint/mmdbridge |
| Blender VMD Retargeting | HIGHLY RECOMMENDED REFERENCE | Evaluated-frame retargeting; Center/Groove/Waist layers | https://github.com/butaixianran/Blender-Vmd-Retargeting |
| Finekit VMD Checker | HIGHLY RECOMMENDED | Diagnose exactly which bones/morphs carry motion | https://www.finekit.co.jp/base/index2e.html |
| Finekit VMD Retarget | HIGHLY RECOMMENDED | Bone-angle/proportion/IK compensation | https://www.finekit.co.jp/base/index2e.html |
| Finekit VMDTMS | HIGHLY RECOMMENDED | Mother/Center correction, twist separation, motion cleanup | https://www.finekit.co.jp/base/index2e.html |
| Finekit VMD Bake | HIGHLY RECOMMENDED | Bake unstable leg IK before downstream retargeting | https://www.finekit.co.jp/base/index2e.html |
| Finekit PMX English Bone-name Adder | SPECIALIST | Easier multilingual retarget mapping | https://www.finekit.co.jp/base/index2e.html |
| Finekit PMX Link Corrector | SPECIALIST | Repair malformed PMX relationships | https://www.finekit.co.jp/base/index2e.html |
| VMD Sizing | SPECIALIST | Adapt VMD to different model proportions | https://github.com/miu200521358/vmd_sizing |
| MMD MotionSupporter | SPECIALIST | Mother/All-Parent transfer and leg FK→IK repair | https://bowlroll.net/file/233713 |
| MikuMikuMoving | SPECIALIST LEGACY | Dense `Integrate Layer` fallback | https://sites.google.com/site/mikumikumovingeng/ |
| NexGiMa | OPTIONAL | Alternate MMD-compatible evaluator | https://sites.google.com/view/nexgima/Home |
| MikuMikuDayo | EXPERIMENTAL | Modern MMD-compatible renderer/tool experiment | https://github.com/pennennennennennenem/MikuMikuDayo |
| PV2FC 1.2 | SPECIALIST INTERCHANGE | PMX/VMD→FBX automation for Cascadeur/UE/external DCC | https://github.com/hatoghx/PV2FC |

## Blender retargeting / animation authoring

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| Retarget (KBSBAUDRICE) 5.1.5 | HIGHLY RECOMMENDED | Blender 5 constraint retarget/bake with MMD preset and root tools | https://github.com/KBSBAUDRICE/Retarget |
| Coach's Enhanced Blender Animation Rigs 4.1 | HIGHLY RECOMMENDED | Skyrim 1P/3P control rigs, IK/FK, annotations, AMR helpers | https://www.nexusmods.com/skyrimspecialedition/mods/148736 |
| NickNak Blender Animation Rigs v5 | HIGHLY RECOMMENDED | Current Blender 5 XP32 1P/3P/paired workflow | https://www.nexusmods.com/skyrimspecialedition/mods/118525 |
| RigifyRig by Bogdan 5.1 | HIGHLY RECOMMENDED | Rigify-based Skyrim animation authoring | https://www.nexusmods.com/skyrimspecialedition/mods/180970 |
| Cascadeur | HIGHLY RECOMMENDED OPTIONAL POLISH | Physics/AI-assisted motion cleanup and root-motion authoring | https://cascadeur.com/download |
| Cascadeur Animation Rigs for Skyrim | HIGHLY RECOMMENDED | Ready Skyrim rigs for Cascadeur | https://www.nexusmods.com/skyrimspecialedition/mods/121536 |
| Blender Dragon Rig | SPECIALIST CREATURE | Current Rigify workflow for Skyrim dragons | https://www.nexusmods.com/skyrimspecialedition/mods/175903 |
| Performance Capture | SPECIALIST CINEMATIC | Webcam/MediaPipe facial mocap for Skyrim | https://www.nexusmods.com/skyrimspecialedition/mods/174030 |

## HKX / skeleton / conversion / inspection

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| PyNifly 28.0.0 | CORE | Native Skyrim LE/SE HKX skeleton + animation import/export in Blender | https://github.com/BadDogSkyrim/PyNifly |
| blender-hkx (Beefclot/Coach fork) | HIGHLY RECOMMENDED | Current HKX plugin bundled with modern Skyrim rigs | https://github.com/beefclot/blender-hkx |
| blender-hkx (jgernandt upstream) | SPECIALIST | Upstream/reference HKX implementation | https://github.com/jgernandt/blender-hkx |
| Smooth HKX_Edit / HKX_View | HIGHLY RECOMMENDED | Standalone game-ready HKX inspection/editing/root-motion QA | https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184 |
| serde-hkx / hkxc 2.0.0 | HIGHLY RECOMMENDED | Modern 32/64-bit HKX conversion, XML, inspect/diff | https://github.com/SARDONYX-sard/serde-hkx |
| Composite HKX Conversion GUI 3.0 | SPECIALIST | LE/SE/XML/KF compatibility conversion | https://www.nexusmods.com/skyrimspecialedition/mods/154237 |
| Reskeletor | SPECIALIST | Normalize custom-skeleton HKX to vanilla track layouts | https://www.nexusmods.com/skyrimspecialedition/mods/182890 |
| ck-cmd | SPECIALIST | Bone-count/asset inspection and Bethesda CLI work | https://github.com/aerisarn/ck-cmd |
| NifSkope | SPECIALIST | Inspect NIF skeleton/model structure | https://github.com/niftools/nifskope |
| BSA Browser | SPECIALIST SUPPORT | Extract exact skeleton.hkx/NIF/animations from archives | https://www.nexusmods.com/skyrimspecialedition/mods/1756 |
| NifBlend | EXPERIMENTAL WATCHLIST | Modern Blender 5 clean-room NIF/KF project | https://github.com/Tzeentchnet/NifBlend |
| armaToHKX | SPECIALIST LEGACY | Environmental/non-character Havok projects | https://github.com/TackYs/armaToHKX |
| convertSAM | SPECIALIST POSE | ScreenArcherMenu YAML → standard HKX static pose | https://www.nexusmods.com/skyrimspecialedition/mods/177216 |

## Annotation / events / root motion

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| Skyrim Annotation Blender Add-on | HIGHLY RECOMMENDED | Long Skyrim markers/events in Blender | https://github.com/skypia0147-dev/blender-skyrim-annotation |
| HKXC Anno GUI 2.0 | HIGHLY RECOMMENDED | Standalone annotation dump/update; paired support | https://www.nexusmods.com/skyrimspecialedition/mods/166435 |
| Animation Motion Revolution (AMR) | CORE FOR TRUE DISPLACEMENT | Annotation-driven actor translation/rotation | https://www.nexusmods.com/skyrimspecialedition/mods/50258 |
| Animation Motion Fix 1.1.9 | HIGHLY RECOMMENDED FOR ROOT-MOTION SETUPS | Runtime root-motion reduction/sticking fixes | https://www.nexusmods.com/skyrimspecialedition/mods/145100 |
| Apply Impulse 1.1.0 | SPECIALIST ANNOTATION RUNTIME | Exact-frame engine impulse/actor rotation from HKX payloads | https://www.nexusmods.com/skyrimspecialedition/mods/181584 |
| Payload Interpreter | SPECIALIST | PIE animation payload execution | https://www.nexusmods.com/skyrimspecialedition/mods/65089 |

**Payload Interpreter warning:** current 2026 user reports for Skyrim 1.6.1170 are mixed. Verify the exact file/DLL/runtime combination before making it a hard dependency.

## Runtime deployment / behavior / interaction

| Tool | Verdict | Best use | Link |
|---|---|---|---|
| Open Animation Replacer 3.2.0 | CORE RUNTIME | Conditional replacement without behavior edits | https://www.nexusmods.com/skyrimspecialedition/mods/92109 |
| OAR External Tool | HIGHLY RECOMMENDED | Offline OAR config/user.json editor | https://github.com/skypia0147-dev/OAR-External-Tool |
| OAR - IED Conditions | SPECIALIST | IED/SDS weapon-placement driven OAR conditions | https://www.nexusmods.com/skyrimspecialedition/mods/98308 |
| Pandora Behaviour Engine Plus 4.4.0-beta | CORE WHEN BEHAVIORS NEEDED | Modern behavior generation / creature support | https://www.nexusmods.com/skyrimspecialedition/mods/133232 |
| Dynamic Animation Framework 0.2.2 | HIGHLY RECOMMENDED FOR INTERACTIONS | JSON-driven animation chains from gameplay/UI events | https://www.nexusmods.com/skyrimspecialedition/mods/158262 |
| Effect Animation Framework 1.0.2 | SPECIALIST | Effect-driven animation triggers | https://www.nexusmods.com/skyrimspecialedition/mods/171917 |
| A-Pose Bug Fix / Universal Behavior Runtime | HIGHLY RECOMMENDED COMPATIBILITY | Runtime LE animation/behavior conversion and A-pose fixes | https://www.nexusmods.com/skyrimspecialedition/mods/168903 |
| Universal Kinematics | EXPERIMENTAL SPECIALIST | Procedural locomotion/kinematic corrections | https://www.nexusmods.com/skyrimspecialedition/mods/185777 |
| Paired Animation Improvements | HIGHLY RECOMMENDED FOR PAIRED | Make annotated events in paired animations work normally | https://www.nexusmods.com/skyrimspecialedition/mods/99621 |
| Animation Queue Fix | HIGHLY RECOMMENDED FOR LARGE OAR SETUPS | Prevent overloaded animation loading queues | https://www.nexusmods.com/skyrimspecialedition/mods/82395 |
| Trigger Combat Behaviour 1.1.1a | SPECIALIST COMBAT | Paired animations, stagger, i-frames, snap-target, stop-time from annotations | https://www.nexusmods.com/skyrimspecialedition/mods/167256 |
| Precision | SPECIALIST COMBAT | Accurate melee collision synchronized to authored attacks | https://www.nexusmods.com/skyrimspecialedition/mods/72347 |
| BFCO - Attack Behavior Framework | SPECIALIST COMBAT | Current combat animation behavior framework | https://www.nexusmods.com/skyrimspecialedition/mods/117052 |
| Offset Movement Animation - Modders Resource | SPECIALIST | Movement-offset behavior for interactions | https://www.nexusmods.com/skyrimspecialedition/mods/110408 |
| FreeCamera Framework | SPECIALIST CINEMATIC | Record/program camera timelines around animation scenes | https://www.nexusmods.com/skyrimspecialedition/mods/174046 |

## Supporting resources

| Tool/resource | Verdict | Best use | Link |
|---|---|---|---|
| XP32 Maximum Skeleton Special Extended | HIGHLY RECOMMENDED RESOURCE | Common expanded runtime skeleton/track ecosystem | https://www.nexusmods.com/skyrimspecialedition/mods/1988 |
| Creation Kit | OPTIONAL SPECIALIST | New game records, idles, quests/events, integration | https://store.steampowered.com/app/1946180/Skyrim_Special_Edition_Creation_Kit/ |
| Bethesda Archive Extractor | OPTIONAL LEGACY | Older BSA/BA2 extraction | https://www.nexusmods.com/skyrimspecialedition/mods/974 |

## Legacy / superseded paths kept for compatibility

These remain in the database because old tutorials and assets still reference them, not because they are recommended for new work:

- Blender 2.49b
- 3ds Max 2012/2014 + Havok Content Tools export chain
- Havok Content Tools 2010.2 (specialist legacy dependency only)
- Havok Content Tools 2014.x for Skyrim character export — **avoid**
- ConvertUI
- hkxcmd
- hkanno64
- HKANNO64 GUI
- hkxPoser
- FNIS SE
- Nemesis Unlimited Behavior Engine (compatibility cases only)
- Dynamic Animation Replacer (superseded by OAR)
- blind hip→pelvis VMD mapping
- skeleton.nif-only animation authoring
- unnecessary KF intermediates
- unnecessary old Blender FBX round-trips

See [LEGACY.md](LEGACY.md) for the migration guidance.

# Source Ledger — Skyrim Animation Research

Verified research snapshot: **2026-08-21**  
Canonical exhaustive source ledger: **69 entries** in the live Google Sheet:  
https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit

This page lists the load-bearing primary sources used by the repository. The Sheet remains the exhaustive sortable ledger with version/date/status fields.

## Core authoring / MMD

| Project | Current observation | Primary source |
|---|---|---|
| Blender | 5.2 LTS, released 2026-07-14 | https://www.blender.org/download/releases/5-2/ |
| MMD Tools | 4.5.13, 2026-06-28; README documents Blender 4.2–5.1 for current v4.x line | https://github.com/MMD-Blender/blender_mmd_tools |
| MMD Tools Extension | Official Blender extension distribution | https://extensions.blender.org/add-ons/mmd-tools/ |
| MMD Tools Append | Active modern Rigify/MMD companion | https://github.com/MMD-Blender/blender_mmd_tools_append |
| MikuMikuRig rewrite | Active 2026 branches for modern Blender | https://github.com/XiaoFFGe/MikuMikuRig |
| MMDBridge maintained fork | MMD-native evaluation fallback | https://github.com/rintrint/mmdbridge |
| Blender VMD Retargeting | 1.25.1 research line; Center/Groove/Waist layered-motion methodology | https://github.com/butaixianran/Blender-Vmd-Retargeting |
| Finekit MMD/VMD tools | VMD Checker, Retarget, VMDTMS, VMD Bake and PMX utilities; several 2026 updates | https://www.finekit.co.jp/base/index2e.html |
| VMD Sizing | Proportion-aware VMD processing | https://github.com/miu200521358/vmd_sizing |
| MMD MotionSupporter | Specialist Mother/All-Parent and FK→IK repair utility | https://bowlroll.net/file/233713 |
| MikuMikuMoving | Legacy but uniquely useful Integrate Layer workflow | https://sites.google.com/site/mikumikumovingeng/ |
| PV2FC | 1.2 PMX/VMD→FBX automation bridge | https://github.com/hatoghx/PV2FC |

## Skyrim Blender / HKX authoring

| Project | Current observation | Primary source |
|---|---|---|
| PyNifly | 28.0.0, 2026-07-17; Blender 5.2 support and native Skyrim HKX workflow | https://github.com/BadDogSkyrim/PyNifly |
| PyNifly Animation Guide | `skeleton.hkx`-based animation workflow and annotation behavior | https://github.com/BadDogSkyrim/PyNifly/blob/main/ANIMATIONS.md |
| blender-hkx (Beefclot/Coach fork) | Current fork used by modern Skyrim Blender rigs | https://github.com/beefclot/blender-hkx |
| blender-hkx upstream | Upstream/reference implementation | https://github.com/jgernandt/blender-hkx |
| Coach's Enhanced Blender Animation Rigs | 4.1, 2026-01-19 | https://www.nexusmods.com/skyrimspecialedition/mods/148736 |
| NickNak Blender Animation Rigs | v5, 2026-06-05 current Blender 5 branch | https://www.nexusmods.com/skyrimspecialedition/mods/118525 |
| RigifyRig by Bogdan | 5.1, 2026-06-02 | https://www.nexusmods.com/skyrimspecialedition/mods/180970 |
| KBSBAUDRICE Retarget | 5.1.5, 2026-07-31; Blender 5 retargeter with MMD preset | https://github.com/KBSBAUDRICE/Retarget |
| Blender Dragon Rig | 2026 creature-specific Rigify authoring resource | https://www.nexusmods.com/skyrimspecialedition/mods/175903 |
| Cascadeur | 2026 physics/AI animation authoring/polish | https://cascadeur.com/download |
| Cascadeur Skyrim rigs | Skyrim authoring bridge | https://www.nexusmods.com/skyrimspecialedition/mods/121536 |

## HKX conversion / validation / annotations

| Project | Current observation | Primary source |
|---|---|---|
| Smooth HKX_Edit / HKX_View | July 2026 HKX viewer/editor and root-motion tooling | https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184 |
| serde-hkx / hkxc | 2.0.0, 2026-07-26; modern HKX serialization/conversion/inspection backend | https://github.com/SARDONYX-sard/serde-hkx |
| HKXC Anno GUI | 2.0 standalone annotation workflow with paired-animation support | https://www.nexusmods.com/skyrimspecialedition/mods/166435 |
| Skyrim Annotation Blender Add-on | Blender-side marker/annotation authoring | https://github.com/skypia0147-dev/blender-skyrim-annotation |
| Composite HKX Conversion GUI | 3.0 compatibility converter for LE/SE/XML/KF workflows | https://www.nexusmods.com/skyrimspecialedition/mods/154237 |
| Reskeletor | 2026 custom-skeleton HKX normalization/recovery utility | https://www.nexusmods.com/skyrimspecialedition/mods/182890 |
| ck-cmd | Bethesda asset/bone-count inspection backend | https://github.com/aerisarn/ck-cmd |
| NifSkope | NIF inspection | https://github.com/niftools/nifskope |
| NifBlend | Experimental modern Blender 5 NIF/KF watchlist project | https://github.com/Tzeentchnet/NifBlend |
| convertSAM | 1.0, 2026-04-12; ScreenArcherMenu YAML → HKX static pose | https://www.nexusmods.com/skyrimspecialedition/mods/177216 |

## Runtime replacement / behaviors / motion

| Project | Current observation | Primary source |
|---|---|---|
| Open Animation Replacer | 3.2.0, 2026-07-26 | https://www.nexusmods.com/skyrimspecialedition/mods/92109 |
| OAR source | Maintained source repository | https://github.com/ersh1/OpenAnimationReplacer |
| OAR External Tool | Current offline OAR config editor | https://github.com/skypia0147-dev/OAR-External-Tool |
| Pandora Behaviour Engine Plus | 4.4.0-beta current August 2026 stable-labelled build | https://www.nexusmods.com/skyrimspecialedition/mods/133232 |
| Animation Motion Revolution | Annotation-driven true actor displacement | https://www.nexusmods.com/skyrimspecialedition/mods/50258 |
| Animation Motion Fix | 1.1.9, 2026-08-01 | https://www.nexusmods.com/skyrimspecialedition/mods/145100 |
| Dynamic Animation Framework | 0.2.2, 2026-07-28 | https://www.nexusmods.com/skyrimspecialedition/mods/158262 |
| Effect Animation Framework | 1.0.2, 2026-02-07 | https://www.nexusmods.com/skyrimspecialedition/mods/171917 |
| Universal Behavior Runtime / A-Pose Fix | 1.1.0-a, 2026-03-17 | https://www.nexusmods.com/skyrimspecialedition/mods/168903 |
| Universal Kinematics | v2, 2026-07-23 | https://www.nexusmods.com/skyrimspecialedition/mods/185777 |
| Paired Animation Improvements | Paired annotation/event runtime support | https://www.nexusmods.com/skyrimspecialedition/mods/99621 |
| Animation Queue Fix | Large animation-library runtime queue fix | https://www.nexusmods.com/skyrimspecialedition/mods/82395 |
| Payload Interpreter | PIE animation payload execution | https://www.nexusmods.com/skyrimspecialedition/mods/65089 |
| Payload Interpreter source | Source repository | https://github.com/D7ry/PayloadInterpreter |
| Apply Impulse | 1.1.0, 2026-07-03; annotation-driven impulse/rotation | https://www.nexusmods.com/skyrimspecialedition/mods/181584 |
| Trigger Combat Behaviour | 1.1.1a, 2026-06-05; annotation-driven paired/combat actions | https://www.nexusmods.com/skyrimspecialedition/mods/167256 |
| Precision | Animation-driven melee collision | https://www.nexusmods.com/skyrimspecialedition/mods/72347 |
| BFCO | 3.100.5, 2026-07-19 combat animation behavior framework | https://www.nexusmods.com/skyrimspecialedition/mods/117052 |

## Cinematic / facial / camera

| Project | Current observation | Primary source |
|---|---|---|
| Performance Capture | 2026 webcam/MediaPipe facial capture for Skyrim | https://www.nexusmods.com/skyrimspecialedition/mods/174030 |
| FreeCamera Framework | 1.0.0, 2026-03-06; cinematic timeline/camera framework | https://www.nexusmods.com/skyrimspecialedition/mods/174046 |
| FreeCamera Framework source | Source repository | https://github.com/staalo18/FreeCameraFramework |

## Legacy references retained for diagnosis

| Project | Reason retained | Primary source |
|---|---|---|
| ConvertUI | Explains old HKX→KF workflows and empty-output failure reports | https://www.nexusmods.com/skyrim/mods/17109 |
| hkxcmd | Historic HKX/XML/KF tool | https://github.com/figment/hkxcmd |
| FNIS SE | Legacy behavior ecosystem | https://www.nexusmods.com/skyrimspecialedition/mods/3038 |
| Nemesis | Legacy/compatibility behavior ecosystem | https://www.nexusmods.com/skyrimspecialedition/mods/60033 |
| Dynamic Animation Replacer | Superseded conditional replacer | https://www.nexusmods.com/skyrimspecialedition/mods/33746 |
| Blender 2.49b | Historic VMD tutorial baseline | https://www.blender.org/download/releases/2-49/ |

## 2026-08-21 rescan note

The final pre-publication sweep found **convertSAM**, **Apply Impulse**, and **Trigger Combat Behaviour** as meaningful additions. It also found enough mixed current discussion around Payload Interpreter on Skyrim 1.6.1170 to make exact-runtime validation a documented requirement.

See [`2026-08-21-RESCAN.md`](2026-08-21-RESCAN.md) for the rescan details.

# Latest Ecosystem Rescan — 2026-08-21

A fresh web sweep was run immediately before publication. The goal was to find **materially useful current tooling** missing from the earlier research—not to inflate the catalog with generic animation packs or old forks.

## New qualified additions

### convertSAM — ScreenArcherMenu YAML to HKX Pose Converter

- Version: **1.0**
- Updated: **2026-04-12**
- Link: https://www.nexusmods.com/skyrimspecialedition/mods/177216
- Why it earned inclusion: converts ScreenArcherMenu `.yaml` static poses into standard Skyrim `.hkx`, enabling an in-game pose-authoring → normal HKX deployment workflow.
- Documented pipeline includes Python/PyYAML and existing pose/Havok utilities.
- Caveat: weapon-node rotations may need cleanup.
- Verdict: **SPECIALIST / POSE**

### Apply Impulse

- Version: **1.1.0**
- Updated: **2026-07-03**
- Link: https://www.nexusmods.com/skyrimspecialedition/mods/181584
- How-to: https://www.nexusmods.com/skyrimspecialedition/mods/181584?tab=articles
- Why it earned inclusion: physical impulse and timed actor rotation at exact animation timestamps through annotation payloads.
- Caveat: runtime impulse is not a substitute for correctly authored root/world motion.
- Verdict: **SPECIALIST / ANNOTATION RUNTIME**

### Trigger Combat Behaviour (TCB)

- Version: **1.1.1a**
- Updated: **2026-06-05**
- Link: https://www.nexusmods.com/skyrimspecialedition/mods/167256
- How-to: https://www.nexusmods.com/skyrimspecialedition/mods/167256?tab=articles
- Why it earned inclusion: annotation-driven paired animations, stagger, i-frames, snap-target, stop-time and other combat actions.
- Verdict: **SPECIALIST / COMBAT**

---

## Revalidated current leaders

- NickNak Blender Animation Rigs v5 — https://www.nexusmods.com/skyrimspecialedition/mods/118525
- Coach's Enhanced Blender Animation Rigs 4.1 — https://www.nexusmods.com/skyrimspecialedition/mods/148736
- MMD Tools 4.5.13 — https://github.com/MMD-Blender/blender_mmd_tools
- Blender VMD Retargeting 1.25.1 — https://github.com/butaixianran/Blender-Vmd-Retargeting
- OAR 3.2.0 — https://www.nexusmods.com/skyrimspecialedition/mods/92109
- Animation Motion Fix 1.1.9 — https://www.nexusmods.com/skyrimspecialedition/mods/145100
- HKXC Anno GUI 2.0 — https://www.nexusmods.com/skyrimspecialedition/mods/166435
- serde-hkx / hkxc 2.0.0 — https://github.com/SARDONYX-sard/serde-hkx
- PyNifly 28.0.0 — https://github.com/BadDogSkyrim/PyNifly

---

## Payload Interpreter compatibility warning

Payload Interpreter:
- Source: https://github.com/D7ry/PayloadInterpreter
- Nexus: https://www.nexusmods.com/skyrimspecialedition/mods/65089
- Discussion: https://www.nexusmods.com/skyrimspecialedition/mods/65089?tab=posts

2026 user discussion contains **mixed reports for Skyrim 1.6.1170**, including working configurations and DLL/version failures.

Therefore the wiki's recommendation is:

> **Validate the exact game runtime + SKSE + Payload Interpreter file/DLL + dependent framework combination before making it a hard dependency.**

---

## Search convergence

The final sweep covered current Skyrim animation/HKX/Blender/VMD/paired/root-motion/pose/cinematic/modder-resource searches across GitHub and Nexus.

After the additions above, remaining results were predominantly:
- tools already cataloged
- old forks of historic `io_anim_hkx`
- generic animation replacement packs rather than authoring/conversion tools
- legacy tutorials already represented in the migration matrix
- teased/unreleased systems without enough current public material to recommend as usable tooling

The curated database therefore stops at **75 tools/resources** rather than padding the list with weaker duplicates.

Canonical database: https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit
# Skyrim Animation Research — 2026

A current research hub for **MMD/VMD → Blender → Skyrim HKX** animation workflows, plus modern Skyrim animation authoring, annotations, root motion, paired animations, behaviors, runtime deployment, creature/cinematic tooling, troubleshooting, and legacy migration.

**Research snapshot:** 2026-08-21  
**Catalog:** 75 tools/resources • 69 source-ledger entries • 20 troubleshooting cases  
**Live sortable Google Sheet:** https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit

> This repository is documentation/research, not a claim that every tool should be installed. The tables distinguish core, highly recommended, specialist, experimental/watchlist, and legacy/superseded paths.

## Best current VMD → Skyrim workflow

1. **Preflight the VMD** — inspect which MMD bones/morphs actually carry motion, especially Center, Groove, Waist and Mother/All Parent.
2. **Use a documented MMD-compatible Blender stack** — MMD Tools 4.5.13 currently documents Blender **4.2–5.1**. Blender 5.2 LTS is current and PyNifly supports it, but MMD Tools' README does not yet explicitly list 5.2.
3. **Preserve MMD evaluation fidelity** — if Blender's IK/physics differs, use MMDBridge or a dense/evaluated bake rather than manually guessing corrections.
4. **Retarget the evaluated motion** to the Skyrim target/control rig. Do not map raw VMD curves blindly when Center/Groove/waist layering is involved.
5. **Import the actual Skyrim `skeleton.hkx`** for correct Havok bone ordering/binding.
6. **Bake the final visual transforms every frame** on the Skyrim deform/export skeleton.
7. **Export HKX directly** with PyNifly or a modern Blender-HKX workflow; avoid the old ConvertUI/KF round-trip unless reproducing a legacy pipeline.
8. **Inspect/annotate the HKX** with current tools such as HKX_View/Edit or HKXC Anno GUI.
9. **Handle real world displacement explicitly** with the appropriate root-motion/runtime system; pelvis movement is not automatically actor displacement.
10. **Round-trip verify** by importing the finished HKX back onto the same skeleton in a fresh scene before blaming Skyrim runtime/behavior files.

See **[docs/WORKFLOW.md](docs/WORKFLOW.md)** for the full 20-step research workflow.

## Core stack

- [Blender 5.2 LTS](https://www.blender.org/download/releases/5-2/) — **CORE**
- [MMD Tools](https://extensions.blender.org/add-ons/mmd-tools/) — **CORE**
- [PyNifly](https://github.com/BadDogSkyrim/PyNifly) — **CORE**
- [Open Animation Replacer (OAR)](https://www.nexusmods.com/skyrimspecialedition/mods/92109) — **CORE RUNTIME**
- [Pandora Behaviour Engine Plus](https://www.nexusmods.com/skyrimspecialedition/mods/133232) — **CORE WHEN BEHAVIORS NEEDED**
- [Animation Motion Revolution (AMR)](https://www.nexusmods.com/skyrimspecialedition/mods/50258) — **CORE FOR TRUE DISPLACEMENT**

## What changed in the final 2026-08-21 rescan

The last sweep found three additional tools worth adding to the database:

- **[convertSAM](https://www.nexusmods.com/skyrimspecialedition/mods/177216)** — April 2026 ScreenArcherMenu YAML → standard Skyrim HKX pose conversion. Useful for in-game pose authoring/export without Blender.
- **[Apply Impulse](https://www.nexusmods.com/skyrimspecialedition/mods/181584)** — July 2026 exact-frame physical impulse and actor rotation driven from animation annotation payloads.
- **[Trigger Combat Behaviour (TCB)](https://www.nexusmods.com/skyrimspecialedition/mods/167256)** — June 2026 annotation-triggered paired animations, stagger, i-frames, snap-target and stop-time.

The rescan also reinforced a caution around **Payload Interpreter**: it remains widely used and valuable, but 2026 user reports on Skyrim **1.6.1170** are mixed across files/setups, so exact-runtime validation is mandatory rather than assuming universal compatibility.

See **[docs/2026-08-21-RESCAN.md](docs/2026-08-21-RESCAN.md)** for sources and details.

## Repository map

| Path | Purpose |
|---|---|
| `docs/WORKFLOW.md` | Full modern conversion/validation pipeline |
| `docs/TOOLS.md` | Human-readable catalog of all researched tools |
| `docs/TROUBLESHOOTING.md` | Symptom → cause → diagnostic → fix matrix |
| `docs/LEGACY.md` | Old workflows, why they fail, modern replacements |
| `docs/SOURCES.md` | Source ledger with direct links |
| `docs/2026-08-21-RESCAN.md` | Latest web rescan and newly added findings |
| `wiki/*.md` | Repository-backed wiki-ready mirrors of the key documentation |

## Important compatibility notes

- **MMD Tools 4.5.13:** official README currently documents **Blender 4.2–5.1** for v4.x.
- **Blender 5.2 LTS:** current Blender LTS and supported by PyNifly 28.0.0; treat MMD Tools 5.2 compatibility as not yet explicitly documented.
- **PyNifly:** use the real `skeleton.hkx` rather than only `skeleton.nif` when authoring/exporting animations.
- **MMD IK:** Blender's IK solver can differ from MMD; source evaluation fidelity must be solved before Skyrim retargeting.
- **ConvertUI/KF:** preserved only for legacy compatibility. A modern Blender/PyNifly path avoids this fragile conversion chain.
- **Root motion:** visual skeleton translation and physical actor/world displacement are separate concerns.

## Canonical live database

The Google Sheet remains the canonical sortable/filterable dataset and contains richer capability columns than Markdown can comfortably display:

https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit

The repository documentation is curated from that verified workbook so the research remains readable and version-controlled without duplicating a stale second spreadsheet dataset.

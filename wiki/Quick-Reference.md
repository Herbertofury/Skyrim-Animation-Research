# Quick Reference

## Golden pipeline

`source → verify → evaluate → retarget → bake → HKX export → fresh re-import → annotations → OAR/runtime`

## Default decisions

| Question | Default answer |
|---|---|
| Best VMD importer | MMD Tools |
| Blender version for conservative MMD Tools 4.5.13 use | 5.1 (README currently documents 4.2–5.1) |
| Current Blender LTS | 5.2 LTS |
| Best core Skyrim HKX Blender path | PyNifly 28.x |
| Use skeleton.nif or skeleton.hkx for animation binding? | `skeleton.hkx` |
| Default animation FPS | 30 FPS unless the source/workflow intentionally needs another rate |
| Default simple deployment | OAR |
| Behavior generator for new behavior logic | Pandora |
| True actor travel | AMR / intentional runtime displacement |
| Annotation editor | Skyrim Annotation Blender Add-on or HKXC Anno GUI |
| Modern HKX low-level converter/inspector | serde-hkx / hkxc |
| Legacy KF chain? | Avoid unless specifically required |

## Missing VMD bounce

Check in this order:

1. Center `センター`
2. Groove `グルーブ`
3. Waist / lower-body controls
4. Mother / All Parent `全ての親`
5. Leg-D / IK
6. Blender-vs-MMD IK/physics evaluation
7. Evaluated target bake

## HKX acceptance test

- Same target `skeleton.hkx`
- Fresh Blender scene
- Import exported HKX
- Compare timing
- Compare vertical extrema
- Compare feet/hands/hips
- Compare root/COM translation
- Compare annotation frames

If it fails here, **do not debug OAR/Pandora yet**.

## Simple replacer rule

**OAR first. Pandora only if behavior generation is genuinely required.**

## Root-motion rule

**Bone translation ≠ actor world displacement.**

## Direct links

- Blender: https://www.blender.org/download/releases/5-2/
- MMD Tools: https://extensions.blender.org/add-ons/mmd-tools/
- Finekit: https://www.finekit.co.jp/base/index2e.html
- PyNifly: https://github.com/BadDogSkyrim/PyNifly
- OAR: https://www.nexusmods.com/skyrimspecialedition/mods/92109
- Pandora: https://www.nexusmods.com/skyrimspecialedition/mods/133232
- AMR: https://www.nexusmods.com/skyrimspecialedition/mods/50258
- HKXC Anno GUI: https://www.nexusmods.com/skyrimspecialedition/mods/166435
- serde-hkx: https://github.com/SARDONYX-sard/serde-hkx
- Live research sheet: https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit
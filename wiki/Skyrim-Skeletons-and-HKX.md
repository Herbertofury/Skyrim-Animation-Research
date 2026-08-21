# Skyrim Skeletons & HKX

Correct animation data on the wrong skeleton is still a broken animation.

## `skeleton.hkx` is authoritative for animation binding

For Skyrim animation authoring, use the actual target **`skeleton.hkx`**.

[PyNifly animation guide](https://github.com/BadDogSkyrim/PyNifly/blob/main/ANIMATIONS.md)

The HKX skeleton contains animation-specific data such as bone ordering/binding information that you should not infer only from `skeleton.nif`.

### `skeleton.nif` is still useful
Use it for:
- visual reference
- node/model inspection
- geometry/skeleton context

But do not treat it as the complete animation binding source.

---

## Extract the exact target skeleton

Useful tools:

### BSA Browser
https://www.nexusmods.com/skyrimspecialedition/mods/1756

Extract the exact vanilla/reference skeleton and animation assets from game archives.

### NifSkope
https://github.com/niftools/nifskope

Inspect NIF skeleton/model structure and nodes.

### ck-cmd
https://github.com/aerisarn/ck-cmd

Useful for Bethesda asset inspection and bone-count diagnostics.

---

## Vanilla vs XPMSSE/custom skeletons

### XPMSSE
https://www.nexusmods.com/skyrimspecialedition/mods/1988

Modern animation rigs frequently target or assume XPMSSE-style expanded skeletons.

Always ask:
- Which skeleton was used when the animation was authored?
- Which skeleton is deployed in the game?
- Does the animation include extra tracks not present in the target?

### Reskeletor
https://www.nexusmods.com/skyrimspecialedition/mods/182890

A 2026 specialist recovery/normalization tool for animations authored against expanded custom skeletons that do not import cleanly into vanilla-style workflows.

Use it when bone-count/track-layout diagnosis proves the mismatch.

---

## LE vs SE/AE HKX

Skyrim's legacy and Special Edition animation ecosystems differ in platform/serialization expectations. Old converters often assume Oldrim/32-bit-era HKX.

Modern recommended tools:

- [PyNifly](https://github.com/BadDogSkyrim/PyNifly) — native Skyrim LE/SE workflow in Blender.
- [serde-hkx / hkxc](https://github.com/SARDONYX-sard/serde-hkx) — modern low-level 32/64-bit HKX conversion/inspection.
- [Composite HKX Conversion GUI](https://www.nexusmods.com/skyrimspecialedition/mods/154237) — compatibility GUI when deliberate LE/SE/XML/KF conversion is needed.

Do not run arbitrary HKX through a legacy converter and assume silent failure means the animation is bad.

---

## Havok generation matters

Skyrim animation tooling historically revolves around Havok 2010.2-era formats. A generic newer Havok export is not automatically Skyrim-compatible.

### Havok Content Tools 2010.2
Keep only as a **specialist legacy dependency** when a current workflow explicitly requires it.

### Havok Content Tools 2014.x
Do not treat it as a drop-in Skyrim character-animation export baseline.

Modern direct Blender/HKX tooling removes much of the need for manual HCT conversion.

---

## Skeleton mismatch symptoms

- generic/broken armature on import
- missing tracks
- animation mostly works but some bones explode
- A-pose despite a visually good source
- exporter rejects bone count
- fresh re-import does not match the baked scene
- custom skeleton animation cannot fit vanilla target

### Isolation order

1. confirm target game edition
2. confirm exact `skeleton.hkx`
3. confirm custom/XPMSSE status
4. inspect bone count/order
5. fresh-import the skeleton independently
6. only then import the animation

---

## Skeleton acceptance checklist

- [ ] exact target `skeleton.hkx` identified
- [ ] edition/platform known
- [ ] first/third-person/creature skeleton correct
- [ ] custom/XPMSSE extra tracks understood
- [ ] target control rig corresponds to deployed skeleton
- [ ] exported animation can be re-imported using the same skeleton

Next: **[HKX Export & Validation](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/HKX-Export-and-Validation)**.
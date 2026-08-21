# HKX Export & Validation

The export stage should be **boring**. If it becomes a chain of mysterious converters, simplify it.

## Preferred exporter — PyNifly

Repository:
https://github.com/BadDogSkyrim/PyNifly

Animation guide:
https://github.com/BadDogSkyrim/PyNifly/blob/main/ANIMATIONS.md

Research snapshot: **PyNifly 28.0.0**, July 17 2026, with Blender 5.2 support.

Recommended use:
1. import the target `skeleton.hkx`
2. author/retarget/bake on the matching target
3. export directly to intended Skyrim HKX
4. fresh re-import for verification

---

## Strong alternative — current blender-hkx fork

https://github.com/beefclot/blender-hkx

Used by current Skyrim Blender-rig ecosystems and a strong alternative when following Coach/NickNak-style workflows.

Upstream/reference:
https://github.com/jgernandt/blender-hkx

---

## Fresh-scene round-trip — mandatory

After export:

1. Save/close the working scene.
2. Open a new Blender scene.
3. Import the **same target `skeleton.hkx`**.
4. Import the exported animation HKX.
5. Compare with the baked target.

### Compare numerically/visually
- duration
- frame count
- highest/lowest vertical position
- root/COM path
- foot contact frames
- hand target frames
- large rotations
- event/annotation frames

If the re-import differs, debug **before** launching Skyrim.

---

## Standalone HKX inspection

### Smooth HKX_View / HKX_Edit
https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184

Major 2026 addition for direct HKX viewing/editing/QA. Useful for checking game-ready files independently of the Blender work scene.

### serde-hkx / hkxc
https://github.com/SARDONYX-sard/serde-hkx

Modern low-level backend for:
- 32/64-bit HKX conversion
- XML conversion
- structural inspection
- diff/debug workflows

Use it when you need to know whether two files differ structurally rather than visually guessing.

---

## Compatibility conversion — only when intentional

### Composite HKX Conversion GUI
https://www.nexusmods.com/skyrimspecialedition/mods/154237

Use for deliberate:
- LE ↔ SE compatibility
- HKX ↔ XML
- legacy KF workflows

This is a **fallback/compatibility tool**, not a mandatory stage in a new 2026 pipeline.

---

## Custom skeleton recovery

### Reskeletor
https://www.nexusmods.com/skyrimspecialedition/mods/182890

Use when animation tracks were authored against XPMSE/3BA/SMP/expanded skeletons and vanilla-style import/export cannot handle the bone count/layout.

Pair with:
https://github.com/aerisarn/ck-cmd

---

## Why ConvertUI can create an empty output folder

ConvertUI is an old Oldrim-era path. Silent/empty output often means the file does not match the platform/skeleton/serialization assumptions of the converter.

A powerful diagnostic clue is:

- known-good downgraded vanilla animation converts
- custom HKX does not

That suggests the custom HKX format/binding is the problem for the legacy converter, not necessarily the source animation.

### Modern response
Prefer:
- PyNifly direct export
- serde-hkx inspection/conversion
- Composite GUI for deliberate compatibility

Do not add `HKX → KF → HKX` just to mimic an old tutorial.

---

## HKX validation checklist

- [ ] correct target skeleton and edition
- [ ] baked target independent of constraints
- [ ] direct modern exporter used where possible
- [ ] fresh-scene re-import matches
- [ ] standalone viewer/inspection passes
- [ ] annotations preserved/verified
- [ ] no unnecessary KF intermediate
- [ ] runtime testing begins only after these pass

Next: **[Annotations, Events & Root Motion](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Annotations-Events-and-Root-Motion)**.
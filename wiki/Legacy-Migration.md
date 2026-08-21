# Legacy Migration

Canonical migration guide: [`docs/LEGACY.md`](../docs/LEGACY.md)

For new work, avoid making the historic `Blender 2.49 → FBX → 3ds Max → Havok Content Tools → ConvertUI → KF → HKX` chain your default. Modern Blender/HKX tooling can remove most of those fragile boundaries.

Key replacements:

- Blender 2.49 → current Blender + MMD Tools
- ConvertUI / mandatory KF → PyNifly or modern HKX conversion tooling
- hkanno64 / HKANNO64 GUI → HKXC Anno GUI / Blender annotation add-on
- DAR → OAR
- FNIS/Nemesis for new generic behavior work → Pandora, unless a specific mod requires the legacy engine
- `skeleton.nif`-only authoring → actual `skeleton.hkx`
- blind hip→pelvis VMD mapping → evaluated Center/Groove/Mother-aware retargeting

Full guide: https://github.com/Herbertofury/Skyrim-Animation-Research/blob/main/docs/LEGACY.md

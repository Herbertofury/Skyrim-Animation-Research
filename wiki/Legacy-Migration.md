# Legacy Migration — Replace Old Skyrim Animation Pipelines Safely

Old tutorials are valuable historical references, but many assume tools and file formats from 2011–2015. This page maps them to a modern workflow.

---

# Old chain vs modern chain

### Historic chain
`VMD → Blender 2.49 → FBX → 3ds Max → Havok Content Tools → HKX → ConvertUI → KF → HKX`

### Modern default
`VMD → current MMD Tools → evaluated retarget → actual Skyrim skeleton.hkx → visual bake → PyNifly/current HKX export → fresh re-import → OAR`

Fewer conversion boundaries means fewer opportunities to lose transforms, bone ordering, annotations or platform compatibility.

---

# Replacement matrix

| Old tool/workflow | Why it is no longer preferred | Modern path |
|---|---|---|
| Blender 2.49b | obsolete DCC and old add-on ecosystem | current Blender + current MMD Tools |
| old FBX handoff | can introduce transform/resampling boundaries | stay in Blender where possible |
| 3ds Max 2012/2014 | unnecessary mandatory bridge for ordinary animations | Blender + PyNifly/current blender-hkx |
| HCT 2014.x | wrong generation is a serious Skyrim format risk | Skyrim-targeted modern HKX workflow |
| HCT 2010.2 everywhere | discontinued; only needed by some legacy-compatible workflows | direct PyNifly/serde path where possible |
| ConvertUI | Oldrim-era assumptions and silent empty-output failures | PyNifly / serde-hkx / Composite GUI |
| HKX→KF→HKX by default | unnecessary format hop | direct HKX export |
| hkxcmd | stale historic converter | serde-hkx / PyNifly |
| hkanno64 | superseded annotation CLI | HKXC Anno GUI |
| HKANNO64 GUI | deprecated | HKXC Anno GUI |
| hkxPoser | obsolete preview path | Smooth HKX_View/Edit |
| Dynamic Animation Replacer | superseded conditional replacer | OAR |
| FNIS | legacy behavior ecosystem | Pandora for new behavior work |
| Nemesis | legacy/compatibility behavior ecosystem | Pandora unless a specific mod requires Nemesis |
| `skeleton.nif` only | insufficient animation-binding reference | actual `skeleton.hkx` |
| hip→pelvis VMD mapping | drops layered MMD Center/Groove/Mother semantics | evaluated layered-motion retarget |

---

# ConvertUI empty output diagnosis

If ConvertUI creates an empty output folder:

1. Test a known-good Oldrim/LE-compatible HKX.
2. Compare the custom HKX platform/serialization/skeleton binding.
3. If known-good converts and custom does not, do not keep randomizing VMD/FBX settings.
4. Move the custom animation into a modern direct HKX path.

Modern diagnostics:
- serde-hkx: https://github.com/SARDONYX-sard/serde-hkx
- Composite HKX Conversion GUI: https://www.nexusmods.com/skyrimspecialedition/mods/154237
- PyNifly: https://github.com/BadDogSkyrim/PyNifly

---

# When legacy tools still make sense

Keep a legacy tool only when:
- an old asset exists only in that format
- a specific modern rig/exporter explicitly requires the dependency
- you are reproducing a historic pipeline for diagnosis
- a mod/framework hard-depends on it

Do **not** keep a legacy step merely because “that is how the tutorial did it.”

---

# Safe migration strategy for an old project

1. Archive the complete old working project.
2. Preserve its final known-good HKX files.
3. Import/inspect those files with modern tools.
4. Reproduce one animation in the modern pipeline.
5. Compare old vs new in a fresh HKX round-trip.
6. Test in game through OAR.
7. Migrate remaining animations only after parity is proven.

This prevents an all-at-once toolchain rewrite from destroying your only known-good reference.

---

## Legacy references

- Blender 2.49: https://www.blender.org/download/releases/2-49/
- ConvertUI: https://www.nexusmods.com/skyrim/mods/17109
- hkxcmd: https://github.com/figment/hkxcmd
- FNIS SE: https://www.nexusmods.com/skyrimspecialedition/mods/3038
- Nemesis: https://www.nexusmods.com/skyrimspecialedition/mods/60033
- DAR: https://www.nexusmods.com/skyrimspecialedition/mods/33746

For current alternatives, return to **[Recommended Stacks](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Recommended-Stacks)**.
# Legacy / Superseded Skyrim Animation Workflows

Old tools remain documented because many Skyrim animation tutorials still depend on them. They are not automatically recommended for new work.

| Old tool/workflow | Old purpose | Current verdict | Prefer now | Why |
|---|---|---|---|---|
| Blender 2.49b | Old VMD import/editing tutorials | AVOID FOR NEW WORK | Current Blender + MMD Tools | Old plugins/FBX semantics add failure points and can lose modern MMD control-layer behavior |
| 3ds Max 2012/2014 + Havok Content Tools | Merge Skyrim skeleton + FBX and export HKX | AVOID FOR NEW CHARACTER WORK | PyNifly or current Blender-HKX rigs | Extra DCC hop, stale dependencies, fragile Havok platform assumptions |
| Havok Content Tools 2014.x | General Havok export | AVOID FOR SKYRIM CHARACTER EXPORT | PyNifly / serde-hkx; HCT 2010.2 only when a current workflow explicitly requires it | Skyrim's animation ecosystem is built around Havok 2010.2-era serialization; newer HCT is not automatically more compatible |
| Havok Content Tools 2010.2 | Platform writer | SPECIALIST LEGACY DEPENDENCY | Native modern HKX tools | Still appears in some modern rig instructions but is discontinued and unnecessary for many clean native workflows |
| ConvertUI | HKX→KF→HKX | AVOID FOR NEW WORK | PyNifly; Composite HKX Conversion GUI | 2012 Oldrim assumptions and silent empty-output failures; KF intermediate is unnecessary for normal modern authoring |
| hkxcmd | HKX/XML/KF CLI | LEGACY | serde-hkx/hkxc; PyNifly | Stale and its retarget path is not a strong modern baseline |
| hkanno64 | SE annotation CLI | SUPERSEDED | HKXC Anno GUI 2.0 / Blender annotation add-on | Old HCT-dependent annotation workflow |
| HKANNO64 GUI | GUI wrapper for hkanno64 | DEPRECATED | HKXC Anno GUI 2.0 | Replaced by the newer standalone tool |
| hkxPoser | Old HKX pose/animation preview | LEGACY | Smooth HKX_View/HKX_Edit | Much weaker modern format/event/root-motion support |
| FNIS SE | Behavior generation | LEGACY COMPATIBILITY | Pandora | Keep only for mods that genuinely require FNIS-specific behavior/data |
| Nemesis Unlimited Behavior Engine | Behavior generation | LEGACY/COMPATIBILITY | Pandora | New work should prefer the actively developed behavior engine unless a patch explicitly requires Nemesis |
| Dynamic Animation Replacer | Conditional replacement | SUPERSEDED | Open Animation Replacer | OAR is the maintained backwards-compatible successor |
| Bethesda Archive Extractor | BSA/BA2 extraction | OPTIONAL LEGACY | BSA Browser | BAE remains usable, but BSA Browser is generally the more convenient modern extraction utility |
| KF intermediate | Gamebryo animation interchange | AVOID FOR NORMAL SKYRIM HKX | Direct HKX authoring/export | Adds conversion stages without benefit in a modern native HKX workflow |
| `skeleton.nif`-only authoring | Target skeleton reference | AVOID AS SOLE ANIMATION SKELETON | Import actual `skeleton.hkx` | NIF alone does not give the full HKX animation skeleton/bone-order information used for binding |
| Blind hip→pelvis VMD mapping | Quick humanoid retarget | AVOID | Evaluated-frame retarget with Center/Groove/Mother handling | Drops layered MMD body translation and causes the classic missing bounce |
| Old Blender FBX round-trip | Transfer MMD motion into another DCC | AVOID WHEN UNNECESSARY | Stay in Blender and retarget evaluated motion directly | FBX can flatten/control-transform semantics and adds another axis/resampling boundary |

## When the legacy chain is still justified

Keep an old path only when one of these is true:

- You are reproducing an exact historic project that already depends on the old tool.
- A current rig/tool explicitly documents HCT 2010.2 as a required final platform-writing step.
- You have a KF-only asset/tool requirement that is not covered by the native HKX path.
- You are diagnosing an old asset and need to compare against the original authoring environment.

Even then, validate the output against a modern structural tool such as serde-hkx/hkxc or by importing the result back onto the exact target skeleton.

## ConvertUI empty-output interpretation

If a known-good downgraded Oldrim animation converts but a custom HKX produces an empty output folder, that is strong evidence that the custom HKX's serialization/platform/skeleton binding does not match what ConvertUI expects. It does **not** prove the original VMD is bad.

The modern answer is normally to bypass the KF round-trip, not to keep changing the VMD until ConvertUI happens to accept it.

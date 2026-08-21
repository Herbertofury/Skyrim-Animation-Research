# Troubleshooting — Skyrim Animation Research

Use this matrix after separating **source-motion**, **retarget/bake**, **HKX serialization**, and **runtime/behavior** problems. Do not change all four layers at once.

| Symptom | Most likely cause | Diagnostic | Modern fix |
|---|---|---|---|
| VMD looks right in MMD but loses vertical bounce in Blender/Skyrim | Center/Groove/Waist/Mother motion was dropped or flattened incorrectly | Inspect those MMD controls at known high/low frames | Retarget the evaluated MMD result; use Finekit/VMD tools only where diagnosis proves needed |
| Feet/legs differ immediately after MMD import | Blender IK differs from MMD | Compare original MMD playback against Blender before retargeting | Use MMDBridge / MMD-native evaluation and bake the trusted result |
| Pose is mostly correct but body translation is missing | Naive hip→pelvis mapping | Check whether Center/Groove/Mother carry translation | Route layered body controls explicitly; do not copy only hip curves |
| Animation changes after retarget constraints are removed | Target was not baked from evaluated transforms | Disable constraints and compare | Bake visual location + rotation every frame, then clear/disable constraints |
| HKX exports but fresh re-import differs | Wrong skeleton/bone order, bake error, or exporter issue | Fresh scene + exact same `skeleton.hkx` + exported HKX | Fix skeleton binding/bake/export before opening Skyrim |
| Generic armature / wrong tracks / broken binding | Used `skeleton.nif` alone or wrong HKX skeleton | Compare target skeleton source and edition | Import the actual target `skeleton.hkx` and match LE/SE intentionally |
| ConvertUI creates an empty output folder | Oldrim-era HKX/platform/skeleton mismatch | Try a known-good LE-compatible HKX and compare | Stop using ConvertUI for new work; use PyNifly/serde-hkx/Composite GUI |
| Custom HCT export fails but downgraded vanilla animation converts | Custom HKX serialization/binding differs from expected Skyrim format | Inspect HKX structure/platform and skeleton binding | Export natively with modern Skyrim HKX tooling or correct the exact Havok 2010.2 platform path |
| Animation looks correct in Blender but A-poses in game | Runtime behavior/format compatibility, not necessarily animation content | Confirm the same HKX round-trips outside Skyrim | Check OAR path, behavior requirements, Pandora/Universal Behavior Runtime and exact game runtime |
| Simple replacer does nothing | Wrong path/OAR condition/project rather than HKX authoring | Use OAR in-game editor/diagnostics | Simplify to unconditional replacement first, then rebuild conditions |
| Paired actors desync | Actor order, alignment, annotations or paired runtime rules | Test each clip separately and inspect event timing | Fix alignment/annotations; use Paired Animation Improvements where appropriate |
| Paired animation event never fires | Paired annotations/runtime support missing | Dump annotations and inspect exact marker text/timing | HKXC Anno GUI / annotation add-on + Paired Animation Improvements |
| Visible bounce works but actor does not move through world | Bone translation ≠ Skyrim actor displacement | Compare root/pelvis motion with actor world position | Author AMR `animmotion`/rotation or another intentional runtime displacement system |
| Actor slides/snaps during root-motion animation | Incomplete/incorrect motion annotations or runtime interference | Inspect root-motion annotation timing; test without combat/runtime modifiers | Correct AMR annotations; test Animation Motion Fix in affected setups |
| Root motion becomes reduced/stuck in combat | Runtime motion handling bug/conflict | Compare out-of-combat and combat playback | Test Animation Motion Fix and isolate combat frameworks |
| Animation queue stalls with huge OAR library | Runtime animation request queue overload | Reproduce with minimal vs full replacement set | Use Animation Queue Fix and reduce pathological replacement churn |
| Custom-skeleton HKX cannot import cleanly | Extra XPMSE/3BA/SMP tracks exceed vanilla target expectations | Inspect animation bone count | Use Reskeletor/ck-cmd workflow or author against the exact deployed skeleton |
| Long annotation text is truncated/awkward in Blender | Marker-name/editor limitation | Compare exported annotation text to intended marker | Use Skyrim Annotation Blender Add-on or post-export HKXC Anno GUI |
| Combat payload annotation does nothing | Payload/runtime dependency mismatch | Verify exact payload syntax, dependency DLL and game version | Validate Payload Interpreter or use current framework-specific event tooling |
| Payload Interpreter fails on Skyrim 1.6.1170 | File/DLL/runtime mismatch; 2026 reports are mixed | Test exact PI file against exact game/SKSE version | Do not assume universal compatibility; validate the exact dependency set before shipping |
| Weapon pose from ScreenArcherMenu converts imperfectly | convertSAM weapon-node rotation limitation | Compare weapon nodes after conversion | Clean weapon-related rotations manually; treat convertSAM as a static-pose specialist tool |

## Golden isolation order

1. Prove the original VMD/MMD motion.
2. Prove the Blender/MMD evaluated result.
3. Prove the baked Skyrim target with constraints disabled.
4. Prove the exported HKX by fresh round-trip.
5. Only then debug OAR, behaviors, paired logic, payloads, root-motion runtime, combat frameworks, or game-version compatibility.

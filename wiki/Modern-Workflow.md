# Modern Workflow

Canonical repository page: [`docs/WORKFLOW.md`](../docs/WORKFLOW.md)

## Short version

1. Preserve original VMD/PMX.
2. Inspect Center, Groove, Waist, Mother/All Parent and IK channels before retargeting.
3. Import/evaluate with current MMD Tools; if Blender differs from MMD, solve source fidelity first.
4. Import Skyrim's real `skeleton.hkx`.
5. Retarget the **evaluated** MMD result to one authoritative Skyrim target/control rig.
6. Bake visual location/rotation every frame.
7. Disable source constraints and verify the target is unchanged.
8. Export HKX through PyNifly or another current native HKX path.
9. Fresh-scene round-trip the exported HKX onto the same skeleton.
10. Add/verify annotations and intentional root-motion/runtime behavior.
11. Deploy simple replacements through OAR; use Pandora only for genuine behavior-generation needs.

Full workflow: https://github.com/Herbertofury/Skyrim-Animation-Research/blob/main/docs/WORKFLOW.md

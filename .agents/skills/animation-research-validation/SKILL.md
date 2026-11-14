---
name: animation-research-validation
description: Maintain source-led Skyrim animation research and diagnose VMD-to-HKX pipelines with stage-specific fidelity, skeleton, root-motion and runtime evidence.
---

# Animation research and validation

Use for tool-catalog updates, compatibility recommendations, troubleshooting and workflow comparisons. Read `README.md`, `docs/WORKFLOW.md`, `docs/SOURCES.md` and `docs/TROUBLESHOOTING.md`. The repository is research, not proof of an installed or working toolchain.

## Evidence updates

Record review date, exact upstream version/commit, license, documented Blender/game/runtime support and primary-source URL. Keep historical snapshots intact; add a dated correction when a newer source supersedes an older claim. A newer release, popularity or a successful import does not prove an improved complete workflow. Distinguish documented support, community report, hypothesis and direct tested result.

The README links the sortable Google Sheet; do not silently create a competing authoritative dataset. Repository edits do not authorize unrelated external sheet changes. Where authorized, reconcile identities and source links without replacing owner notes or historical compatibility caveats. Keep wiki source updates separate from verified live wiki publication.

## Stage-specific diagnosis

1. **Source motion:** inspect which VMD bones/morphs carry motion, including Center/Groove/Waist/Mother. Record source identity, frame range, frame rate and evaluated IK/physics behavior. Never fix offsets by guessing before inspecting layered motion.
2. **Evaluation and retargeting:** use an exactly documented Blender/add-on combination. Compare evaluated motion, not just raw curves. Retarget to the actual target/control rig; preserve axis conventions, scale and rest transforms.
3. **Binding/export:** use actual Skyrim `skeleton.hkx` for Havok bone ordering/binding, not merely an apparently matching NIF. Bake final visual transforms on the export skeleton every frame as required by the documented pipeline.
4. **Round trip:** import the exported HKX into a fresh scene on the same skeleton. Compare duration, frame timing, bone transforms, feet/contact, root/pelvis separation and annotations before investigating runtime behavior files.
5. **Runtime:** distinguish animation replacement from behavior generation and actual world displacement. Pelvis motion is not automatically actor displacement; optional root-motion systems apply only to workflows that need them. Preserve paired-actor alignment and annotation timing as separate gates.
6. **Deployment:** test the actual game runtime, skeleton, behavior engine and replacer versions in an isolated profile with original assets preserved. Record the selected animation and in-game observation; an HKX viewer preview is not game acceptance.

For a failure, retain original input, exact intermediate/output hashes, tool versions, settings and a smallest reproducible case. Change one stage at a time, compare against last-good output, and separate source evaluation, conversion, behavior and runtime failures. Do not redistribute proprietary rigs, paid animations or creator assets without permission.

## Completion report

Validate changed local links, catalog/source identities and dates. Report research reviewed, conversion tested, round-trip tested, game tested and live publication separately. If no executable/game environment is available, provide a reproducible test plan and explicitly leave those stages untested; do not label a proposed stack universally best.

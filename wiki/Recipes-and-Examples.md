# Recipes & Examples

Use these as **decision recipes**, not rigid tutorials. Exact UI labels can change with tool versions; the verification gates are more important than button names.

---

# Recipe 1 — Convert a VMD dance to a Skyrim OAR replacer

**Goal:** preserve the full dance—including Center/Groove bounce—and deploy it without unnecessary behavior work.

1. Preserve original VMD/PMX.
2. Run [Finekit VMD Checker](https://www.finekit.co.jp/base/index2e.html).
3. Import with [MMD Tools](https://extensions.blender.org/add-ons/mmd-tools/) on a documented-compatible Blender version.
4. Compare high/low bounce and foot-contact frames.
5. If Blender differs, use [MMDBridge](https://github.com/rintrint/mmdbridge) or targeted source repair.
6. Import Skyrim `skeleton.hkx` with [PyNifly](https://github.com/BadDogSkyrim/PyNifly).
7. Retarget evaluated motion; route Center/Groove/Mother intentionally.
8. Bake visual target every frame.
9. Disable constraints and compare.
10. Export HKX directly.
11. Fresh-scene re-import.
12. Inspect final HKX.
13. Deploy as a simple [OAR](https://www.nexusmods.com/skyrimspecialedition/mods/92109) replacement.
14. Add conditions only after unconditional playback works.

**Do not add:** Pandora, KF, HCT, AMR unless the animation actually needs them.

---

# Recipe 2 — Fix “dance works but vertical bounce disappeared”

1. Find a frame with obvious high bounce and a frame with obvious low bounce.
2. Inspect Center, Groove, Mother and Waist/lower-body transforms.
3. Confirm whether Blender reproduces those evaluated world positions.
4. If not, fix source evaluation first.
5. Retarget evaluated body translation instead of only hip curves.
6. Bake visual target.
7. Disable retarget constraints.
8. Export and fresh re-import.
9. Compare the same high/low frames.

Reference: [MMD Motion Fidelity](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/MMD-Motion-Fidelity).

---

# Recipe 3 — Author a Skyrim idle directly in Blender

1. Extract/import exact `skeleton.hkx`.
2. Choose Coach / NickNak / RigifyRig.
3. Animate with controls.
4. Bake to the export skeleton.
5. Add annotations if required.
6. Export HKX with PyNifly/current blender-hkx.
7. Fresh round-trip.
8. Deploy through OAR.

No MMD tooling is needed.

---

# Recipe 4 — Root-motion lunge / dodge / moving attack

1. Finish visual animation first.
2. Round-trip HKX.
3. Decide intended world-space translation/rotation.
4. Author AMR annotations.
5. Verify finished HKX annotation text/timing.
6. Test movement in minimal runtime.
7. Add combat framework.
8. If root motion reduces/sticks only in combat, test [Animation Motion Fix](https://www.nexusmods.com/skyrimspecialedition/mods/145100).
9. Add [Precision](https://www.nexusmods.com/skyrimspecialedition/mods/72347) collision timing if needed.

---

# Recipe 5 — Paired interaction

1. Author/test actor A alone.
2. Author/test actor B alone.
3. Lock shared start transforms and frame zero.
4. Validate contact frames.
5. Bake/export each clip.
6. Inspect annotations.
7. Add [Paired Animation Improvements](https://www.nexusmods.com/skyrimspecialedition/mods/99621).
8. Add OAR/interaction trigger layer.
9. Add TCB/DAF/Pandora only if the design requires those runtime features.

---

# Recipe 6 — Combat attack with modern runtime features

1. Produce clean attack HKX.
2. OAR-test the attack alone.
3. Add AMR if the actor travels.
4. Add Precision for collision.
5. Add framework behavior (for example BFCO) only after the animation itself is stable.
6. Add payload/TCB features one at a time.
7. Validate exact game/SKSE/plugin versions.

---

# Recipe 7 — ScreenArcherMenu pose → HKX pose file

Use [convertSAM](https://www.nexusmods.com/skyrimspecialedition/mods/177216).

Workflow concept:
1. create pose in ScreenArcherMenu
2. save YAML
3. convert to standard HKX static pose
4. inspect weapon-node rotations
5. manually correct weapon nodes if needed
6. deploy through your chosen pose/OAR system

This is a static-pose specialist shortcut, not a general VMD animation converter.

---

# Recipe 8 — Custom-skeleton HKX will not import

1. Determine exact skeleton used to author animation.
2. Compare target bone count/layout.
3. Inspect with [ck-cmd](https://github.com/aerisarn/ck-cmd).
4. Use [Reskeletor](https://www.nexusmods.com/skyrimspecialedition/mods/182890) when appropriate to normalize expanded custom-skeleton tracks.
5. Re-import against exact intended skeleton.
6. Revalidate before runtime testing.

---

# Recipe 9 — Creature animation

1. extract correct creature `skeleton.hkx`
2. use creature-specific rig/workflow
3. animate/bake
4. export against creature skeleton
5. fresh re-import
6. OAR-test replacement if applicable
7. generate creature behaviors with Pandora only when needed

For dragons: [Blender Dragon Rig](https://www.nexusmods.com/skyrimspecialedition/mods/175903).

---

# Recipe 10 — Cinematic interaction scene

1. finish all actor HKX clips
2. validate paired alignment
3. add facial performance with [Performance Capture](https://www.nexusmods.com/skyrimspecialedition/mods/174030) if desired
4. sequence interactions with the appropriate runtime framework
5. add [FreeCamera Framework](https://www.nexusmods.com/skyrimspecialedition/mods/174046) camera timeline
6. test from clean scene start
7. verify exit/reset behavior

---

## Recipe rule

If a recipe fails, return to the **last proven gate**, not to a random earlier tool. That is how you avoid spending hours changing the wrong layer.
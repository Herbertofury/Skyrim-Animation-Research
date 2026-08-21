# Troubleshooting

## The rule that saves the most time

Separate failures into four layers:

1. **Source motion** — VMD/MMD is already wrong or Blender evaluates it differently.
2. **Retarget/bake** — Skyrim target depends on constraints or loses layered motion.
3. **HKX/skeleton** — serialization, skeleton binding, edition/platform, annotations.
4. **Runtime/behavior** — OAR, Pandora, AMR, combat plugins, paired logic, game-version compatibility.

Never change all four layers at once.

---

# Golden isolation order

1. Prove original source.
2. Prove Blender/MMD evaluation.
3. Prove baked Skyrim target with source constraints disabled.
4. Prove exported HKX by fresh re-import.
5. Inspect annotations.
6. Test simple OAR replacement.
7. Add root motion / paired / behavior / combat systems one at a time.

---

# Symptom → cause → fix matrix

| Symptom | Most likely cause | Diagnostic | Modern fix |
|---|---|---|---|
| VMD looks right in MMD but loses vertical bounce in Blender/Skyrim | Center/Groove/Waist/Mother motion lost or flattened incorrectly | Inspect those controls at known high/low frames | Retarget evaluated result; Finekit/MMDBridge only where diagnosis proves needed |
| Feet/legs differ immediately after MMD import | Blender IK differs from MMD | Compare source playback against Blender before retargeting | MMDBridge/MMD-native evaluation; bake trusted result |
| Pose is correct but body translation is missing | Naive hip→pelvis mapping | Check Center/Groove/Mother translation | Transfer layered body controls intentionally |
| Animation changes when retarget constraints are removed | Target was not fully baked | Disable constraints and compare | Bake visual location/rotation every frame |
| HKX export fresh re-import differs | Wrong skeleton/bone order, bake or exporter issue | Fresh scene + same `skeleton.hkx` | Fix export/skeleton before Skyrim runtime |
| Wrong tracks / broken binding | `skeleton.nif`-only or wrong target skeleton | Verify exact target `skeleton.hkx` | Import/use correct HKX skeleton |
| ConvertUI creates empty folder | Legacy platform/skeleton/serialization mismatch | Compare known-good LE-compatible HKX | Stop using ConvertUI for new work; PyNifly/serde-hkx/Composite GUI |
| Custom HCT export fails but downgraded vanilla animation converts | Custom HKX format/binding mismatch | Inspect structure/platform/binding | Export with modern Skyrim HKX tooling |
| Blender looks correct but game A-poses | Runtime behavior/format compatibility | Confirm HKX round-trip first | Check OAR/behavior requirements/Pandora/Universal Behavior Runtime |
| Simple replacer does nothing | OAR path/config/condition issue | Simplify to unconditional replacement | Use OAR diagnostics/editor and rebuild conditions incrementally |
| Paired actors desync | actor order/alignment/events/world motion | Test each clip and shared contact frames | Fix authored alignment + paired runtime/annotations |
| Paired event never fires | annotation/runtime support missing | Dump final HKX annotations | HKXC Anno GUI + Paired Animation Improvements |
| Visible bounce works but actor does not move through world | bone translation ≠ actor-world displacement | Compare skeleton vs actor world position | AMR `animmotion`/rotation or intended runtime displacement |
| Actor slides/snaps during root motion | incorrect annotations or runtime interference | Test without combat/runtime modifiers | Correct AMR timing; test Animation Motion Fix |
| Root motion becomes reduced/stuck in combat | runtime motion handling conflict | Compare out-of-combat vs combat | Animation Motion Fix; isolate framework |
| Animation queue stalls under huge OAR library | animation request queue overload | minimal vs full replacement set | Animation Queue Fix |
| Custom-skeleton HKX cannot import | extra XPMSSE/3BA/SMP tracks | inspect bone count/layout | Reskeletor + ck-cmd or exact deployed skeleton |
| Long annotation text is truncated/awkward | marker/editor limitation | compare final HKX annotation | Skyrim Annotation add-on / HKXC Anno GUI |
| Combat payload does nothing | syntax/dependency/runtime mismatch | verify exact payload and DLL/game versions | Validate PI or use framework-specific event tool |
| Payload Interpreter fails on 1.6.1170 | exact file/DLL/runtime mismatch; reports mixed | test exact dependency set | Do not assume universal support; validate exact combination |
| ScreenArcherMenu pose converts with weapon rotation issue | convertSAM weapon-node limitation | inspect weapon nodes | clean those rotations manually |

---

# Decision trees

## Missing VMD bounce

**Does source MMD show bounce?**
- No → source file/model problem.
- Yes → compare Blender evaluation.

**Does Blender MMD evaluation show bounce?**
- No → inspect Center/Groove/Mother/IK and use source fidelity tools.
- Yes → inspect retarget target.

**Does baked target show bounce after constraints off?**
- No → retarget/bake problem.
- Yes → export HKX.

**Does fresh HKX re-import show bounce?**
- No → HKX/skeleton/export problem.
- Yes → runtime/OAR problem.

---

## A-pose in game

1. Does HKX re-import correctly offline?
   - **No:** fix HKX/skeleton.
   - **Yes:** continue.
2. Does simple OAR replacement discover the file?
   - **No:** path/config/condition.
   - **Yes:** continue.
3. Does animation require generated behavior?
   - **Yes:** Pandora/behavior layer.
   - **No:** runtime compatibility/plugin conflict.
4. Test Universal Behavior Runtime/A-Pose Fix when applicable.

---

## Root motion wrong

1. Is visual skeleton motion correct offline?
2. Are AMR annotations present in final HKX?
3. Does minimal runtime move the actor correctly?
4. Does combat/runtime framework change the result?
5. Is a second system also moving/rotating the actor?

Avoid double-motion from two independent systems.

---

# Useful diagnostic tools

- Finekit: https://www.finekit.co.jp/base/index2e.html
- MMDBridge: https://github.com/rintrint/mmdbridge
- PyNifly: https://github.com/BadDogSkyrim/PyNifly
- HKX_View/Edit: https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184
- serde-hkx: https://github.com/SARDONYX-sard/serde-hkx
- HKXC Anno GUI: https://www.nexusmods.com/skyrimspecialedition/mods/166435
- Reskeletor: https://www.nexusmods.com/skyrimspecialedition/mods/182890
- ck-cmd: https://github.com/aerisarn/ck-cmd
- OAR: https://www.nexusmods.com/skyrimspecialedition/mods/92109

If the problem comes from an old tutorial, continue to **[Legacy Migration](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Legacy-Migration)**.
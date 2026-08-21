# Modern 2026 VMD / MMD → Skyrim HKX Workflow

This is the current recommended workflow distilled from the research database. The live sortable workbook remains the exhaustive source: https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit

## 1. Preserve the untouched source
Keep the original VMD and PMX/PMD unchanged. Work from copies so every conversion can be compared against the original motion.

## 2. Preflight the VMD
Use Finekit VMD Checker or direct MMD inspection to determine where the motion actually lives. Check **Center (センター), Groove (グルーブ), Waist, Mother/All Parent, Leg-D and IK bones**. Do not assume vertical bounce lives on a pelvis/hip bone.

Finekit: https://www.finekit.co.jp/base/index2e.html

## 3. Import in a current MMD stack
Use **MMD Tools 4.5.13**. Its current README documents Blender **4.2–5.1** for the v4.x line. Blender 5.2 LTS is current and PyNifly supports it, but MMD Tools does not yet explicitly document 5.2 compatibility.

MMD Tools: https://extensions.blender.org/add-ons/mmd-tools/
Source: https://github.com/MMD-Blender/blender_mmd_tools

Keep original MMD bone names while diagnosing the source.

## 4. Prove MMD evaluation fidelity before retargeting
MMD Tools explicitly warns that Blender IK differs from MMD. If feet, bounce, physics, or other motion differs from the source, do **not** continue downstream.

Use MMDBridge when exact MMD-native IK/physics evaluation is needed:
https://github.com/rintrint/mmdbridge

Useful source-side repair/normalization options include Finekit VMDTMS, VMD Retarget, VMD Bake, MMD MotionSupporter, and MikuMikuMoving Integrate Layer.

## 5. Normalize only the proven problem
Do not blindly flatten every VMD. If diagnosis shows Mother/Center misuse, FK/IK issues, or troublesome layered controls, correct those specific problems. Dense per-frame baking is a fallback when interpolation/layer semantics are otherwise being lost.

## 6. Use Skyrim timing deliberately
Use a consistent sampling rate, normally **30 FPS** for Skyrim/Havok animation workflows, and verify duration/frame count before and after the bake.

## 7. Import the real Skyrim `skeleton.hkx`
For animation authoring, the HKX skeleton is authoritative. PyNifly documentation recommends importing `skeleton.hkx`, not relying only on `skeleton.nif`, because HKX contains animation skeleton data and bone ordering used for bindings.

PyNifly: https://github.com/BadDogSkyrim/PyNifly
Animation guide: https://github.com/BadDogSkyrim/PyNifly/blob/main/ANIMATIONS.md

## 8. Pick one target/control-rig family
Strong current choices include:
- Coach's Enhanced Blender Animation Rigs: https://www.nexusmods.com/skyrimspecialedition/mods/148736
- NickNak Blender Animation Rigs v5: https://www.nexusmods.com/skyrimspecialedition/mods/118525
- RigifyRig by Bogdan: https://www.nexusmods.com/skyrimspecialedition/mods/180970

Keep one deform/export skeleton authoritative. Avoid duplicate competing Skyrim armatures.

## 9. Build an explicit retarget map
Map anatomy normally, but treat MMD's Center/Groove/Waist/Mother controls as layered motion rather than blindly mapping hip → pelvis.

Blender VMD Retargeting is valuable reference material because it explicitly models Center/Groove/Waist layers and evaluated-frame retargeting:
https://github.com/butaixianran/Blender-Vmd-Retargeting

A current generic Blender 5 retargeter with an MMD preset is also available:
https://github.com/KBSBAUDRICE/Retarget

## 10. Bake the evaluated Skyrim target
Bake the **visual/evaluated target**, not raw source F-curves. Bake location + rotation every frame with visual keying. Then disable/remove the source constraints and confirm the target animation does not change.

## 11. Export directly to HKX
Prefer a modern native HKX path:
- PyNifly 28.x: https://github.com/BadDogSkyrim/PyNifly
- Current blender-hkx fork used by modern Skyrim rigs: https://github.com/beefclot/blender-hkx

For ordinary character animations there is no reason to insert a mandatory `HKX → KF → HKX` conversion stage.

## 12. Round-trip in a fresh scene
Create a new Blender scene, import the same target `skeleton.hkx`, and import the finished HKX. Compare:
- vertical bounce extrema,
- foot contacts,
- hand/hip positions,
- timing,
- root/COM movement,
- and important event frames.

If it fails here, debug the bake/export/skeleton. Do not start modifying Skyrim behaviors yet.

## 13. Inspect the final HKX outside the work scene
Current tools include Smooth HKX_View/HKX_Edit and modern HKX inspection/conversion backends.

HKX_View/Edit announcement: https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184
serde-hkx/hkxc: https://github.com/SARDONYX-sard/serde-hkx

## 14. Add or repair annotations
Useful current tools:
- HKXC Anno GUI 2.0: https://www.nexusmods.com/skyrimspecialedition/mods/166435
- Skyrim Annotation Blender add-on: https://github.com/skypia0147-dev/blender-skyrim-annotation

Use these for footsteps, animation events, Precision markers, AMR annotations, paired events, and other exact-frame metadata.

## 15. Handle real actor displacement separately
Visible pelvis/root bone movement is not necessarily physical actor movement through Skyrim's world.

Animation Motion Revolution remains the main annotation-driven solution for intentional actor displacement/rotation:
https://www.nexusmods.com/skyrimspecialedition/mods/50258

Animation Motion Fix is a current runtime fix worth testing in root-motion-heavy setups:
https://www.nexusmods.com/skyrimspecialedition/mods/145100

## 16. Deploy simple replacements with OAR
For an existing idle/dance/attack replacement, start with Open Animation Replacer rather than generating behaviors unnecessarily.

OAR: https://www.nexusmods.com/skyrimspecialedition/mods/92109
OAR External Tool: https://github.com/skypia0147-dev/OAR-External-Tool

## 17. Generate behaviors only when genuinely required
Use Pandora when adding behavior graphs/events/types actually requires behavior generation.

Pandora Behaviour Engine Plus: https://www.nexusmods.com/skyrimspecialedition/mods/133232

Do not add behavior-engine complexity to a plain replacer.

## 18. Treat paired animations as their own runtime case
Paired clips have alignment, actor ordering, event, annotation and synchronization constraints beyond ordinary single-actor HKX.

Paired Animation Improvements: https://www.nexusmods.com/skyrimspecialedition/mods/99621

For annotation-driven paired/combat actions, current specialist tooling includes Trigger Combat Behaviour:
https://www.nexusmods.com/skyrimspecialedition/mods/167256

## 19. Separate runtime defects from bad exports
If the HKX round-trips correctly but Skyrim A-poses, stalls, loses motion, or fails only in combat, investigate runtime compatibility before re-exporting the animation.

Examples in the database include Universal Behavior Runtime/A-Pose Fix, Animation Motion Fix, Animation Queue Fix, OAR, Pandora and paired-animation runtime fixes.

## 20. Final acceptance test
A finished conversion should pass all of these:
- original MMD source visually verified,
- Center/Groove/Mother/IK source channels understood,
- Skyrim target baked with source constraints disabled,
- correct `skeleton.hkx` used,
- exported HKX round-trips in a fresh scene,
- annotations/events inspected,
- OAR or intended runtime path loads it,
- no A-pose or binding failure,
- visible bounce survives,
- true actor travel works only when intentionally authored,
- paired/combat behavior tested separately when relevant.

## Legacy path
The old Blender 2.49 → FBX → 3ds Max → Havok Content Tools → ConvertUI → KF → HKX chain is preserved only for historical compatibility. See `LEGACY.md` for the replacement matrix.

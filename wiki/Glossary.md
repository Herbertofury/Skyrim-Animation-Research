# Glossary

## Animation / DCC

**Bake / Baking** — convert evaluated constraints/IK/drivers into ordinary keyframes so the target no longer depends on the source setup.

**DCC** — Digital Content Creation application such as Blender, 3ds Max or Cascadeur.

**Evaluated pose** — the final transform after constraints, IK, drivers and hierarchy have been applied.

**FK** — Forward Kinematics; bones are rotated through the hierarchy directly.

**IK** — Inverse Kinematics; end targets drive a bone chain. MMD and Blender IK solvers can produce different results.

**Retargeting** — transferring animation from one skeleton/rig to another.

**Rigify** — Blender's rig-generation/control-rig system; several Skyrim workflows build around it.

---

## MMD / VMD

**MMD** — MikuMikuDance ecosystem.

**VMD** — MikuMikuDance motion-data format.

**PMX / PMD** — MMD model formats.

**Center `センター`** — important MMD body-position controller; can carry motion that should not be confused with conventional hips/pelvis animation.

**Groove `グルーブ`** — MMD controller often layered with Center for extra positional/vertical motion.

**Mother / All Parent `全ての親`** — whole-model parent transform used by some motions.

**Leg-D** — MMD leg-related control structure encountered in motion-processing workflows.

**Integrate Layer** — MikuMikuMoving workflow that can collapse layered/interpolated motion into a denser explicit result.

---

## Skyrim / Havok

**HKX** — Havok binary container used for Skyrim animation/skeleton/behavior data.

**`skeleton.hkx`** — the animation skeleton/binding reference; authoritative for animation bone ordering in the modern workflow.

**`skeleton.nif`** — visual/model skeleton asset; useful reference but not a replacement for the animation skeleton HKX.

**LE / Oldrim** — original 32-bit Skyrim release ecosystem.

**SE / AE** — Skyrim Special Edition / Anniversary Edition ecosystem.

**KF** — older NetImmerse/Gamebryo keyframe format seen in historic conversion workflows; not required in the default modern pipeline.

**HCT** — Havok Content Tools; historic Havok authoring/conversion suite.

**Round-trip** — export an HKX, then import the resulting HKX into a fresh scene using the same skeleton and compare it with the source/baked target.

---

## Runtime

**OAR** — Open Animation Replacer; current conditional animation replacement framework.

**DAR** — Dynamic Animation Replacer; legacy predecessor superseded by OAR.

**Pandora** — modern behavior-generation engine used when behavior graph changes are required.

**FNIS / Nemesis** — older behavior-generation ecosystems retained for compatibility cases.

**AMR** — Animation Motion Revolution; annotation-driven actor translation/rotation runtime system.

**PIE / Payload Interpreter** — event-payload runtime mechanism used by some combat/animation frameworks.

**Precision** — melee collision framework that can align collision with authored attack motion.

**Paired animation** — synchronized animation involving two actors/participants with shared alignment/timing requirements.

---

## Motion concepts

**Visual root motion** — root/pelvis/COM bone translation visible inside the animation.

**Actor-world displacement** — Skyrim actually moves the actor's world transform.

**Extracted/reference-frame motion** — Havok animation-format motion/reference data; related to but not identical to game-world actor movement.

**Foot sliding** — visible movement of a planted foot caused by retarget, IK, root translation or runtime motion mismatch.

**A-pose** — runtime failure state often indicating animation/behavior/skeleton compatibility trouble rather than bad artistic motion itself.
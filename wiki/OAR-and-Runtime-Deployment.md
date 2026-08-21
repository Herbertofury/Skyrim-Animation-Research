# OAR & Runtime Deployment

The fastest way to prove a finished HKX is to deploy it with the **simplest possible runtime path**.

## Open Animation Replacer (OAR)

Nexus:
https://www.nexusmods.com/skyrimspecialedition/mods/92109

Source:
https://github.com/ersh1/OpenAnimationReplacer

Use OAR as the default deployment/test layer for:
- idles
- dances
- locomotion replacements
- attacks replacing existing animation slots
- conditional variants
- character-specific sets
- many creature replacements

### Why OAR first

A simple replacement should not require you to debug:
- behavior generation
- new animation-event graphs
- combat frameworks
- paired runtimes
- root-motion plugins

Prove the HKX first, then add conditions/complexity.

---

## OAR External Tool

https://github.com/skypia0147-dev/OAR-External-Tool

Useful for building/editing OAR configuration outside Skyrim and auditing conditions without repeatedly launching the game.

---

## Minimal deployment test

1. Use an HKX that already passes a fresh Blender round-trip.
2. Replace one known animation in the simplest unconditional way supported by your test setup.
3. Launch Skyrim.
4. Use OAR diagnostics/in-game editor to confirm the replacement is discovered.
5. Trigger the animation.
6. Verify animation timing and pose.
7. Only then add conditions.

If OAR does not discover the replacement, debug **path/config/condition/runtime** before touching the HKX again.

---

## Condition debugging

When a complex condition fails:

1. temporarily simplify to an unconditional replacement
2. confirm animation loads
3. add one condition at a time
4. verify actor/reference context
5. verify weapon/equipment/state conditions
6. verify ordering/priority relative to other replacers

For equipment-placement logic, specialist extension:
https://www.nexusmods.com/skyrimspecialedition/mods/98308

---

## Large animation libraries

### Animation Queue Fix
https://www.nexusmods.com/skyrimspecialedition/mods/82395

Useful when very large replacement libraries overload the runtime animation request queue.

Do not use it to hide a broken individual animation; first prove the issue only appears under large library load.

---

## A-pose / runtime format problems

### A-Pose Bug Fix / Universal Behavior Runtime
https://www.nexusmods.com/skyrimspecialedition/mods/168903

Useful modern compatibility layer when animations/behaviors fail at runtime even though offline HKX validation is clean.

If an animation round-trips correctly but A-poses only in game, investigate runtime/behavior compatibility rather than reauthoring the motion blindly.

---

## Runtime kinematic corrections

### Universal Kinematics
https://www.nexusmods.com/skyrimspecialedition/mods/185777

A very new 2026 procedural locomotion/kinematics tool. Keep it in mind when in-game locomotion differs from authored HKX because runtime correction itself may be influencing the result.

---

## Interaction frameworks

### Dynamic Animation Framework
https://www.nexusmods.com/skyrimspecialedition/mods/158262

Use when you need JSON-driven animation chains triggered by gameplay/UI events and interaction logic.

### Effect Animation Framework
https://www.nexusmods.com/skyrimspecialedition/mods/171917

Use when animations should trigger from magic-effect activation without attaching custom scripts to every effect.

---

## When OAR is not enough

Move beyond OAR when you need:
- new behavior graph entries
- new animation event types
- framework-specific behavior patches
- paired/interaction systems with behavior dependencies
- combat frameworks that require generated behaviors
- creature behavior graph changes

Then continue to **[Behaviors with Pandora](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Behaviors-with-Pandora)**.

---

## Runtime acceptance checklist

- [ ] HKX passes offline round-trip first
- [ ] simplest OAR replacement works
- [ ] OAR discovers intended file/config
- [ ] complex conditions added incrementally
- [ ] runtime plugin versions match game/SKSE
- [ ] behavior generation added only if needed
- [ ] large-library fixes used only for proven queue/load problems
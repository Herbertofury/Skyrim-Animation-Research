# Paired Animations & Combat

Paired/interacting actors and combat movesets add constraints that ordinary single-actor animation does not have: **alignment, ordering, event synchronization, world movement, collision timing and behavior dependencies**.

---

# Paired animation fundamentals

Validate each actor's clip independently first.

Then validate the pair together:
- actor A origin
- actor B origin
- facing/orientation
- start distance
- synchronized frame zero
- shared contact frames
- root/world movement
- event annotations
- stop/exit behavior

Do not use runtime snapping to hide fundamentally misaligned animation authoring.

---

## Paired Animation Improvements

https://www.nexusmods.com/skyrimspecialedition/mods/99621

Recommended when annotations/events inside paired animations must work normally at runtime.

Use alongside exact annotation inspection:
https://www.nexusmods.com/skyrimspecialedition/mods/166435

---

## Trigger Combat Behaviour (TCB)

https://www.nexusmods.com/skyrimspecialedition/mods/167256

2026 specialist framework for annotation-driven actions including:
- paired animation triggers
- stagger
- i-frames
- snap target
- stop time
- other combat/runtime behavior commands

Use it when these features match your combat/interaction design; it is not needed for a simple dance or idle.

---

# Combat animation stack

## OAR
https://www.nexusmods.com/skyrimspecialedition/mods/92109

Use for selecting/replacing attack animation sets.

## AMR
https://www.nexusmods.com/skyrimspecialedition/mods/50258

Use when attacks/lunges/dodges must move the actor through the world.

## Precision
https://www.nexusmods.com/skyrimspecialedition/mods/72347

Use when melee collision should follow authored animation geometry/timing accurately.

## BFCO
https://www.nexusmods.com/skyrimspecialedition/mods/117052

Current combat animation behavior framework when building for that ecosystem.

Research snapshot: 3.100.5, July 2026.

## Payload Interpreter
https://www.nexusmods.com/skyrimspecialedition/mods/65089

Source:
https://github.com/D7ry/PayloadInterpreter

Useful for PIE payload execution in compatible setups.

**2026 warning:** reports around Skyrim 1.6.1170 are mixed. Validate the exact DLL/file/runtime combination before depending on it.

## Apply Impulse
https://www.nexusmods.com/skyrimspecialedition/mods/181584

Use when an exact animation moment should impart physics impulse or actor rotation.

---

## Behavior generation

If a combat framework requires behavior graph changes, use [Pandora](https://www.nexusmods.com/skyrimspecialedition/mods/133232).

If the project is only replacing an existing attack within a framework that already provides behavior logic, do not regenerate behavior unnecessarily.

---

## Combat verification ladder

1. baked Blender target
2. fresh HKX round-trip
3. animation alone in OAR
4. annotations/events
5. AMR/world motion if needed
6. collision system
7. payload/runtime command systems
8. behavior framework
9. full combat modlist

When a step fails, return only one level—not all the way back to VMD source unless evidence points there.

---

## Paired/combat acceptance checklist

- [ ] each actor clip works independently
- [ ] paired origins/facing align
- [ ] contact frames synchronize
- [ ] event annotations survive HKX export
- [ ] actor-world motion is intentional
- [ ] collision windows align with animation
- [ ] payload/runtime dependencies tested on exact game version
- [ ] behavior generation present only when required
- [ ] full stack tested after minimal stack passes
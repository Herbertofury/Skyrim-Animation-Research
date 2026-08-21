# Behaviors with Pandora

## Pandora Behaviour Engine Plus

https://www.nexusmods.com/skyrimspecialedition/mods/133232

Pandora is the current behavior-generation recommendation in this research when an animation project genuinely needs behavior patching/generation.

Research snapshot: **4.4.0-beta**, August 2026 stable-labelled build line.

---

## First question: do you need a behavior engine?

### You probably do **not** need Pandora if:
- you are replacing an existing idle
- you are replacing an existing dance/gesture slot
- you are replacing an existing attack and your runtime framework already supplies the behavior
- OAR alone can conditionally select the HKX

### You likely **do** need Pandora if:
- adding new animation events/behavior nodes
- a framework explicitly ships a Pandora/FNIS/Nemesis-style behavior patch
- adding creature behavior changes
- installing a combat/interaction framework whose behavior graph must be generated
- adding movement-offset/behavior resources that require generation

---

## Safe behavior workflow

1. Prove the HKX offline.
2. Prove a simple runtime replacement if possible.
3. Record the exact behavior-dependent mod/framework.
4. Install/configure Pandora for that requirement.
5. Generate behaviors.
6. Test only the new behavior path first.
7. Verify no unrelated animation categories regressed.
8. Then restore the full modlist/runtime stack.

This keeps a behavior-generation defect from being confused with a bad animation export.

---

## Creature support

Pandora is especially relevant when behavior generation must include creatures. Do not assume old humanoid-only behavior workflows generalize to creature graphs.

See **[Creatures, Facial & Cinematics](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Creatures-Facial-and-Cinematics)**.

---

## Legacy behavior engines

### Nemesis Unlimited Behavior Engine
https://www.nexusmods.com/skyrimspecialedition/mods/60033

Keep for compatibility with projects that still require it. Do not choose it for new work merely because an old guide does.

### FNIS SE
https://www.nexusmods.com/skyrimspecialedition/mods/3038

Legacy ecosystem support only.

### Dynamic Animation Replacer
https://www.nexusmods.com/skyrimspecialedition/mods/33746

Superseded by OAR for new conditional-replacement work.

---

## Runtime A-pose distinction

If:
- the HKX imports correctly in a fresh Blender scene
- the skeleton binding is correct
- annotations look correct
- but Skyrim A-poses

then test runtime behavior/compatibility before re-exporting.

Useful current compatibility layer:
https://www.nexusmods.com/skyrimspecialedition/mods/168903

---

## Pandora checklist

- [ ] animation itself already verified
- [ ] project has a concrete behavior-generation requirement
- [ ] exact dependent framework identified
- [ ] current Pandora build chosen for target setup
- [ ] generation completes cleanly
- [ ] intended event/behavior works
- [ ] unrelated animations still work
- [ ] no unnecessary Nemesis/FNIS duplication in the new workflow

Next: **[Paired Animations & Combat](https://github.com/Herbertofury/Skyrim-Animation-Research/wiki/Paired-Animations-and-Combat)**.
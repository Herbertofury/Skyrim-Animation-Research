# Creatures, Facial Animation & Cinematics

Skyrim animation research is bigger than the humanoid third-person skeleton. This page covers the specialist 2026 tools that matter for creatures, facial performance and camera-driven scenes.

---

# Creature animation

## Blender Dragon Rig

https://www.nexusmods.com/skyrimspecialedition/mods/175903

Current 2026 Rigify-oriented resource for Skyrim dragon animation authoring.

Important workflow notes from the research snapshot:
- creature-specific target skeleton
- export workflow uses Skyrim/Coach-style tooling
- LE dragon `skeleton.hkx` reference is part of the documented export approach
- existing-animation import is not its main strength

Treat it as a creature-specific authoring resource, not a humanoid retarget preset.

### Creature behavior generation
[Pandora](https://www.nexusmods.com/skyrimspecialedition/mods/133232) is the current behavior-engine choice in this research when creature behavior generation is needed.

### Creature OAR
[OAR](https://www.nexusmods.com/skyrimspecialedition/mods/92109) can be useful for creature replacements where its runtime conditions/replacement support fit the project.

### Creature rule
Never force humanoid assumptions about pelvis/root/finger/IK structure onto a creature skeleton. Start from the actual creature `skeleton.hkx`.

---

# Facial performance capture

## Performance Capture

https://www.nexusmods.com/skyrimspecialedition/mods/174030

2026 specialist cinematic/facial tool using webcam + MediaPipe-style capture into Blender/Skyrim facial-expression workflows.

Research notes include:
- 52 ARKit-style expression channels
- Blender preview workflow
- real-time Skyrim facial-expression use
- support claims for multiple head/race setups with documented exceptions

Verify current runtime requirements and dependencies from the mod page before building a production pipeline around it.

---

# Cinematic cameras

## FreeCamera Framework

Nexus:
https://www.nexusmods.com/skyrimspecialedition/mods/174046

Source:
https://github.com/staalo18/FreeCameraFramework

2026 framework for:
- recorded camera paths
- programmatic timelines
- interpolation/easing
- multiple timelines
- YAML import/export
- event callbacks
- world/reference-relative control points

Use it to make a finished animation scene feel authored rather than simply watching the default game camera.

---

# Interaction sequencing

## Dynamic Animation Framework
https://www.nexusmods.com/skyrimspecialedition/mods/158262

Useful for JSON-driven animation chains triggered by gameplay/UI events and for interaction-style sequences.

## Effect Animation Framework
https://www.nexusmods.com/skyrimspecialedition/mods/171917

Useful when magic/effect activation should trigger animations cleanly.

---

# Cinematic production order

1. Finish body animation first.
2. Verify HKX/paired alignment.
3. Add facial performance.
4. Add world displacement/interactions.
5. Add camera timeline.
6. Add gameplay/effect triggers.
7. Test the complete scene from a clean start.

Do not use camera motion to hide broken actor alignment or foot sliding.

---

## Specialist acceptance checklist

### Creature
- [ ] correct creature `skeleton.hkx`
- [ ] creature-specific bone map
- [ ] correct behavior generation if needed
- [ ] creature replacement tested independently

### Facial
- [ ] capture profile matches target face/race setup
- [ ] expression channels verified before body/camera integration
- [ ] exact runtime dependencies tested

### Cinematic
- [ ] actor animation works without camera framework
- [ ] camera path starts in correct reference space
- [ ] event callbacks align with actor timing
- [ ] YAML/timeline persistence verified
- [ ] full scene reproducible from clean start
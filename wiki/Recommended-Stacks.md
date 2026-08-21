# Recommended Stacks

Use this page to avoid the two biggest Skyrim-animation setup mistakes: **installing too much** and **using a legacy tool simply because an old tutorial mentions it**.

## 🟢 Stack A — Default VMD/MMD → Skyrim animation

**Use for:** dances, idles, gestures, normal single-character motions.

1. [MMD Tools](https://extensions.blender.org/add-ons/mmd-tools/)
2. [Finekit VMD tools](https://www.finekit.co.jp/base/index2e.html)
3. [MMDBridge](https://github.com/rintrint/mmdbridge) only if MMD evaluation differs
4. [PyNifly](https://github.com/BadDogSkyrim/PyNifly)
5. One Skyrim control rig: [Coach](https://www.nexusmods.com/skyrimspecialedition/mods/148736), [NickNak](https://www.nexusmods.com/skyrimspecialedition/mods/118525), or [RigifyRig](https://www.nexusmods.com/skyrimspecialedition/mods/180970)
6. [HKX_View/Edit](https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184) and/or [serde-hkx](https://github.com/SARDONYX-sard/serde-hkx)
7. [OAR](https://www.nexusmods.com/skyrimspecialedition/mods/92109)

**Do not add by default:** Pandora, AMR, Payload Interpreter, KF conversion, Havok Content Tools.

---

## 🟢 Stack B — Skyrim-native Blender authoring

**Use for:** animations created directly for Skyrim.

- Blender
- Coach / NickNak / RigifyRig
- PyNifly or current blender-hkx fork: https://github.com/beefclot/blender-hkx
- Skyrim Annotation Blender Add-on: https://github.com/skypia0147-dev/blender-skyrim-annotation
- HKXC Anno GUI: https://www.nexusmods.com/skyrimspecialedition/mods/166435
- OAR for deployment

Optional motion polish: [Cascadeur](https://cascadeur.com/download)

---

## 🔵 Stack C — True root motion / world displacement

**Use for:** attacks, dodges, lunges, locomotion, interactions where the actor must physically move through the world.

Base stack +:

- [Animation Motion Revolution](https://www.nexusmods.com/skyrimspecialedition/mods/50258)
- [Animation Motion Fix](https://www.nexusmods.com/skyrimspecialedition/mods/145100) when affected by runtime root-motion issues
- [HKXC Anno GUI](https://www.nexusmods.com/skyrimspecialedition/mods/166435) or the Blender annotation add-on
- [HKX_Edit](https://www.patreon.com/SmoothAanimation/posts/animation-tool-162933184) when its current toolset helps author/inspect motion

Optional exact-frame physics/rotation: [Apply Impulse](https://www.nexusmods.com/skyrimspecialedition/mods/181584)

**Important:** pelvis translation is not automatically actor-world translation.

---

## 🟣 Stack D — Paired / interaction animation

Base stack +:

- [Paired Animation Improvements](https://www.nexusmods.com/skyrimspecialedition/mods/99621)
- Annotation tooling
- OAR
- [Dynamic Animation Framework](https://www.nexusmods.com/skyrimspecialedition/mods/158262) when JSON-driven interaction chains fit the project
- Pandora only when behavior generation is required

For advanced annotation-triggered paired/combat actions: [Trigger Combat Behaviour](https://www.nexusmods.com/skyrimspecialedition/mods/167256)

---

## 🔴 Stack E — Combat animation

Base stack + the minimum runtime features needed:

- [OAR](https://www.nexusmods.com/skyrimspecialedition/mods/92109)
- [AMR](https://www.nexusmods.com/skyrimspecialedition/mods/50258) when attacks translate/rotate the actor
- [Precision](https://www.nexusmods.com/skyrimspecialedition/mods/72347) for animation-aligned melee collision
- [BFCO](https://www.nexusmods.com/skyrimspecialedition/mods/117052) if building around that combat behavior ecosystem
- [Trigger Combat Behaviour](https://www.nexusmods.com/skyrimspecialedition/mods/167256) when its annotation triggers match your design
- [Payload Interpreter](https://www.nexusmods.com/skyrimspecialedition/mods/65089) only after exact runtime validation

**Payload Interpreter warning:** 2026 reports for Skyrim 1.6.1170 are mixed across files/setups. Do not make it a hard dependency without testing your exact runtime/DLL combination.

---

## 🐉 Stack F — Creature animation

- Creature-specific target skeleton
- [Blender Dragon Rig](https://www.nexusmods.com/skyrimspecialedition/mods/175903) for dragon work
- PyNifly / appropriate HKX exporter
- HKX_View/Edit for inspection where supported
- Pandora when creature behavior generation is needed
- OAR where creature replacement rules fit

Do not force humanoid retarget assumptions onto creature skeletons.

---

## 🎬 Stack G — Cinematic / facial animation

- Base body-animation stack
- [Performance Capture](https://www.nexusmods.com/skyrimspecialedition/mods/174030) for webcam/MediaPipe facial performance
- [FreeCamera Framework](https://www.nexusmods.com/skyrimspecialedition/mods/174046) for recorded/programmatic camera timelines
- [Dynamic Animation Framework](https://www.nexusmods.com/skyrimspecialedition/mods/158262) for interaction sequencing when appropriate
- [Effect Animation Framework](https://www.nexusmods.com/skyrimspecialedition/mods/171917) for effect-driven triggers when appropriate

---

## 🛟 Stack H — Legacy rescue / format diagnosis

Use only when old assets/tutorials force it:

- [serde-hkx / hkxc](https://github.com/SARDONYX-sard/serde-hkx)
- [Composite HKX Conversion GUI](https://www.nexusmods.com/skyrimspecialedition/mods/154237)
- [Reskeletor](https://www.nexusmods.com/skyrimspecialedition/mods/182890)
- [ck-cmd](https://github.com/aerisarn/ck-cmd)
- PyNifly

Keep ConvertUI, hkxcmd, hkanno64, FNIS, Nemesis, HCT and KF only when a specific legacy asset or dependency requires them.

---

## Minimalism rule

If a project can be completed with:

**Blender/MMD Tools → PyNifly → OAR**

then do exactly that first. Every extra converter, behavior generator, runtime DLL and format hop creates another place for transforms, annotations, skeleton bindings or compatibility to fail.
# Troubleshooting

Canonical troubleshooting matrix: [`docs/TROUBLESHOOTING.md`](../docs/TROUBLESHOOTING.md)

## Isolation order

1. Prove the original MMD/VMD motion.
2. Prove Blender/MMD evaluated playback.
3. Prove the baked Skyrim target after disabling source constraints.
4. Prove the exported HKX by importing it in a fresh scene on the same `skeleton.hkx`.
5. Only then debug OAR, behaviors, paired logic, payloads, root-motion runtime, or game-version compatibility.

Key cases covered include missing Center/Groove bounce, MMD-vs-Blender IK drift, wrong skeleton binding, ConvertUI empty output, A-pose failures, paired desync, custom-skeleton track counts, root-motion/runtime issues, Payload Interpreter 1.6.1170 compatibility, and convertSAM weapon-node cleanup.

Full matrix: https://github.com/Herbertofury/Skyrim-Animation-Research/blob/main/docs/TROUBLESHOOTING.md

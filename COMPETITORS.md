# Alternative animation tools and workflow comparisons

This repository is a research hub, so the useful competitors are **alternative workflows**, not rival storefronts. Keep the [tool catalog](docs/TOOLS.md), [source ledger](docs/SOURCES.md), [workflow](docs/WORKFLOW.md) and its canonical linked workbook as the detailed source of truth. Existing historical version recommendations are not silently revalidated by this page.

| Primary-source comparator | Role | Proposed comparison |
|---|---|---|
| [PyNifly](https://github.com/BadDogSkyrim/PyNifly) | Blender / game-asset interchange | Evaluate the exact supported animation path against the existing documented export workflow; keep skeleton identity and game variant fixed. |
| [blender-hkx](https://github.com/jgernandt/blender-hkx) | Blender HKX animation import/export | Compare track order, frame timing, annotations and round-trip transform error on identical permitted clips. |
| [MMD Tools](https://github.com/MMD-Blender/blender_mmd_tools) | MMD model and motion import/export | Evaluate source-motion fidelity before attributing retargeting problems to HKX export. |
| Existing MMDBridge, retargeting, annotation and runtime tools | Complementary stages already in the tool catalog | Compare complete pipelines instead of declaring unlike tools interchangeable. Verify exact Blender/game/plugin versions before adoption. |

## Improvement backlog, not accepted results
- [ ] Curate permitted clips covering IK, Center/Groove layering, root motion, paired animation and creatures.
- [ ] Preserve an evaluated source reference, retargeted reference and reimported export for each test.
- [ ] Record bone mapping, units, handedness, skeleton hash, event timing and per-bone error; retain visual video evidence when authorized.
- [ ] Distinguish visual pelvis motion from actual actor displacement in the game.
- [ ] Validate runtime behavior in isolated profiles. A Blender preview or successful export does not establish in-game correctness.
- [ ] Add reproducible troubleshooting cases for concrete regressions instead of merely promoting a new version.
- [ ] Respect licenses: no redistribution of proprietary game skeletons or third-party animation assets.

## Review and evidence rules

Review date: **2026-11-12**. This is a comparison agenda, not a benchmark result or proof of superiority. Official-source capability descriptions and our proposed experiments are separate. Pin actual versions and licenses before reuse; record publication date separately from the date checked. Retain failed comparisons and rejected candidates.

During recurring reviews, inspect upstream releases, breaking changes, security notices and relevant issue reports; add a dated change note only for a meaningful change. Reuse the existing catalogs instead of creating another disconnected list. A missing observation is **unknown**, not unsupported. No new feature is silently authorized merely by appearing here.

For each proposed adoption, record baseline revision, candidate revision, identical workload, required outputs, correctness/security/compatibility checks, latency distribution, memory and reproducible raw evidence. Never make a target-project superiority claim from a synthetic microbenchmark. Keep private assets and traces out of public evidence.

## Publication status

This repository document is the canonical comparison entry point for this addition. A repository-backed wiki page can link to it without duplicating its tables. Native GitHub Wiki publication must be verified separately; a wiki-enabled setting or a source mirror is not publication proof.

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


## Potential foundations and pipeline reuse

| Potential foundation | Specific reusable element to investigate | Improvement opportunity | Proof / compatibility boundary |
|---|---|---|---|
| Existing tool catalog and canonical workbook | Stable source links, stage roles, known limitations and troubleshooting cases | One evidence ledger instead of several inconsistent “best tool” lists | Preserve historical versions and record new checked dates separately; do not overwrite an old compatibility result with an assumption. |
| PyNifly / blender-hkx | Inspect exact import/export APIs and round-trip diagnostics | Reuse a maintained interchange path rather than implement another HKX converter without need | Verify exact Blender, game variant, skeleton and exporter versions; compare transforms, track order, timing and annotations. |
| MMD Tools and documented evaluated-bake alternatives | Inspect motion import, evaluated pose and bake boundaries | Diagnose source evaluation separately from target retargeting/export | Keep IK/physics and Center/Groove behavior in the reference; never call a visually different bake “faster.” |
| Existing annotation/runtime tooling | Reuse documented event contracts and test cases | Explain whether failure arises in authoring, export, behavior generation or runtime | In-game paired/root-motion evidence is required; export success alone is insufficient. |
| Potential Hover / game-tool interoperability | Investigate read-only inspection metadata and diagnostic receipts | Make asset provenance and compatibility understandable without mutating source files | This is an interface hypothesis, not a target-app recommendation. Compare with the target's current parser and preserve full outputs before proposing adoption. |

**Licensing/compatibility:** review each exact upstream and dependency license before reusing code. Separately check permissions for rigs, animation clips, game skeletons and screenshots. A tool license does not license the assets processed by it. Keep proprietary fixtures local and publish only authorized sanitized results.

**Empirical protocol:** pin the complete pipeline and a permitted corpus; record source evaluation, baked output, exported file and clean reimport. Measure per-bone transform error, event/frame drift, conversion duration and memory while preserving fidelity. Then validate real runtime displacement, blending and paired events where relevant. Document failed fixtures and rejected pipeline variants.

**Status:** these are reuse investigations and proposed acceptance criteria. No new plugin integration, target-app upgrade or universal compatibility claim is established.

## Review and evidence rules

Review date: **2026-11-12**. This is a comparison agenda, not a benchmark result or proof of superiority. Official-source capability descriptions and our proposed experiments are separate. Pin actual versions and licenses before reuse; record publication date separately from the date checked. Retain failed comparisons and rejected candidates.

During recurring reviews, inspect upstream releases, breaking changes, security notices and relevant issue reports; add a dated change note only for a meaningful change. Reuse the existing catalogs instead of creating another disconnected list. A missing observation is **unknown**, not unsupported. No new feature is silently authorized merely by appearing here.

For each proposed adoption, record baseline revision, candidate revision, identical workload, required outputs, correctness/security/compatibility checks, latency distribution, memory and reproducible raw evidence. Never make a target-project superiority claim from a synthetic microbenchmark. Keep private assets and traces out of public evidence.

## Publication status

This repository document is the canonical comparison entry point for this addition. A repository-backed wiki page can link to it without duplicating its tables. Native GitHub Wiki publication must be verified separately; a wiki-enabled setting or a source mirror is not publication proof.

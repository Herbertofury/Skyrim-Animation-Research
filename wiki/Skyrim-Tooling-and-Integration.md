# Skyrim SE tooling and integration research: 2026-11-14

## Scope and evidence status

This dated addendum broadens the animation research hub into creation, management, diagnosis and repair **research**, not a new mod manager. Inventory found this existing public research repository and the public [Modhunter application](https://github.com/Herbertofury/Modhunter); reuse their respective documentation and application boundaries rather than create a duplicate repository. No private implementation or account material is included.

The primary sources linked below were reviewed on 2026-11-14. This is source/documentation evidence, **not installed-tool, performance, round-trip or in-game acceptance**. No executable was installed, game/save modified, license accepted or integration implemented for this review. The August catalog counts and canonical Google Sheet remain historical and were not synchronized by this addendum. [Issue #1](https://github.com/Herbertofury/Skyrim-Animation-Research/issues/1) remains open for actual workflow/runtime verification.

## Compatibility findings that change planning

* [SKSE's official download page](https://skse.silverlock.org/) currently pairs AE **2.3.1 with game 1.7.104**, GOG AE **2.2.6 with 1.6.1179**, older SE **2.0.20 with 1.5.97**, and VR **2.0.12 with 1.4.15**. Record executable version, storefront and each native plugin's supported runtime, not just the label “SE” or “AE”. Do not upgrade an installation based on these labels alone.
* [PyNifly's latest-release redirect](https://github.com/BadDogSkyrim/PyNifly/releases/latest) resolved to [V30.3.0](https://github.com/BadDogSkyrim/PyNifly/releases/tag/V30.3.0), titled HKX animations. The August 28.0.0 entry is not a current-version recommendation. [Animation instructions](https://github.com/BadDogSkyrim/PyNifly/blob/main/ANIMATIONS.md) still require the actual game skeleton for HKX work. Latest is a candidate, not proof of compatibility with the chosen Blender, rig or existing export chain.
* [libloot](https://github.com/loot/libloot) is a Rust library with C++, Python and Node wrapper projects. Evaluate the maintained upstream before writing a sorter. This is not evidence that replacing an existing implementation improves a particular project.
* Nexus [discontinued the Nexus Mods App in favor of Vortex](https://help.nexusmods.com/article/164-discontinuing-the-nexus-mods-app-faq). Do not confuse that app with the maintained Vortex integration surface.

## Primary-source tool and license screening

License labels are initial source-level screening, not legal clearance for a packaged product. Pin the exact release/commit and inspect its license, exceptions, dependency notices and asset permissions before embedding or redistribution. An external process boundary does not automatically eliminate license obligations. Mods, SDKs and game assets have rights separate from tool code. Unknown means **not cleared**, not public domain.

| Tool / primary source | Role and reuse boundary to investigate | License signal / important gate |
|---|---|---|
| [Creation Kit SE](https://store.steampowered.com/app/1946180/Skyrim_Special_Edition_Creation_Kit/) | Installed Bethesda editor for world/quest/record authoring; launch rather than bundle | Proprietary terms; no acceptance or executable/asset redistribution here |
| [xEdit / SSEEdit](https://github.com/TES5Edit/TES5Edit) | Record inspection, conflict reports, scripted patching; preserve source masters and generate separate patches | Current [source LICENSE](https://github.com/TES5Edit/TES5Edit/blob/dev-4.1.6/LICENSE.txt) is MPL-2.0; older website license summaries can disagree |
| [Mutagen](https://github.com/Mutagen-Modding/Mutagen) | Typed .NET reading/writing of Bethesda plugins | GPL-3.0 source; round-trip unknown records, FormIDs, masters and localized strings before adoption |
| [Synthesis](https://github.com/Mutagen-Modding/Synthesis) | Existing patcher pipeline instead of a bespoke patch runner | GPL-3.0; individual patchers have separate licenses; pin versions and order |
| [Spriggit](https://github.com/Mutagen-Modding/Spriggit) | Plugin/text conversion for reviewable version control | GPL-3.0; test semantic round-trip, not merely successful serialization |
| [Mod Organizer 2](https://github.com/ModOrganizer2/modorganizer) | Profile, VFS and plugin integration; preserve existing manager semantics | GPL-3.0 repository; components have their own licenses; test under actual VFS |
| [LOOT](https://github.com/loot/loot) | Sorting, dependency warnings and metadata-driven advice | GPL-3.0; retain masterlist revision and user rules; sorting does not solve all conflicts |
| [libloot](https://github.com/loot/libloot) | Supported library/wrapper candidate for diagnostic and sorting adapter | GPL-3.0; exact wrapper/platform and target workload acceptance required |
| [Wrye Bash](https://github.com/wrye-bash/wrye-bash) | Bashed Patch and specialist management functions | [Official documentation](https://wrye-bash.github.io/docs/Wrye%20Bash%20General%20Readme.html) specifies GPL-3.0-or-later; do not assume every conflict is mergeable |
| [Vortex](https://github.com/Nexus-Mods/Vortex) | Extension API and existing deployment workflow | GPL-3.0; do not mix deployment state with another manager |
| [Wabbajack](https://github.com/wabbajack-tools/wabbajack) | Reproducible modlist acquisition and installation | GPL-3.0 code; download permissions, access restrictions and mod redistribution rights remain separate |
| [BodySlide / Outfit Studio](https://github.com/ousnius/BodySlide-and-Outfit-Studio) | Body/outfit authoring and generated mesh output | [GPL-3.0](https://github.com/ousnius/BodySlide-and-Outfit-Studio/blob/dev/LICENSE); meshes/presets retain authors' rights |
| [nifly](https://github.com/ousnius/nifly) | Existing C++ NIF representation and conversion candidate | GPL-3.0; test format variants, skinning and material preservation |
| [PyNifly](https://github.com/BadDogSkyrim/PyNifly) | Blender NIF/HKX import/export workflow | GPL-3.0 source; exact Blender/tool/skeleton tuple must be validated |
| [NifSkope](https://github.com/niftools/nifskope) | Interactive NIF inspection and diagnosis | Selected build/fork license and release lineage still require verification; not cleared for bundling |
| [Cathedral Assets Optimizer](https://github.com/Guekka/Cathedral-Assets-Optimizer) | Asset/archive conversion candidate, staged copies only | MPL-2.0 source signal; repository explicitly describes in-development experimental work and potentially outdated docs, not a production default |
| [MMD Tools](https://github.com/MMD-Blender/blender_mmd_tools) | Existing VMD/MMD import stage in this repository's workflow | Selected release license and Blender compatibility need a pinned follow-up; August compatibility range is not revalidated here |
| [Caprica](https://github.com/Orvid/Caprica) | Papyrus compiler candidate | MIT; compare dialect, compiler flags and import definitions against reference output |
| [Champollion](https://github.com/Orvid/Champollion) | PEX inspection/decompilation when authorized | LGPL-3.0 source; recovered text is not original source, and scripts retain their own rights |
| [SKSE](https://skse.silverlock.org/) | Runtime extension prerequisite, detect installed version before launch | Review exact package terms separately; native DLL compatibility is per runtime/storefront |
| [Open Animation Replacer](https://github.com/ersh1/OpenAnimationReplacer) | Runtime conditional animation replacement | GPL-3.0-or-later with [Modding and GPL linking exceptions](https://github.com/ersh1/OpenAnimationReplacer/blob/main/EXCEPTIONS); preserve exact exception terms |
| [Pandora Behaviour Engine Plus](https://github.com/Monitor221hz/Pandora-Behaviour-Engine-Plus) | Behavior generation/patching with isolated output | GPL-3.0 family; preserve source header terms; do not mix generated engine outputs blindly |
| [FallrimTools / ReSaver](https://github.com/mdfairch/FallrimTools) | Save inspection and narrowly justified repair on copies | Apache-2.0 source, mixed dependency licenses; no universal automated save-cleaning policy |
| [Crash Logger SSE AE VR](https://github.com/alandtse/CrashLoggerSSE) | Runtime-matched crash evidence, not automatic causal diagnosis | Selected distribution license still needs verification; redact private paths/account data before sharing logs |

## Proposed integration design, not an adopted replacement

1. **Read-only inventory first.** Capture executable/storefront, manager/profile identity, enabled plugins, master dependencies, native DLL versions, archive/loose-file precedence and input hashes. Missing information is an explicit unknown, never “healthy”. Separate asset conflicts from record conflicts and runtime incompatibility.
2. **Adapters around maintained upstreams.** Start with supported APIs/CLI or explicit external-tool handoffs. Capture selected executable identity, version, arguments, exit status and structured/raw diagnostics. Do not scrape restricted services, export browser tokens or treat a website session as an API grant. No automatic update/download executable execution.
3. **Transactional outputs.** Generate patches, meshes, behavior and sorted-order proposals in an isolated output mod. Keep input snapshots, original save plus cosave, hashes and rollback metadata. Preview changed records/files. Never edit original masters or overwrite the only backup. Cancel/failure must leave the active profile unchanged.
4. **Evidence before promotion.** Compare the candidate against the project's current path under the same fixture/runtime and requirements. License compatibility, correctness, deterministic output, performance and recovery all gate adoption. A fast microbenchmark cannot replace manager, authoring or in-game acceptance.

### Acceptance matrix for an eventual implementation

| Scenario | Required evidence before calling it complete |
|---|---|
| Plugin creation/patching | Masters/FormIDs/localized data/unknown records preserved; independent xEdit inspection; clean plugin load; intentional changes only |
| Sort/manager adapter | Missing master/cycle/user-rule fixtures; dry-run diff; actual profile/VFS launch; no hidden deployment or selection changes |
| Mesh conversion | Skeleton/skinning/material/texture checks; round-trip on representative assets; in-game visuals; originals intact |
| VMD → HKX | Evaluated bake, frame rate/length, skeleton bone order, annotations and root motion; fresh-scene round-trip and native runtime acceptance |
| Behavior/OAR deployment | Exact runtime/plugin versions; reproducible generated files isolated; actual condition/transition playback, not simply a loaded DLL |
| Save diagnosis/repair | Non-mutating inspection; copy plus cosave; precise preview; failure rollback; successful game load/save/reload with expected quest state |
| Batch/stress | Corrupt/truncated/missing input, permission denial, cancellation, disk-full and interrupted write; retained failures and last-good outputs |

## Next research and acceptance gates

* Pin exact upstream commits/releases and complete unresolved license/dependency reviews before packaging. Branch URLs above are mutable research citations, not a reproducible software lockfile.
* Revalidate Blender/MMD/PyNifly compatibility as a complete tuple. Do not relabel the historical August catalog as current or claim the canonical Sheet has been refreshed.
* Build a small author-owned/permitted fixture set and run the existing animation milestone's round-trip/native gates. No private/paywalled assets or personal saves belong in this public repository.
* Evaluate manager-facing diagnostics in the existing application rather than invent another manager. Keep all proposals here until target-project evidence justifies adoption.

**Outcome of this pass:** a source-linked integration and license map, two concrete version/compatibility updates, and explicit test gates. No claim of implemented integrations, repaired user saves, benchmark superiority or in-game acceptance.

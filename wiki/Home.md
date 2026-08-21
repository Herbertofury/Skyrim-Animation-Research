# Skyrim Animation Research Wiki

Current snapshot: **2026-08-21** — **75 tools/resources**, **69 verified source-ledger entries**, **20 troubleshooting cases**.

This directory is the repository-backed mirror of the wiki content. The research is organized into:

- [Modern Workflow](Modern-Workflow.md)
- [Tool Catalog](Tool-Catalog.md)
- [Troubleshooting](Troubleshooting.md)
- [Legacy Migration](Legacy-Migration.md)
- [Latest Rescan — 2026-08-21](Latest-Rescan-2026-08-21.md)
- [Source Ledger](Source-Ledger.md)

## Current recommended path

**VMD/MMD → source diagnostics → MMD Tools / trusted MMD evaluation → evaluated retarget → actual Skyrim `skeleton.hkx` → per-frame target bake → PyNifly/modern HKX export → HKX/annotation QA → OAR deployment.**

Use Pandora only when behavior generation is genuinely required. Use AMR or another intentional runtime mechanism when the actor must physically travel through the world; visible pelvis/root translation alone is not equivalent to world displacement.

Live sortable research database:
https://docs.google.com/spreadsheets/d/1MUrse5aUj5M0rMvXXrrnfWCtp66WWrjiwWxo1fFaHHY/edit

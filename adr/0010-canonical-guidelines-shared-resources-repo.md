# ADR-0010: Canonical guidelines / shared-resources repo (ALFA+OMEGA)

**Status:** Accepted
**Date:** 2026-07-22

## Context

The four guideline docs existed as three byte-identical but **unlinked** copies (ALFA+OMEGA, `LEDGER/guidelines/`, `AI-LAB/docs/guidelines/`) with no sync mechanism — identical today, guaranteed to drift the moment one is edited, and the "canonical" ALFA+OMEGA copy was itself unversioned (no git). The 2026-07-22 audit flagged this as a hygiene risk. David has since made **ALFA+OMEGA a git repo** and framed it as the source-of-truth hub for **all** reusable cross-project resources — guidelines now, and `artifacts/`, `skillsets/`, `licenses/`, scripts as future sibling folders — with a hard rule that guideline docs stay universal (no project-specific content), distributed by copying `guidelines/` into each project.

## Decision

ALFA+OMEGA (git, remote configured) is the **single canonical home** for shared guidelines and reusable admin/maintenance resources. The Ledger scan engine, the `ledger` skillset, and the dashboard generator will live here too and be consumed by Ledger.

**Versioning** is by git tags (`guidelines-v1.0`, etc.) plus a one-line **version stamp inside each doc**, so a copy dropped into a project self-identifies its version; `guidelines/` always holds the latest. Physical `v1/`/`v2/` directories are **not** used — redundant with git history for a copy-distribution model.

**Ledger's own `guidelines/*.md` are superseded** — replaced with pointer stubs naming the canonical source and version, **not deleted**, so existing path references in `SPEC.md`, `README.md`, the `ledger` skill, and ADRs still resolve.

Because distribution is by copy, **`ledger scan` compares each project's copied guideline version-stamp against canonical** and flags staleness (e.g. "guidelines v1 vs canonical v2") as amber.

## Consequences

One editable source of truth; the three-copy drift risk is closed and turned into a *detectable* signal for project copies. Ledger now depends on an external repo for canonical guidelines — acceptable, since both are David's and both are under git. Cost: a stamping convention to maintain. Partly realized already (repo stood up 2026-07-22); remaining work: tag `guidelines-v1.0` + add version stamps, write the pointer stubs (Phase 0), and add the scan drift-check (Phase 1).

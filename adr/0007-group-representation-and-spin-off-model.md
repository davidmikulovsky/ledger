# ADR-0007: Group representation and spin-off model

**Status:** Accepted
**Date:** 2026-07-22

## Context

Egraine Oy is a parent entity (Nordic distributor) with ventures — Medex Beauty Clinic and THANN — that on disk are independent sibling repos, each with its own git, docs, and decision log, with the child projects referencing the parent read-only. Ledger v0.5 modeled them as nested `sub_units:` under the Egraine unit (`business/egraine/ventures/*`). The 2026-07-22 framework audit found this diverged from disk (the THANN child's real repo at `PROJECTS/Thann` wasn't even referenced by its unit) and — more decisively — David confirmed ventures may be **sold or spun out**: Medex or THANN could become separate from Egraine. Containment-by-nesting fights both the filesystem and the divestiture requirement.

## Decision

Represent the parent→child relationship as a **link, not containment**.

- Each venture is its own top-level unit (e.g. `business/thann`, `business/medex`) with its own `source:` pointing at its real repo, carrying `parent: business/egraine` and optionally `relationship:` (e.g. `distributed-brand`).
- The parent unit carries `portfolio_members:` listing its ventures — a rollup view, not ownership of their files.
- `sub_units:` nesting is retired.
- **Spin-off** = drop the `parent:` link (and remove from `portfolio_members:`); the venture's own repo, history, and ledger are untouched.
- The dashboard groups by `parent`, so the Egraine group still displays together.

## Consequences

The model matches disk (killing the source-mismatch bug class the audit found) and makes divestiture a one-line edit instead of file surgery. The `components:` schema stays one-repo-per-unit, which now fits because each venture is its own unit. Supersedes the `sub_units:` convention from v0.1; historical ledger entries mentioning nesting stay unedited per the append-only principle. Cost: the currently-nested THANN and Medex units must be promoted to top-level and their references updated — done as the Phase 2 data-reconciliation, not here.

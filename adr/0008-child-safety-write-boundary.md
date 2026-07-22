# ADR-0008: Child-safety write boundary between projects

**Status:** Accepted
**Date:** 2026-07-22

## Context

ADR-0001 stops Ledger writing to a tracked project's source. It does not govern one project's session writing into **another** project — specifically a child/venture session reaching up into its parent or across into a sibling. The 2026-07-22 audit found this risk is real and has already materialized once: Egraine's own `STRUCTURE-README.md` documents a cleanup pass that deleted 48 files (~19 MB) and left the git working tree "deleted, but not committed," safe only because a backup existed. THANN's `CLAUDE.md` already tells sessions to treat `../Egraine` as read-only reference — but that is one project's own prose, not a framework guarantee.

## Decision

A session working inside a child or sibling project treats **parent and sibling folders as read-only** — it may read, summarize, and cite them, but never write, move, or delete in them.

Any **destructive operation inside any project** — bulk delete, `git rm`, folder moves or renames, history rewrites — requires the owner's explicit go-ahead **and a verified backup first**, never as a side effect of another task.

This is the mirror of ADR-0001, applied between projects rather than only between Ledger and projects.

## Consequences

The accidental-deletion class is closed structurally, not by remembering to be careful. Cross-brand facts still flow (read + cite), so nothing legitimate is blocked — a child that genuinely needs a change in its parent raises it as an explicit, owner-approved task in the parent, the same deliberate-separate-action discipline ADR-0001 already establishes. Enforcement is by convention today; `ledger scan` / the child project's own `CLAUDE.md` are where this gets reinforced per project.

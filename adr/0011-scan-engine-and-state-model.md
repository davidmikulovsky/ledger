# ADR-0011: Scan engine and state model

**Status:** Accepted
**Date:** 2026-07-22

## Context

The 2026-07-22 audit's core finding was that drift accumulates because every tracking step is manual and nothing surfaces unknown gaps: a unit's declared state is never automatically re-checked against its real source, and on-disk projects can go untracked unseen. The v0.6 plan resolves this with a single machine-readable snapshot that every downstream feature reads.

## Decision

A **scan engine** (`ledger scan`, run on the owner's machine where the repos live) reads every unit's front-matter plus a live read of each project's real folder and git (last commit, ahead/behind, dirty tree, lock files, README/changelog/decision-log presence and freshness) and writes one file, **`ledger-state.json`**.

Per unit it records: declared status/priority/urgency, source, git + doc facts, a `movement` classification (`moving | stalling | blocked | dormant | ended`), a `health` colour (`green | amber | red | grey`) by defined rules, and a `flags[]` list; plus portfolio-level flags (untracked on disk, no-git, etc.).

Rules: **red** = a hard violation or declared-vs-reality contradiction (git missing on an active unit, drift, wrong/missing source, live lock, unresolved `disputed`); **amber** = a soft/stale gap (stale changelog/README, stale `verified:`, uncommitted changes, stale copied guidelines); **green** = conforms and recently verified; **grey** = dormant/ended. **`movement: stalling`** (status `active` but no activity within the active window, default 14 days) is the silent-death detector.

The engine only **reads** projects and **writes** `ledger-state.json` + Ledger's own unit files — ADR-0001 holds. Every other v0.6 skill (`audit`, `gaps`, `check`, `doctor`, `report since:`, `dashboard`) is a reader of this snapshot.

## Consequences

One spine, many thin readers — gaps announce themselves instead of needing a manual audit, and the state model doubles as the data contract the dashboard and future automation read. Cost: the scan must run on the owner's machine (git is local, not in the cloud), and scheduled/automated runs depend on the desktop bridge being connected — the plan degrades gracefully around this.

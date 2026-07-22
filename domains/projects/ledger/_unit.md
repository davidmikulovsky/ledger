---
domain: projects
unit: ledger
type: maintenance
status: active
priority: medium
urgency: medium
started: 2026-07-14
last_updated: 2026-07-22 (v0.5 — ledger admin/reporting skill designed, ADR-0006)
source:
  - "this folder (self-referential — tracks itself as a unit too)"
---

# Ledger (this framework, tracking itself)

Renamed 2026-07-21 from "life-os" to "Ledger" — dropping the "life tracking" framing in favor of a project-tracking framing that doesn't presuppose scope. Folder renamed `domains/projects/life-os` → `domains/projects/ledger` in the same commit. Old name kept in historical ledger entries and other units' ledgers unedited, per the append-only principle — this is a forward-facing rename, not a rewrite of history.

The tracking framework itself, treated as a project with its own progress worth tracking — same pattern as everything else in here, applied reflexively. This unit gives its own backlog (mostly infrastructure work, not content) a place in the index so it doesn't get lost among the domains it tracks.

## Built so far

- Core structure: `domains/<domain>/<unit>/_unit.md` + `ledger.md` pattern, front-matter schema (type/status/priority/source), root `_index.md` rollup.
- Domains scaffolded: business, projects (populated); health, sport, nutrition, relationships, career (empty, ready).
- Seed content: Egraine (parent + 4 sub-ventures, corrected against real source docs — decision log, strategic plan), Jascandi.
- **ADR log established (2026-07-21)** at `adr/` — governance decisions about the framework itself, separate from per-project ledgers. ADR-0001 (read-only boundary on tracked projects — hard rule, see below) and ADR-0002 (local-only storage/hosting) in place.
- **Storage migrated 2026-07-21**: pen drive → persistent local SSD (`/Users/mklvsky/AI/LIFE_OS`). Verified via `git log` diff that all 5 prior commits are byte-identical between old and new location — nothing lost. Pen drive is still connected/available and now serves as an incidental second copy, not the primary.

## Hard rule, now enforced (ADR-0001)

This framework never writes, edits, or otherwise modifies any file in a tracked project's own source location — only reads it. Corrections apply only to this framework's own files. Verified retroactively that this was already true in practice for every past correction (e.g. the Egraine rebuild) before being made an explicit rule. See `adr/0001-read-only-boundary-on-tracked-projects.md` for the full record.

## Versioning (from v0.2)

Ledger now tracks its own version in `CHANGELOG.md`, same standard it asks of tracked projects (see `SPEC.md`, applying `guidelines/project-standard.md` to itself). Current: **v0.5**. v0.1 applied retroactively to everything before the guideline system existed.

## v0.5 (2026-07-22) — reporting/admin skill designed

Prompted by the second ad hoc "where are we on THANN" conversation — the case `ROADMAP.md`'s "Reporting skills" section had been waiting for since v0.2. David asked for a repeatable, scalable way to pull project status at different depths, framed as a slash-command-style skill, and explicitly delegated the mechanism to Claude rather than prescribing it. Two candidate phrasings of that request were reviewed first: David's own conversational ask (kept — correct division of labor, delegates implementation while stating real requirements) versus a pre-written "spec" that invented a training/knowledge-graph implementation with no bearing on how a Claude skill or this framework actually work (rejected).

Designed: one skill, `ledger`, with a verb grammar (`report | sync | log | new | portfolio | audit`) instead of one skill per capability, so the trigger surface stays simple and extensible. `report` gets a four-tier depth ladder — `glance` (front-matter only; renamed from an earlier `pulse`, flagged as misleading), `brief` (default; adds recent ledger entries + next-step line), `full` (adds live re-verification against `guidelines/project-standard.md`, claimed-vs-verified labeling), `audit` (adds a principles-compliance pass). Project names resolve against `_index.md` before any verb acts; every report closes with a `last verified: <date> · depth: <x>` footer. ADR-0001's read-only boundary carries over unconditionally to every verb that touches a tracked project's real source. Recorded as ADR-0006.

Not yet done: packaging as an installable `.skill` file, end-to-end testing. Logic testing against THANN (which is already a tracked unit, `business/egraine/ventures/thann`) is next.

## v0.4 (2026-07-21) — domain restructure, vocabulary v2

David asked for two changes on review. First: nest the personal-life domains (career, health, nutrition, relationships, sport) under a new top-level `personal` domain, alongside `business` and `projects` — the flat list of seven domains was starting to blur "areas of a life" with "areas of work." Second, and larger: he questioned whether the v0.3 vocabulary was actually as clean as it claimed. `dormant` and `paused` were too similar to justify separately; same for `done` and `ended`; `disputed` wasn't clearly a status at all, more like a flag about the record itself; `critical` didn't reflect how priority is actually used ("we only recognize 3 levels"); and — the sharpest point — priority alone can't express "urgent but low priority" vs. "urgent and high priority," which are genuinely different situations, or the reverse case of a high-priority item that can still wait (a visual refactor was his example).

Resolved: `status` collapsed to `active | blocked | dormant | ended` (paused folded into dormant, done folded into ended — the success-or-not nuance moves to ledger prose instead of a dedicated value). `priority` collapsed to `high | medium | low` (critical dropped, optional folded into low). `disputed` pulled out of the status enum entirely, now an independent optional flag. New `urgency` field added as a third independent axis (`high | medium | low`), explicitly separate from priority — an Eisenhower-style importance-vs-time-sensitivity split. Applied across `guidelines/project-standard.md`, `workflow.md`, `checklists.md`, `SPEC.md`'s schema table, `README.md`, and every existing unit (SkinThea's `optional` → `low`; urgency added everywhere, each value flagged as Ledger's proposed read pending David's confirmation, same pattern used for priority in v0.3). Recorded as ADR-0005.

## Guideline system — done (2026-07-21, ADR-0003), extended same day (ADR-0004)

Four documents at `guidelines/`: `project-standard.md` (what a tracked project should contain — git as the one hard requirement, plus the canonical `status`/`priority` vocabulary, added v0.3), `tracking-protocol.md` (how Ledger checks a project, including the claimed-vs-verified discipline learned directly from the Jascandi live-fetch check, and a structured `components` schema in `_unit.md`), `workflow.md` (Start → Work → Check → Update → End/New-Version loop, mapped to the existing `type` field, offered as adaptable not mandatory), `checklists.md` (the loop as concrete checkboxes, added v0.3). Piloted `components` on Jascandi immediately using data already verified the same day, rather than leaving it theoretical.

**v0.3, same day:** David reviewed the above and pushed back on two things, both fixed. First, `status` and `priority` were being conflated — Jascandi's invented `dormant-capable` was really trying to say two things at once ("real work is happening" and "no business stakes behind it"). Split into two independent canonical enumerations, explicitly designed to support future visualization by either axis. Second, the three guideline documents named Jascandi and David directly, which meant they couldn't be lifted out and reused to drive a different tracking effort — rewritten generic, portable, principles-first. See ADR-0004.

## Open backlog for the framework itself

- **Rebrand — done (2026-07-21):** now "Ledger." Applied to README.md, `_index.md`, and this unit (renamed from `life-os`).
- **Hosting — decided 2026-07-21 (ADR-0002), supersedes the 2026-07-15 GitHub-private plan:** local git only, on persistent storage, no remote. Revisit if an off-device backup need becomes real.
  - Note: the earlier "turn Medex/Egraine's docs folders into git repos, push to GitHub" plan is now in tension with ADR-0001 if read literally — doing that *as part of this framework's operation* would mean this framework modifying those projects' own folders. Treat any future work like that as a separate, explicit, user-directed task on that project — not something this framework initiates on its own.
- `_index.md` regeneration is currently manual (I rewrite it by hand when asked) — flagged earlier as a later automation step once the unit count grows. Still true, still deferred.
- No domains outside business/projects have any units yet — health, sport, nutrition, relationships, career are all empty. Not a problem, just the honest state: this framework is currently exercised on one life area (business) and one hobby project, not yet on the personal-life domains it was originally designed for.

## Why this unit exists

So "what's left to build in the tracking system itself" has the same clear answer as any other domain, rather than living only in chat history.

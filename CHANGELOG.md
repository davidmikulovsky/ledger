# Ledger — Changelog

*Plain-language version history of Ledger itself — what changed and when, not why (that's `adr/`) and not what's happening in tracked projects (that's each unit's own `ledger.md`). Newest first.*

## v0.5 — 2026-07-22

Reporting/admin skill designed: a single `ledger` skill rather than one per capability, invoked with a verb grammar (`report | sync | log | new | portfolio | audit`) and, for `report`, a four-tier depth ladder (`glance | brief | full | audit`) running from a one-line status check up to a full principles-compliance audit. Project-name resolution against `_index.md` and a `last verified: <date> · depth: <x>` footer on every report make the claimed-vs-verified discipline visible in the output itself. Answers the "Short reports, single or multi-project" item on `ROADMAP.md`.

Recorded as ADR-0006. Design only — not yet packaged as an installable skill, not yet tested end-to-end.

## v0.4 — 2026-07-21

Domain structure changed: `career`, `health`, `nutrition`, `relationships`, `sport` nested under a new top-level `personal` domain — top level is now `business` / `personal` / `projects` instead of seven flat domains.

Vocabulary redesigned after review. `status` collapsed from 7 values to 4: `active | blocked | dormant | ended`. `paused` merged into `dormant` (both meant "not moving right now, not closed" — the distinction wasn't earning its keep). `done` merged into `ended` (whether a thing reached its goal or was discontinued is now a line in the ledger entry, not a separate status value). `disputed` removed from the status enum entirely and reintroduced as an independent optional flag (`disputed: true`), since it answers a different question ("is the record itself trustworthy") that's orthogonal to lifecycle state.

`priority` collapsed from 5 values to 3: `high | medium | low`. `critical` dropped — "we only recognize 3 levels." `optional` folded into `low`, which already covers "real but limited stakes, not scheduled."

New `urgency` field added as a third independent axis, `high | medium | low`, distinct from priority: priority is "how much does this matter," urgency is "how soon does it need attention." An Eisenhower-style split, added because priority alone couldn't express that "urgent but low priority" and "urgent and high priority" are different situations, or that a high-priority item (e.g. a visual refactor) can still be low urgency.

Applied across `guidelines/project-standard.md`, `workflow.md`, `checklists.md`, `SPEC.md`'s schema table, `README.md`, and every existing unit — `urgency` added to each with a proposed value flagged for review, same pattern used for `priority` in v0.3.

Recorded as ADR-0005.

## v0.3 — 2026-07-21

Canonical `status` and `priority` vocabularies defined in `guidelines/project-standard.md`, as two deliberately independent axes: `priority` (real-world stakes — critical/high/medium/low/optional) answers "how much does this matter," `status` (active/paused/blocked/dormant/done/ended/disputed) answers "what's happening right now." Designed explicitly to support future visualization by either axis (see `ROADMAP.md`). Two units' invented, non-canonical status values corrected: Jascandi's `dormant-capable` → `active` (priority stays `low` — active and low-priority isn't a contradiction, it's a hobby project with no real business stakes, exactly the case that prompted this change) and SkinThea's `hibernated` → `dormant` (same meaning, standard term).

`guidelines/project-standard.md`, `tracking-protocol.md`, and `workflow.md` rewritten to be usable outside Ledger's own scope — stripped of Ledger/David-specific references, kept generic ("a tracker," "the project owner") so the same principles could drive a different tracking system entirely. Ledger-specific application of these principles stays where specificity belongs: `SPEC.md`, unit files, this changelog.

New `guidelines/checklists.md` — the workflow loop as concrete, checkable steps per stage (Start, Work, Check, Update, End/New-Version), so a step being skipped is a choice, not an accident.

Recorded as ADR-0004.

## v0.2 — 2026-07-21

Guideline system added: `guidelines/project-standard.md` (what a tracked project should look like — git as a hard requirement, README/docs/changelog expectations, missing pieces framed as normal), `guidelines/tracking-protocol.md` (how Ledger checks a project against that standard, including the claimed-vs-verified discipline and the `components` data structure), and `guidelines/workflow.md` (the Start → Work → Check → Update → End/New-Version loop, as an adaptable recommendation, not a mandate).

Ledger applied the same standard to itself for the first time: this file, `SPEC.md` (full specification), and `ROADMAP.md` (future directions — report-generating skills, live feeds, notifications) all added.

The `components` structured data block added to the `_unit.md` schema — a per-project, at-a-glance record of git/docs/changelog/live-artifact status, each entry carrying a verification date and method. Piloted on Jascandi using data already gathered the same day.

Recorded as ADR-0003.

## v0.1 — 2026-07-14 through 2026-07-21 (retroactively summarized)

Initial build: the `domains/<domain>/<unit>/_unit.md` + `ledger.md` pattern, front-matter schema, root `_index.md` rollup. Seeded with Egraine (parent + four ventures) and Jascandi. Hosting decided (local git, no remote) and later reconsidered in light of a real risk analysis (Coolify's own CVE history, GitHub private as the better fit for now). Framework migrated from a pen drive to persistent local storage, verified byte-identical via git history. ADR log established, starting with the read-only boundary rule (ADR-0001) and the storage decision (ADR-0002). Renamed from "life-os" to "Ledger," dropping the life-tracking framing for a scope-agnostic one. A multi-location git audit across pen drive, SSD, and Documents surfaced real discrepancies (diverged commits, an orphan repo, three previously-untracked projects) and confirmed Ledger's read-only stance by design — it reported, David resolved.

No formal version numbers existed during this period; v0.1 is applied retroactively to mark "the framework existed and worked" as a baseline before the guideline system in v0.2.

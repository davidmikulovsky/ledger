# Ledger — Changelog

*Plain-language version history of Ledger itself — what changed and when, not why (that's `adr/`) and not what's happening in tracked projects (that's each unit's own `ledger.md`). Newest first.*

## v0.2 — 2026-07-21

Guideline system added: `guidelines/project-standard.md` (what a tracked project should look like — git as a hard requirement, README/docs/changelog expectations, missing pieces framed as normal), `guidelines/tracking-protocol.md` (how Ledger checks a project against that standard, including the claimed-vs-verified discipline and the `components` data structure), and `guidelines/workflow.md` (the Start → Work → Check → Update → End/New-Version loop, as an adaptable recommendation, not a mandate).

Ledger applied the same standard to itself for the first time: this file, `SPEC.md` (full specification), and `ROADMAP.md` (future directions — report-generating skills, live feeds, notifications) all added.

The `components` structured data block added to the `_unit.md` schema — a per-project, at-a-glance record of git/docs/changelog/live-artifact status, each entry carrying a verification date and method. Piloted on Jascandi using data already gathered the same day.

Recorded as ADR-0003.

## v0.1 — 2026-07-14 through 2026-07-21 (retroactively summarized)

Initial build: the `domains/<domain>/<unit>/_unit.md` + `ledger.md` pattern, front-matter schema, root `_index.md` rollup. Seeded with Egraine (parent + four ventures) and Jascandi. Hosting decided (local git, no remote) and later reconsidered in light of a real risk analysis (Coolify's own CVE history, GitHub private as the better fit for now). Framework migrated from a pen drive to persistent local storage, verified byte-identical via git history. ADR log established, starting with the read-only boundary rule (ADR-0001) and the storage decision (ADR-0002). Renamed from "life-os" to "Ledger," dropping the life-tracking framing for a scope-agnostic one. A multi-location git audit across pen drive, SSD, and Documents surfaced real discrepancies (diverged commits, an orphan repo, three previously-untracked projects) and confirmed Ledger's read-only stance by design — it reported, David resolved.

No formal version numbers existed during this period; v0.1 is applied retroactively to mark "the framework existed and worked" as a baseline before the guideline system in v0.2.

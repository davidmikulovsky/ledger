# Ledger — Changelog

*Plain-language version history of Ledger itself — what changed and when, not why (that's `adr/`) and not what's happening in tracked projects (that's each unit's own `ledger.md`). Newest first.*

## v0.7.3 — 2026-07-23

ADR-0012 rollout closed out, per David's explicit go-ahead on all four open items from the v0.7.2 entry:

1. **Eden's Eva and SkinThea converted to the `mentions:` tier.** Neither ever had real folder or repo activity — both existed only as Egraine Decision Log entries — so their standalone `_unit.md`/`ledger.md` files are retired. They now live as two lines in `egraine/_unit.md`'s new `mentions:` field, with full history preserved (not deleted — the device bridge can move but not delete) at `LEDGER/_to_delete/eden-eva_unit.md`, `eden-eva_ledger.md`, `skinthea_unit.md`, `skinthea_ledger.md`. David can clear that folder natively whenever convenient. Nothing about either venture's real-world status changed.
2. **Promotion of Thann/Medex to flat top-level units — analyzed, not applied.** A consequences write-up was added to `egraine/_unit.md` ("Promoting Thann/Medex — consequences"): the move is mechanically low-risk (Ledger's own files only) but functionally inert today, since `ledger.py`'s `load_units()` already walks the entire `domains/` tree regardless of nesting depth. The real tradeoff is timing — promote now calmly, or later under the pressure of an actual spin-off. Left open for David.
3. **Guideline copies inside tracked projects' own repos — declined.** David: "forbidden." No write made to Egraine/Thann/Medex's own repos. The `GUIDELINES-STALE` drift check accordingly still can't fire for any of them — a known, accepted limitation, not a bug.
4. **ALFA+OMEGA guidelines-v2.1 committed and tagged.** Commit `48e9697` on `main` (7 files: `CHANGELOG.md`, all 5 guideline docs, `ledger.py`), tag `guidelines-v2.1` — David to push.

Also shipped this cycle: the two `ledger.py` checks proposed in v0.7.2 (`MEMBER-MISMATCH`, `ORPHAN-PARENT`) — implemented in `build_state()`, applied to the real ALFA+OMEGA repo, syntax-checked, and smoke-tested against the actual Egraine family data (`ledger.py scan`): 7 units scanned cleanly post-conversion (down from 9), zero false positives from either new check. A stray `.git/index.lock`/`HEAD.lock`/`objects/maintenance.lock` picked up mid-session during this work was moved to `ALFA+OMEGA/_to_delete/` per the standard lock-handling runbook, not left in place.

Every write this entry describes was verified directly against the live device (`md5sum` for file content, `git log`/`git status` for the commit/tag), not assumed from a local draft.

## v0.7.2 — 2026-07-23

ADR-0012 accepted: family schema & delivery mechanism. Closes a real gap the uploaded proposal doc (from David's separate Cowork session in the Egraine repo) surfaced — ADR-0007's link-not-nesting decision for group/family projects existed only in `adr/`, which no tracked project's own docs ever reference, and the field names it proposed (`portfolio_members`) never matched what `ledger.py`'s own code already reads (`parent`). David's framing: this is a communication/delivery problem, not a structural one — no physical restructuring was done or proposed as part of this.

Fixed by: (1) locking canonical field names in ADR-0012 (`role`, `parent`, `relationship`, `members` for real family members; a new `mentions:` list for related-but-not-tracked entities with no real folder — the "children's children / orphans" case); (2) delivering the schema through `project-standard.md` and `tracking-protocol.md` — the docs actually copied into tracked projects, not just the ADR log; (3) adding a "Folder and naming conventions" section to `project-standard.md`; (4) bumping the ALFA+OMEGA guidelines stamp v2.0→v2.1 (content-only bumps are invisible to the `GUIDELINES-STALE` check — this one is real and detectable).

Applied this cycle: `parent_unit:`/`sub_units:` renamed to `role:`/`parent:`/`members:` (plus `relationship: distributed-brand` for Thann/Medex, per ADR-0007's own language) across all 5 Egraine-family unit files (`egraine`, `thann`, `medex-beauty-clinic`, `eden-eva`, `skinthea`). Field-name fix only — no folder moves, no change to what any of these units actually are. Every write verified directly against the live device via `md5sum`, not the file-staging cache, per the lesson from the earlier v0.7.1 false-alarm entry.

Not applied, left for David: converting Eden's Eva/SkinThea to the new `mentions:` tier; physically promoting Thann/Medex to flat top-level units; placing an actual guidelines copy inside Egraine/Thann/Medex's own repos (a write to a tracked project); running `git commit`/`git tag guidelines-v2.1` in ALFA+OMEGA; the two proposed new `ledger.py` flags (`MEMBER-MISMATCH`, `ORPHAN-PARENT`) — presented as a diff, not coded.

## v0.7.1 — 2026-07-23

**Correction, same session:** an earlier version of this entry reported that today's Egraine audit writes and Thann's 07-22 fix had silently reverted mid-session, and speculated a concurrent-session write conflict. That was a false alarm on this tool's own part — a stale local read cache in the Cowork session's file-staging pipeline was serving pre-fix content back after the real writes had already succeeded, not a real revert on disk. Verified directly against the actual files (md5sum via a live shell on the device, not the cached staging path): every write this session — Thann's fix, Egraine's full audit, this changelog, the index — matched exactly what was intended, the whole time. No data was ever lost or overwritten. Retracting the earlier speculation about a concurrent-session conflict; nothing about David's separate Cowork session in the Egraine repo was at fault.

## v0.7 — 2026-07-22

Phase 1 (scan engine + gap verbs — `scan`/`audit`/`gaps`/`check`/`doctor`, `ledger-state.json` as the shared spine) and Phase 3 (dashboard — self-contained HTML, health-colored portfolio grid, fun-facts stats) both shipped this cycle, per `claude/ledger-phase1-shipped-2026-07-22.md` and `claude/ledger-phase3-dashboard-2026-07-22.md` in the attached project. Real first scan found 7 red · 1 amber · 1 green, headlined by the whole Egraine family being sourced to a disconnected pen drive.

Phase 2 (data reconciliation across the portfolio) is now in progress, run by David directly rather than as a Ledger-initiated action — Thann is the first unit reconciled (source repointed to its own git repo, disputed flag cleared, priority/urgency corrected to match the project's own record; see `domains/business/egraine/ventures/thann/ledger.md`). Remaining Phase 2 items (untracked Ozuvox/project-cars/dives-enterprises, Medex's missing git, live lock cleanup, promoting Thann/Medex to flat ADR-0007 units) are still open.

The four guideline documents referenced throughout this file are maintained as v2.0 in the canonical ALFA+OMEGA repo (ADR-0010) — confirmed current as of this entry.

## v0.6 — 2026-07-22

Framework hardening after the first full self-audit (stored at `reviews/framework/2026-07-22-framework-evaluation.md`, with the resulting plan alongside it). The audit found real drift: a declared-vs-reality contradiction on THANN, three on-disk projects untracked, Medex tracked as an active sprint with no git, systemic git-lock cruft, guideline-copy drift risk, and a parent/child safety gap. Phase 0 (this entry) records the governance decisions; build and data-reconciliation follow.

Five ADRs accepted: **0007** group representation & spin-off model (ventures are independent units linked by `parent:` + `portfolio_members:`, not nested — so any venture can be sold by dropping the link; supersedes the `sub_units:` convention); **0008** child-safety write boundary (a child/sibling session treats parent/sibling folders read-only; destructive ops need explicit ok + backup — the mirror of ADR-0001); **0009** git-lock & folder-access policy (read-only by default, David sole grantor, ask before first git write, lock prevention + cleanup runbook + `_to_delete/` fallback); **0010** canonical guidelines / shared-resources repo (ALFA+OMEGA is now git and the single source of truth; versioned by tag + in-doc stamp; Ledger's own guideline copies superseded); **0011** scan engine & state model (`ledger scan` → `ledger-state.json`, the snapshot spine every other v0.6 skill reads).

Guidelines consolidated: `guidelines/project-standard.md`, `tracking-protocol.md`, `workflow.md`, `checklists.md` replaced with pointer stubs to the canonical ALFA+OMEGA copies (ADR-0010) — not deleted, so existing path references still resolve. The scan engine, the `ledger` skillset, and the dashboard generator are slated to live in ALFA+OMEGA too.

Design only for the build items (scan engine, expanded verb grammar, dashboard, automation) — Phase 1 onward, not yet shipped, per the standing "don't backfill to look further along than it is" principle.

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

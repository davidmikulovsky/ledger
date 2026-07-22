# Architecture Decision Records — this framework's own governance

Not asked for until now (2026-07-21) — this is a new addition. ADRs here capture decisions *about how this framework itself operates*: its boundaries, its storage/hosting model, its own naming and structure. This is distinct from the per-project ledgers under `domains/`, which log what's happening *in the tracked projects*, not decisions about the tracking system itself.

Format: numbered, short title, Status (Accepted / Superseded / Proposed), Context, Decision, Consequences. Superseded ADRs stay in place, marked as such, rather than being deleted — same append-don't-erase principle used in the domain ledgers.

## Index

- [0001 — Read-only boundary on tracked projects](0001-read-only-boundary-on-tracked-projects.md) — this framework never writes to a tracked project's own source; corrections happen only in this framework's own files.
- [0002 — Storage location and hosting](0002-storage-location-and-hosting.md) — local git only, on persistent local storage, no remote for now; supersedes the 2026-07-15 GitHub-private plan for this framework's own history.
- [0003 — Project standard, tracking protocol, and versioned changelog](0003-project-standard-and-tracking-protocol.md) — written standard for what a tracked project should contain, a formal checking protocol (including the claimed-vs-verified discipline and the `components` data structure), and versioning for Ledger itself, starting at v0.2.
- [0004 — Status/priority vocabulary and portable guidelines](0004-status-priority-vocabulary-and-universal-guidelines.md) — `status` and `priority` formalized as two independent canonical enumerations (built for future visualization); the three guideline documents rewritten to be usable outside Ledger's own scope; `guidelines/checklists.md` added. **Vocabulary superseded by ADR-0005; portability/checklist decisions still stand.**
- [0005 — Domain restructure and vocabulary v2](0005-domain-restructure-and-vocabulary-v2.md) — `personal` domain added to nest career/health/nutrition/relationships/sport; `status` simplified to 4 values, `priority` to 3; `disputed` extracted from status into its own flag; new independent `urgency` axis added.
- [0006 — Ledger admin/reporting skill design](0006-ledger-skill-design.md) — single `ledger` skill, verb grammar (report/sync/log/new/portfolio/audit) and a four-tier report depth ladder (glance/brief/full/audit); design only, not yet packaged or tested.

## Not yet backfilled

Several earlier decisions predate this ADR log and only exist in the `projects/ledger` unit ledger: the original framework design (domain/unit/ledger pattern), the SkinThea disputed-then-resolved status, and the framework's own rename from "life-os" to "Ledger" (2026-07-21, done — see that unit's ledger). Happy to backfill any of these as formal ADRs if useful — otherwise they stay as ledger entries, which is a reasonable place for them too.

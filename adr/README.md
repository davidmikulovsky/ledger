# Architecture Decision Records — this framework's own governance

Not asked for until now (2026-07-21) — this is a new addition. ADRs here capture decisions *about how this framework itself operates*: its boundaries, its storage/hosting model, its own naming and structure. This is distinct from the per-project ledgers under `domains/`, which log what's happening *in the tracked projects*, not decisions about the tracking system itself.

Format: numbered, short title, Status (Accepted / Superseded / Proposed), Context, Decision, Consequences. Superseded ADRs stay in place, marked as such, rather than being deleted — same append-don't-erase principle used in the domain ledgers.

## Index

- [0001 — Read-only boundary on tracked projects](0001-read-only-boundary-on-tracked-projects.md) — this framework never writes to a tracked project's own source; corrections happen only in this framework's own files.
- [0002 — Storage location and hosting](0002-storage-location-and-hosting.md) — local git only, on persistent local storage, no remote for now; supersedes the 2026-07-15 GitHub-private plan for this framework's own history.

## Not yet backfilled

Several earlier decisions predate this ADR log and only exist in the `projects/ledger` unit ledger: the original framework design (domain/unit/ledger pattern), the SkinThea disputed-then-resolved status, and the framework's own rename from "life-os" to "Ledger" (2026-07-21, done — see that unit's ledger). Happy to backfill any of these as formal ADRs if useful — otherwise they stay as ledger entries, which is a reasonable place for them too.

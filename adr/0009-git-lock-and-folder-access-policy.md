# ADR-0009: Git-lock handling and folder-access policy

**Status:** Accepted
**Date:** 2026-07-22

## Context

The 2026-07-22 audit found systemic git lock cruft — `index.lock`, `HEAD.lock`, `maintenance.lock`, `*.lock.stale`, `tmp_obj_*` — across THANN, project-cars, Egraine, Jascandi, and LEDGER itself, with two repos holding **live** locks that block their next commit. Root cause, documented in AI-LAB's README: the Cowork device-bridge sandbox blocks delete/rename by default, which breaks `git init`/commit and orphans lock files that then can't be `rm`'d, so cleanup falls back to moving them into `_to_delete/`. The brand-new ALFA+OMEGA repo already exhibited live locks straight from setup.

## Decision

**(a) Access is the owner's alone.** The default stance for any AI session is read-only. Before the first `git init`, or any write/commit/delete in a project, the session asks the owner for permission, naming the exact folder. **David alone grants or revokes** folder access; no session assumes write rights.

**(b) Prevention.** One session per repo at a time (concurrent `index.lock` is the main cause). Finish git operations before ending a session (a half-finished commit leaves a live lock). Commit in small real steps.

**(c) Cleanup runbook.** A lock is *stale* if no git process is running against that repo — then removing `.git/index.lock`, `.git/HEAD.lock`, and `.git/objects/maintenance.lock` is safe. When the sandbox can't delete, the fallback is moving the lock into `_to_delete/` renamed `*.stale`; the **owner empties `_to_delete/` periodically** (the one step the AI can't finish). `ledger scan` surfaces every live lock as a red flag so locks never accumulate invisibly again.

The full runbook lives in `guidelines/git-and-access.md` (to be written; canonically in ALFA+OMEGA per ADR-0010).

## Consequences

Lock cruft becomes visible and bounded; write access is explicit and owner-controlled, tightening ADR-0001's boundary rather than loosening it. Cost: a small permission step before the first git write on any project, and a periodic manual `_to_delete/` sweep only the owner can perform.

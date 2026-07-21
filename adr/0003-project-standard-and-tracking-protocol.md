# ADR-0003: Project standard, tracking protocol, and versioned changelog for Ledger itself

**Status:** Accepted
**Date:** 2026-07-21

## Context

Two tracked projects (Egraine, Jascandi) so far. The Jascandi deep-dive the same day — checking git state, reading README/changelog, fetching the live site directly — worked well but was done ad hoc, with no written standard for what a project should contain or how Ledger should check it. David flagged this as a real scaling problem: with more projects, ad hoc tracking gets messy fast, and asked for a defined internal structure for projects, a checking protocol for Ledger, and for Ledger to hold itself to the same standard it asks of tracked projects.

Two things from the Jascandi session were worth generalizing rather than treating as one-offs: the distinction between what a project's docs *claim* (e.g. "v2.2, live") and what's actually been *verified* this session (fetching the URL, reading `git status`), and the fact that Jascandi's own organic structure — README, `docs/` vs `technical/`, a changelog, git as non-negotiable — was already a reasonable template worth writing down rather than rediscovering per project.

## Decision

Three new guideline documents at `guidelines/`: `project-standard.md` (what a tracked project should contain — git as the one hard requirement, README/docs/changelog as expected-but-not-mandatory, explicit framing that missing pieces are normal), `tracking-protocol.md` (how Ledger checks a project against that standard, formalizing the claimed-vs-verified discipline and introducing a structured `components` data block in `_unit.md` front-matter), and `workflow.md` (a Start → Work → Check → Update → End/New-Version loop, offered as an adaptable default mapped to the existing `type` field, not a mandate).

Ledger now applies `project-standard.md` to itself: `SPEC.md` (full specification), `CHANGELOG.md` (Ledger's own version history, distinct from both ADRs and tracked-project ledgers), and `ROADMAP.md` (future directions — reporting skills, a live dashboard surface, notifications — explicitly unbuilt) added. Versioning introduced starting at v0.1 (retroactive, the framework's existence through 2026-07-21) and v0.2 (this change).

The `components` schema was piloted on Jascandi immediately, using data already gathered the same session, rather than left as a theoretical addition.

## Consequences

Future project units have a written standard to be checked against instead of an implicit one reconstructed each time. The `components` block adds real structure to `_unit.md` files, which is more to maintain per unit but pays for itself once report-generation (see `ROADMAP.md`) becomes real — structured data is what a future skill or dashboard would need to read, rather than parsing prose. The versioning scheme means Ledger's own evolution is now a legible history rather than something only reconstructable from git log and chat transcripts. Cost: another layer of documents to keep in sync with reality — the guidelines themselves are subject to the same "don't let claims drift from what's actually true" discipline they impose on tracked projects.

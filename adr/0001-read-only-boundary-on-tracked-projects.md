# ADR-0001: Read-only boundary on tracked projects

**Status:** Accepted
**Date:** 2026-07-21

## Context

This framework tracks external projects — business ventures, apps, research, creative work, personal-life domains, anything — by reading their real source material (decision logs, task trackers, git repos, docs, spec sheets) and summarizing state, status, and relationships in its own unit files and ledgers. It deliberately does not hold the actual project content.

In practice, every correction made so far (e.g. rebuilding the Egraine unit after reading its real Decision Log and Strategic Plan) was applied only to this framework's own `_unit.md`/`ledger.md` files — never to the source documents themselves, which were only ever read, never written to. That was true so far, but it held by consistent practice, not by an enforced rule. David has now made it an explicit, non-negotiable requirement rather than an implicit one.

## Decision

This framework — and any session of Claude operating within it — must **never write, edit, create, delete, or otherwise modify any file belonging to a tracked project's own source location**: its repo, decision log, task tracker, docs folder, CMS, live store/site, or any other system where that project natively lives. This applies regardless of how minor the change, how obviously correct the fix, or how convenient it would be to just make it there directly.

All corrections, conflict resolutions, and updates happen **only within this framework's own files** — unit files, ledgers, and ADRs. Those files capture this framework's *understanding* of a project (status, relationships, open questions), never the project's own record of itself.

If a discrepancy or conflict is found between what this framework believes and what a project's real source says, it gets **flagged here and left unresolved** — for David, or a separate session working directly and explicitly within that project, to resolve at the actual source. This framework cannot and does not self-heal source-side inconsistencies.

A related distinction, called out explicitly so it isn't blurred later: if David asks for help on a tracked project directly — e.g. "set up git for Medex's docs folder" — that is a separate, explicit, user-directed task performed with awareness that it touches that project's own location. It is not something this framework does automatically or silently as a side effect of tracking progress. Tracking activity itself (reading, summarizing, logging) never has side effects outside this framework's own folder.

## Consequences

Tracked projects remain fully independent and authoritative over their own history; this framework carries zero write risk to any of them, by construction. The cost: this framework cannot fix a discrepancy it finds — it can only surface it. Resolution always requires a human decision and, if source-side changes are needed, a deliberate separate action outside this framework's normal operation.

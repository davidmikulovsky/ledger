# ADR-0006: Ledger admin/reporting skill — single `ledger` skill, verb + depth grammar

**Status:** Accepted
**Date:** 2026-07-22

## Context

This was the second time David asked about a specific tracked project (THANN) in ordinary conversation rather than through anything repeatable. Rather than answer ad hoc again, he asked for a way to pull status and reports "on different levels" — from a one-line active/urgent check up to an extensive overview — invoked like a slash command with a project name, and asked Claude to design the mechanism itself rather than prescribe it, since Claude understands the mechanics better. This is the item named but not built in `ROADMAP.md`'s "Reporting skills" section ("a skill that reads across one or several units' `_unit.md`/`ledger.md` files and produces a digestible status report... generated on demand").

David supplied two candidate phrasings of that request and asked Claude to judge them before doing anything else. The first was his own conversational ask (goal stated, mechanism delegated to Claude). The second was a pre-written "spec" that read like a finished answer rather than an instruction, and — on inspection — was ungrounded in how a Claude skill or Ledger actually work: it proposed "training" the skill on prompts and storing project data in "a database or knowledge graph," neither of which has any bearing on how a skill (a markdown instruction file, read at invocation) or Ledger (plain files, read directly) function. Claude recommended proceeding from David's own prompt and drafted a fuller design as a third option; David approved proceeding from prompt 1, treating that fuller design as its direct next iteration, asked for the `pulse` depth name to be replaced (found misleading), and asked for the rest of a skillset — not just single-project reporting — covering Ledger admin generally.

## Decision

One skill, `ledger`, rather than one skill per capability — a single trigger surface with a verb grammar, so new capabilities extend the grammar instead of multiplying skill files that could collide on triggering:

```
/ledger <project>                       → report, brief depth (default)
/ledger report <project> [depth]        → glance | brief | full | audit
/ledger sync <project>                  → explicit Check→Update cycle, always logs
/ledger log <project> "<update>"        → append a conversational update, no verification
/ledger new <project> <source-path>     → Start checklist: bootstrap the unit
/ledger portfolio [urgent|active|all]   → cross-project rollup
/ledger audit                           → Ledger-wide governance sweep
```

**`report` depths** (renamed from an earlier draft's `pulse`, which read as a health-monitoring metaphor rather than "quick check" — `glance` was chosen instead):

- `glance` — status/priority/urgency/disputed, one line each, straight from `_unit.md` front-matter. No other file reads.
- `brief` (default when no depth is given) — glance + the last 2–3 `ledger.md` entries + a synthesized "what's next" line. Ledger-only, no source re-check.
- `full` — brief + live re-verification against `guidelines/project-standard.md`'s categories, each labeled claimed or verified per `guidelines/tracking-protocol.md`; updates the `components:` block and `verified:` dates; appends a ledger entry recording what was checked.
- `audit` — full + a principles-compliance pass: does the unit's `type` match `guidelines/workflow.md`'s expectations for that type, are status/priority/urgency/disputed internally consistent, is anything stale.

**Name resolution.** Before acting on any verb, the project name is resolved against `_index.md`: an exact match proceeds; no match offers to run `ledger new`; a name matching units in more than one domain asks which, rather than guessing.

**Verified footer.** Every `report` output closes with `last verified: <date> · depth: <x>`, so the claimed-vs-verified discipline is visible in the output itself, not only applied internally.

**Read-only boundary carries over unconditionally** (ADR-0001). `sync`, `report ... full`, and `report ... audit` read a tracked project's real source but never write to it — only to this framework's own `_unit.md`/`ledger.md`. `new` and `log` only ever write inside Ledger's own folder.

Six verbs are in scope for this design; `report` and `log` cover the default workflow already documented in `README.md` ("David reports updates conversationally, or asks to sync"), `sync`/`new`/`portfolio`/`audit` extend it to the rest of the admin surface David asked for.

## Consequences

A single trigger surface (`/ledger ...`) stays simple for David to remember and won't compete with future skills for triggering priority; the grammar is extensible — a new verb is a grammar addition, not a new skill file. Cost: the skill's own instructions carry routing logic for six verbs in one file rather than six focused files; if that gets unwieldy in practice, splitting later isn't precluded by this decision.

Not yet done: packaging this design as an actual installable `.skill` file, and testing it end-to-end. This ADR records the design; `CHANGELOG.md` v0.5 notes it as designed, not shipped, per the standing "don't backfill the roadmap to look further along than it is" principle already in place on `ROADMAP.md`.

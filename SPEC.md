# Ledger — Specification

*Ledger applying `guidelines/project-standard.md` to itself. If a tracked project is expected to have a spec, so is the thing doing the tracking.*

## What Ledger is

A project-tracking framework — not where project content lives, but where "where did I leave off, and is that actually still true" gets answered for anything being tracked: businesses, apps, design work, research, personal goals. Named for its core mechanism: every tracked thing keeps a ledger, an append-only record of what happened and when.

## Core principles

1. **Read-only toward tracked projects.** Ledger never writes to a tracked project's own source — only reads it. See `adr/0001-read-only-boundary-on-tracked-projects.md`. This is the single most load-bearing rule in the whole design.
2. **Append-only history.** `ledger.md` files are never rewritten, only appended to. ADRs are never deleted, only superseded in place. Git provides the same guarantee at the framework level. The point is an honest record — what was believed true on a given date stays visible, even after it's corrected.
3. **Claimed vs. verified.** Ledger distinguishes what a source document says from what's actually been checked this session. See `guidelines/tracking-protocol.md`.
4. **Absence is normal.** A tracked project missing docs, a changelog, or a decision log isn't a defect — see `guidelines/project-standard.md`. The one exception is git, which is a hard requirement for anything tracked.
5. **Ledger doesn't hold the work.** It links to real sources (a repo, a decision log, a live URL) and summarizes; it's never the canonical copy of anything it tracks.

## Structure

```
LEDGER/
  README.md              orientation, quick start
  SPEC.md                this file
  CHANGELOG.md            Ledger's own version history
  ROADMAP.md              future directions, not yet built
  guidelines/
    project-standard.md   what a tracked project should look like, incl. status/priority vocabulary
    tracking-protocol.md  how Ledger checks a project, the components schema
    workflow.md           the Start/Work/Check/Update/End loop
    checklists.md          the same loop, as concrete steps
  adr/                    governance decisions about Ledger itself
  domains/
    business/<unit>/
    personal/<career|health|nutrition|relationships|sport>/<unit>/
    projects/<unit>/
    team/<unit>/
      _unit.md             type, status, priority, urgency, disputed, source links, components
      ledger.md            append-only dated history
  reviews/                 optional daily/weekly rollups, empty until used
  _index.md                 rolled-up view across every unit
```

> **Guidelines are now canonically maintained in the shared ALFA+OMEGA git repo (ADR-0010).** The four files under `guidelines/` here are superseded pointer stubs, kept so existing path references still resolve; edit the canonical copies in ALFA+OMEGA (versioned by git tag + in-doc version stamp).

## Schema reference

**`_unit.md` front-matter:**

| Field | Values | Notes |
|---|---|---|
| `domain` | business, personal (career, health, nutrition, relationships, sport), projects, team, ... | open-ended, add more as needed; `personal` nests its own sub-domains |
| `unit` | free text (matches folder name) | |
| `type` | goal \| plan \| sprint \| milestone \| maintenance | see `guidelines/workflow.md` for how each moves through the loop |
| `status` | active \| blocked \| dormant \| ended | canonical set, see `guidelines/project-standard.md` — lifecycle state, independent of priority and urgency |
| `priority` | high \| medium \| low | canonical set, see `guidelines/project-standard.md` — real-world stakes/importance, not progress or activity |
| `urgency` | high \| medium \| low | canonical set, see `guidelines/project-standard.md` — time-sensitivity, independent of priority (Eisenhower-style split: important vs. time-sensitive are different questions) |
| `disputed` | true \| absent | optional flag, not part of `status` — set when the record itself is contested/unresolved, independent of the other three axes |
| `source` | path(s) / URL(s) | where the real thing lives — never duplicated here |
| `last_updated` | date | of the most recent ledger entry |
| `components` | structured block, optional | see `guidelines/tracking-protocol.md` |

**Nesting:** units can nest (`business/egraine/ventures/medex-beauty-clinic`) when one thing has real sub-things.

## Current scope (be honest about this)

Right now, Ledger is a simple tracking tool for git-backed projects, plus reading and summarizing whatever docs/specs exist. It has no automation, no scheduled checks, no live data feed, no notifications — those are `ROADMAP.md` items, not current behavior. Two top-level domains (business, projects) have real units; `personal` (career, health, nutrition, relationships, sport) is scaffolded and empty. That's the honest current state, not a gap to apologize for.

## Version

See `CHANGELOG.md`. Current: v0.6.

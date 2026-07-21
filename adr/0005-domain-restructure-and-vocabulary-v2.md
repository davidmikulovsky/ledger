# ADR-0005: Personal domain nesting; status/priority simplified; urgency added; disputed extracted

**Status:** Accepted
**Date:** 2026-07-21

## Context

David reviewed v0.3 (ADR-0004's vocabulary) and raised two further points, same day.

First, structural: the seven top-level domains (`business`, `projects`, `health`, `sport`, `nutrition`, `relationships`, `career`) blurred two different kinds of thing — one area of work (business) and one hobby project domain (projects) sitting flat alongside five domains that are all facets of one thing, a personal life. He asked for `career`, `health`, `nutrition`, `relationships`, `sport` to be nested under a new top-level `personal` domain.

Second, vocabulary. Reviewing the ADR-0004 status/priority set directly, he questioned whether it was actually as clean as it claimed to be:
- `dormant` and `paused` — "they seem similar to me," asked whether they should merge.
- `done` and `ended` — same question, same instinct.
- `disputed` — asked what it actually is, and whether it can merge with something else or needs its own field.
- `priority`'s `critical` tier — "we only recognize 3 levels," asked for it to be dropped.
- Most substantively: **urgency wasn't reflected at all.** His own framing: "I want to say something is urgent but low priority vs. something is urgent and high priority — those are 2 different outcomes. Also high priority project can have low urgency, ex. if work is just visual refactor — it can wait." Priority alone couldn't express this; ADR-0004's vocabulary conflated importance and time-sensitivity into one axis.

## Decision

**Domains.** `domains/personal/{career,health,nutrition,relationships,sport}/` — five domains moved (via `git mv`, preserving history) under a new `personal` parent. Top level is now `business` / `personal` / `projects`.

**Status** collapsed to `active | blocked | dormant | ended`:
- `paused` merged into `dormant` — both meant "no current work, not closed"; splitting them required a judgment call (intent to resume vs. not) that wasn't reliably knowable or worth tracking as a distinct enum value.
- `done` merged into `ended` — both meant "the loop terminated." Whether it succeeded or was discontinued is real information, but it belongs in the ledger entry's prose, not a dedicated status value.
- `disputed` removed from the status enum. It was never really a lifecycle state — it answers "is what's recorded here trustworthy," which is orthogonal to whether the project is active, blocked, dormant, or ended. Reintroduced as an independent optional flag, `disputed: true` (omitted when not disputed), so it can be layered onto whatever the real status is instead of overwriting it.

**Priority** collapsed to `high | medium | low`:
- `critical` dropped, per David's explicit "we only recognize 3 levels."
- `optional` folded into `low` — it was already describing "real but limited stakes, not scheduled," which `low` covers without a separate tier.

**Urgency** added as a new, independent third axis: `high | medium | low`. Answers "how soon does this need attention," distinct from priority's "how much does this matter" — an Eisenhower-matrix-style split. This directly implements David's stated requirement: urgent-and-low-priority and urgent-and-high-priority are now expressible as genuinely different states, and a high-priority, low-urgency case (his example: a visual refactor that matters but can wait) is no longer forced into a false urgency by the absence of the field.

**Propagation.** `guidelines/project-standard.md`'s vocabulary section rewritten; `workflow.md` and `checklists.md`'s `done`/`ended` references updated; `SPEC.md`'s schema table and structure diagram updated; `README.md`'s domain list and front-matter field list updated; every existing unit (Egraine parent + 4 ventures, Jascandi, Ledger's own unit) given a proposed `urgency` value, each explicitly flagged as Ledger's read pending David's confirmation — same review pattern used for `priority` in ADR-0004. SkinThea's `priority: optional` corrected to `priority: low`.

## Consequences

The vocabulary is smaller (4 status values instead of 7, 3 priority values instead of 5) and gains a genuinely new dimension (urgency) rather than growing more complex — a rare combination, made possible because the removed distinctions (`paused`/`dormant`, `done`/`ended`) weren't actually load-bearing, while the added one (urgency vs. priority) was a real gap. ADR-0004 remains in place, unedited, per the append-only/never-delete-only-supersede principle — this ADR supersedes its vocabulary section specifically, not the document as a whole (the portability and checklist decisions in ADR-0004 still stand).

Cost: any future unit that would have reached for `paused` or `done` specifically now needs to fold that nuance into prose instead of a field — a small loss of machine-sortable precision in exchange for a smaller, more honestly-used enum. The `disputed` flag's exact semantics (does it block anything, does it need a resolution date) aren't fully specified yet — deferred until a real disputed case actually arises again, per the "missing pieces are normal" principle.

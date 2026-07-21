# ADR-0004: Canonical status/priority vocabulary; guideline docs made portable; checklists added

**Status:** Accepted
**Date:** 2026-07-21

## Context

David reviewed the v0.2 guideline documents and raised three points. First: `status` and `priority` were being used inconsistently — Jascandi's `dormant-capable` and SkinThea's `hibernated` were both invented on the spot to solve the same real problem, trying to encode two different questions ("how much does this matter" and "what's happening right now") into a single field. David gave a concrete example of the confusion this caused: Jascandi should be low priority not because it's incomplete, but because it has no real business or client stakes — a fact about importance, not about progress or activity. He also wants future ability to visualize tracked units by priority/urgency and separately by status, which requires clean, small, canonical enumerations rather than free text or one-off inventions.

Second: David pointed out that `project-standard.md`, `tracking-protocol.md`, and `workflow.md` were written referencing Jascandi and David by name — fine within Ledger's own scope, but it meant these documents couldn't be lifted out and used to drive a different tracking effort entirely, even though the principles themselves aren't Ledger-specific.

Third: no checklists existed. The guideline documents described what should happen at each workflow stage in prose, but nothing gave a concrete, checkable, step-by-step sequence a project could actually follow start to finish without skipping something by accident.

## Decision

**Vocabulary.** `priority` and `status` formalized as two independent, canonical enumerations in `guidelines/project-standard.md`:
- `priority`: `critical` \| `high` \| `medium` \| `low` \| `optional` — real-world stakes and urgency, explicitly not a measure of progress or activity.
- `status`: `active` \| `paused` \| `blocked` \| `dormant` \| `done` \| `ended` \| `disputed` — current lifecycle state, explicitly independent of how much the project matters.

Existing units corrected to the canonical set: Jascandi (`dormant-capable` → `status: active`, `priority: low` unchanged but now explicitly justified) and SkinThea (`hibernated` → `dormant`, same meaning). `SPEC.md`'s schema table updated to match.

**Portability.** `project-standard.md`, `tracking-protocol.md`, and `workflow.md` rewritten to remove Ledger- and David-specific references, using generic language ("a tracker," "the project owner") throughout, while keeping concrete lessons (the claimed-vs-verified discipline, the multi-copy git caution) as generalized principles rather than dropping them. Ledger-specific application of the same principles remains, deliberately, in `SPEC.md`, `CHANGELOG.md`, and the unit files themselves — specificity belongs there, not in the portable guideline layer.

**Checklists.** New `guidelines/checklists.md`: the `workflow.md` loop rewritten as concrete checkboxes per stage (Start, Work, Check, Update, End/New-Version), cross-referenced from all three other guideline documents.

## Consequences

Priority and status are now genuinely independent and small enough to visualize by — a stated goal for the future dashboard surface (see `ROADMAP.md`), and this decision is what makes that buildable later without a data model change. The cost of the vocabulary change: any future unit that would have reached for a one-off status word (the way `dormant-capable` and `hibernated` were each invented under time pressure) now needs to fit the canonical seven, or a case for an eighth needs to be made explicitly rather than improvised per unit.

The guideline documents are now double-purposed — usable standalone, outside Ledger — at the cost of being slightly more abstract to read than when they could just say "Jascandi" and "David" directly. Worth it for the stated goal (these principles outliving or extending beyond this specific deployment), but a real tradeoff, not a free improvement.

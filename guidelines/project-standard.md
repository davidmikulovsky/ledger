# Project Standard

*What a project should look like so it can be tracked cleanly. Handed to a project when it starts; referenced whenever work resumes. Written to stand on its own — these principles apply to any tracked project, not just the tracker that happens to be using them. Companion documents: `tracking-protocol.md` (how a tracker reads against this standard), `workflow.md` (the working loop this standard supports), `checklists.md` (the same loop, as concrete steps).*

## Why this exists

A tracking system that reads a project's real material, rather than holding a copy of it, only works if the project has *some* consistent, findable shape — not a rigid one, just consistent enough that picking it up cold (a new session, a collaborator, the original owner returning after months away) doesn't require reverse-engineering where anything lives. This document exists because a real project, tracked in practice, organically converged on a shape worth writing down before the next one has to rediscover it by accident.

## The one hard requirement: git

**Every tracked project must be a git repository.** Not optional, not "add it later." This is the one thing worth flagging as a real gap rather than a normal in-progress state, because everything else in this standard — history, recoverability, an honest record of what changed and when — depends on it. A project with no git has no verifiable past, only whatever someone remembers.

Minimum bar: `git init` done, meaningful commits as work happens (not one giant commit at the end), a remote if the project matters enough to survive one device dying. A local-only repo is acceptable for something new or low-stakes; it should still exist.

## Expected structure

None of the below needs to exist on day one. All of it earns its place as the project grows. What matters is that when something *does* exist, it lives somewhere predictable.

**`README.md`** — the front door. What this project is, current status in one line, basic folder structure, how to run/deploy it if that applies. This is the one doc worth writing early, even briefly, because it's what makes everything else findable.

**Docs and specs** — whatever form fits the project: a `docs/` folder, a single spec file, a brief. Audience-facing material (what this is, who it's for, pricing/scope if relevant) and technical/project material (design decisions, architecture, how it's built) are worth keeping visibly separate once there's enough of either to matter — a `docs/` (audience-facing) vs `technical/` (project-facing) split is one reasonable way to do that, not the only one.

**A changelog and/or a decision log** — useful, not mandatory, and they answer different questions. A **changelog** is *what* happened, in order — a plain-language history someone can read to get oriented fast, explicitly not a substitute for `git log` but a map on top of it. A **decision log or ADRs** is *why* something happened — the reasoning, the alternatives considered, the tradeoffs. A project can have one, both, or neither early on; git commit messages are a minimum viable substitute for both until something more structured earns its keep.

**A live artifact, if there is one** — a deployed site, an app, a running service. Worth noting *where* it's supposed to be reachable (a URL, a deployment target) so status can actually be checked rather than assumed.

## Missing pieces are normal

A new project will be missing most of this, and that's expected, not a problem to fix immediately. The standard exists so that *when* something is written, it lands somewhere predictable — not to gate a project from starting until it's fully documented. Everything on this list except git should be read as "not yet present," a normal and unremarkable state, not a defect.

## Status, priority, and urgency: three independent axes (plus a disputed flag)

These often get collapsed into one idea — "important," "active," and "urgent" start to feel like the same thing — but they answer three different questions and should be tracked separately.

**Status** answers: *what's actually happening with it right now?* Current lifecycle state, independent of how much it matters or how soon it needs attention.

- `active` — real work happening now, or expected imminently.
- `blocked` — stalled on something outside the project's own control — a decision, a dependency, another party.
- `dormant` — no current work and no clear intent to resume right now, but not closed. Covers both "paused, will pick back up" and "no near-term plan" — that distinction matters less than whether it's genuinely closed, and belongs in prose/ledger notes if worth saying, not a separate status value.
- `ended` — work on it has stopped for good, regardless of outcome — whether it reached its goal or was discontinued. Whether it succeeded is worth a line in the ledger; it doesn't need its own status value.

**Priority** answers: *how much does this matter?* Real-world stakes and importance, not progress, not how soon.

- `high` — matters a lot, real ongoing stakes.
- `medium` — matters, no outsized stakes either way.
- `low` — real, but limited stakes. A project can get plenty of active attention and still sit here — priority isn't a measure of effort or activity, just of what's riding on it. A well-worked personal or hobby project with no dependents and no revenue behind it is a clean example: real, current, cared-for, and still legitimately low priority. Backlog/someday ideas belong here too, not in a separate tier — low priority already covers "not now."

**Urgency** answers: *how soon does this need attention?* Time-sensitivity, independent of priority — an Eisenhower-matrix split between "important" and "urgent," which are genuinely different questions with genuinely different answers. A high-priority project can be low urgency (a visual refactor that matters but can wait); a low-priority project can still be urgent (something small but time-boxed). Urgent-and-low-priority and urgent-and-high-priority are different situations that call for different responses, which is exactly why this needs to be its own field rather than folded into priority.

- `high` — needs attention soon; delay has a near-term cost.
- `medium` — should get attention in a normal timeframe, no immediate deadline.
- `low` — no time pressure; can wait indefinitely without cost.

**Disputed** is not a status value — it's a separate optional flag (`disputed: true`, omitted otherwise). It answers a different question again: *is the tracked information itself in conflict or unresolved?* That's orthogonal to whether the project is active/blocked/dormant/ended, to how much it matters, and to how soon it needs attention — a project can be disputed while simultaneously being active and high priority. Keeping it a separate flag rather than a status value means it can be layered onto whatever the real status is instead of overwriting it.

Keeping these as small, independent fields (rather than one combined field, or free text) is deliberate: it's what makes a project sortable and visualizable along any one axis later without the others bleeding into it.

## A living reference

See this standard applied to a real, currently tracked project's own unit file for what this looks like in practice, rather than in the abstract.

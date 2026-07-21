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

## Priority and status: two independent axes

These often get collapsed into one idea — "important" and "active" start to feel like the same thing — but they answer different questions and should be tracked separately.

**Priority** answers: *how much does this matter, if left unattended?* It's about real-world stakes and urgency, not progress. A project can be extremely far along and still low priority (nothing depends on it right now), or brand new and critical (a real deadline, a real consequence if it slips).

- `critical` — time-sensitive, real consequences if neglected right now.
- `high` — matters a lot, real ongoing stakes.
- `medium` — matters, no urgent deadline.
- `low` — real, but limited stakes. A project can get plenty of active attention and still sit here — priority isn't a measure of effort or activity, just of what's riding on it. A well-worked personal or hobby project with no dependents and no revenue behind it is a clean example: real, current, cared-for, and still legitimately low priority.
- `optional` — explicitly backlog/someday. Not scheduled, not abandoned, just not now.

**Status** answers: *what's actually happening with it right now?* It's about current lifecycle state, independent of how much it matters.

- `active` — real work happening now, or expected imminently.
- `paused` — stopped, with clear intent to resume.
- `blocked` — stalled on something outside the project's own control — a decision, a dependency, another party.
- `dormant` — no current work and no near-term plan, but not closed. Could restart anytime, nobody's actively planning to.
- `done` — reached its goal. Applies naturally to project types with a real endpoint (a goal, a sprint, a milestone).
- `ended` — deliberately discontinued or closed, regardless of whether it succeeded. Different from `done`: `done` means it got there, `ended` means work on it stopped.
- `disputed` — the *tracked information itself* is in conflict or unresolved — not a statement about the project's real-world activity, but a flag that what's recorded here shouldn't be trusted until sorted out.

Keeping these as two small, separate enumerations (rather than one combined field, or free text) is deliberate: it's what makes a project sortable and visualizable along either axis independently later — "what's urgent" and "what's active" are genuinely different questions and deserve different answers.

## A living reference

See this standard applied to a real, currently tracked project's own unit file for what this looks like in practice, rather than in the abstract.

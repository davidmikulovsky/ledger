# Project Standard

*What a project should look like so it can be tracked cleanly. Handed to a project when it starts; referenced whenever work resumes. Companion document: `tracking-protocol.md` (how Ledger reads against this standard) and `workflow.md` (the working loop this standard supports).*

## Why this exists

Ledger tracks projects by reading their real material, not by holding it. That only works if a project has *some* consistent, findable shape — not a rigid one, just consistent enough that picking it up cold (a new session, a collaborator, you in six months) doesn't require reverse-engineering where anything lives. Jascandi converged on this shape organically before this document existed; this writes down the pattern so the next project doesn't have to rediscover it by accident.

## The one hard requirement: git

**Every tracked project must be a git repository.** Not optional, not "add it later." This is the one thing Ledger will actually flag as a real gap rather than a normal in-progress state, because everything else in this standard — history, recoverability, an honest record of what changed and when — depends on it. A project with no git has no verifiable past, only whatever someone remembers.

Minimum bar: `git init` done, meaningful commits as work happens (not one giant commit at the end), a remote if the project matters enough to survive one device dying. A local-only repo is acceptable for something new or low-stakes; it should still exist.

## Expected structure

None of the below needs to exist on day one. All of it earns its place as the project grows. What matters is that when something *does* exist, it lives somewhere predictable.

**`README.md`** — the front door. What this project is, current status in one line, basic folder structure, how to run/deploy it if that applies. This is the one doc worth writing early, even briefly, because it's what makes everything else findable.

**Docs and specs** — whatever form fits the project: a `docs/` folder, a single spec file, a brief. Business-facing material (what this is, who it's for, pricing/scope if relevant) and technical/project material (design decisions, architecture, how it's built) are worth keeping visibly separate once there's enough of either to matter — Jascandi's `docs/` (business) vs `technical/` (project) split is one reasonable way to do that, not the only one.

**A changelog and/or a decision log** — useful, not mandatory, and they answer different questions. A **changelog** is *what* happened, in order — a plain-language history someone can read to get oriented fast (Jascandi's `technical/changelog.md` is explicit about this: "not a git log substitute... a plain-language map for anyone picking up the project cold"). A **decision log or ADRs** is *why* something happened — the reasoning, the alternatives considered, the tradeoffs. A project can have one, both, or neither early on; git commit messages are a minimum viable substitute for both until something more structured earns its keep.

**A live artifact, if there is one** — a deployed site, an app, a running service. Worth noting *where* it's supposed to be reachable (a URL, a deployment target) so status can actually be checked rather than assumed.

## Missing pieces are normal

A new project will be missing most of this, and that's expected, not a problem to fix immediately. The standard exists so that *when* something is written, it lands somewhere predictable — not to gate a project from starting until it's fully documented. Ledger is built to read "not yet present" as a normal, unremarkable state for everything on this list except git.

## A living reference

Jascandi (`domains/projects/jascandi/`) is the current best real example of this shape in practice — not because it was built to satisfy this document, but because this document was written by noticing what already worked there.

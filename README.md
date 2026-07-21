# Ledger

A project-tracking framework — not where project content lives, but where you can always answer "where did I leave off" for anything you're running: a business, an app, a design, a piece of research, a hobby, a personal goal. Built to grow into any of those, not scoped to "life tracking" specifically — the name reflects its core mechanism (every unit keeps a ledger of what happened), not a claimed domain.

## How it's organized

```
domains/<domain>/<unit>/
  _unit.md      ← what this unit is: type, status, priority, links to real source material
  ledger.md     ← append-only dated log of what happened, in your own words or mine
```

- **domain** = a broad area: business, projects, health, sport, nutrition, relationships, career — add more anytime, nothing about the design assumes this list is final.
- **unit** = a specific thing within that domain: a project, a venture, a person, a workout block, a recipe collection. Units can nest (e.g. `business/egraine/ventures/medex-beauty-clinic`) when one thing has sub-things.
- **_unit.md** front-matter fields:
  - `type`: goal | plan | sprint | milestone | maintenance — pick whatever fits; maintenance = ongoing, no finish line (most relationships, most business operations).
  - `status`: active | paused | done | dormant | blocked
  - `priority`: high | medium | low
  - `source`: path(s) to where the real content/data lives (a git repo, a folder of docs, a spreadsheet) — this framework links to it, doesn't duplicate it.
  - `last_updated`: date of the most recent ledger entry.
  - `components`: optional structured block (git/docs/changelog/live-artifact status, each with a verification date) — see `guidelines/tracking-protocol.md`.
- **ledger.md** — short dated entries, newest first, never rewritten, just appended to. This is the history and the "what's the status" answer in one place.

## Guidelines

Three companion documents, added 2026-07-21 as tracked units grew past what ad hoc tracking could keep straight:

- **`guidelines/project-standard.md`** — what a tracked project should contain (git is the one hard requirement; everything else — README, docs, changelog — is expected but fine to be missing early on).
- **`guidelines/tracking-protocol.md`** — how Ledger checks a project against that standard, including the claimed-vs-verified discipline and the `components` schema.
- **`guidelines/workflow.md`** — the Start → Work → Check → Update → End/New-Version loop a project moves through, offered as a default, not a mandate.

Ledger holds itself to the same standard — see `SPEC.md`, `CHANGELOG.md`, and `ROADMAP.md` (future directions: reporting skills, a live dashboard, notifications — none of it built yet).

## This folder is not the work

Nothing in `domains/` is the actual project. `_unit.md` and `ledger.md` point at the real thing (a repo, a doc folder, a fitness tracker export) via `source:`. When you ask "what's the status of X," the ledger plus a quick read of the linked source is the answer.

## Hard rule (see `adr/0001-read-only-boundary-on-tracked-projects.md`)

Ledger never writes to, edits, or otherwise modifies a tracked project's own source — only reads it. All corrections happen inside Ledger's own files. This is enforced, not just a habit.

## Using it

- Ad hoc: tell me "update [unit]" with what happened, or just talk about it and I'll log it.
- If something's already written down elsewhere (a decision log, a task tracker, a repo), say "sync [unit] from source" and I'll re-read the real source rather than needing you to re-summarize it.
- `_index.md` is a rolled-up view across every unit — regenerate it by asking any time.
- Weekly/daily reviews in `reviews/` are optional and empty until you want that cadence.
- Governance/meta decisions about Ledger itself (not about any tracked project) live in `adr/` as ADRs.

## Git

This folder is git-tracked locally (see `adr/0002-storage-location-and-hosting.md` for the current hosting decision) so you get free history of how goals, priorities, and status changed over time — separate from git history in the actual project repos it links to.

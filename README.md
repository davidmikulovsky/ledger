# life-os

Personal tracking framework — not where project content lives, but where you can always answer "where did I leave off" for any domain of your life.

## How it's organized

```
domains/<domain>/<unit>/
  _unit.md      ← what this unit is: type, status, priority, links to real source material
  ledger.md     ← append-only dated log of what happened, in your own words or mine
```

- **domain** = a life area: health, sport, nutrition, relationships, career, business, projects.
- **unit** = a specific thing within that domain: a project, a person, a venture, a workout block, a recipe collection. Units can nest (e.g. `business/egraine/ventures/medex-beauty-clinic`) when one thing has sub-things.
- **_unit.md** front-matter fields:
  - `type`: goal | plan | sprint | milestone | maintenance — pick whatever fits; maintenance = ongoing, no finish line (most relationships, most business operations).
  - `status`: active | paused | done | dormant | blocked
  - `priority`: high | medium | low
  - `source`: path(s) to where the real content/data lives (a git repo, a folder of docs, a spreadsheet) — this framework links to it, doesn't duplicate it.
  - `last_updated`: date of the most recent ledger entry.
- **ledger.md** — short dated entries, newest first or oldest first (pick one and stay consistent per file), never rewritten, just appended to. This is your history and your "what's the status" answer in one place.

## This folder is not the work

Nothing in `domains/` is the actual project. `_unit.md` and `ledger.md` point at the real thing (a repo, a doc folder, a fitness tracker export) via `source:`. When you ask "what's the status of X," the ledger plus a quick read of the linked source is the answer.

## Using it

- Ad hoc for now: tell me "update [unit]" with what happened, or just talk about it and I'll log it.
- `_index.md` is a rolled-up view across every unit — regenerate it by asking any time.
- Weekly/daily reviews in `reviews/` are optional and empty until you want that cadence.

## Git

This folder is git-tracked so you get free history of how goals, priorities, and status changed over time — separate from git history in the actual project repos it links to.

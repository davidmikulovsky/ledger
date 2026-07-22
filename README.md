# Ledger

A project-tracking framework — not where project content lives, but where you can always answer "where did I leave off" for anything you're running: a business, an app, a design, a piece of research, a hobby, a personal goal. Built to grow into any of those, not scoped to "life tracking" specifically — the name reflects its core mechanism (every unit keeps a ledger of what happened), not a claimed domain.

## How it's organized

```
domains/<domain>/<unit>/
  _unit.md      ← what this unit is: type, status, priority, links to real source material
  ledger.md     ← append-only dated log of what happened, in your own words or mine
```

- **domain** = a broad area, nested one level deep: `business`, `personal` (with `career`, `health`, `nutrition`, `relationships`, `sport` underneath), `projects`, `team` (org/team-level capability building, e.g. AI adoption) — add more anytime, nothing about the design assumes this list is final.
- **unit** = a specific thing within that domain: a project, a venture, a person, a workout block, a recipe collection. Units can nest (e.g. `business/egraine/ventures/medex-beauty-clinic`) when one thing has sub-things.
- **_unit.md** front-matter fields:
  - `type`: goal | plan | sprint | milestone | maintenance — pick whatever fits; maintenance = ongoing, no finish line (most relationships, most business operations).
  - `status`: active | blocked | dormant | ended — current lifecycle state.
  - `priority`: high | medium | low — real-world stakes/importance, independent of status.
  - `urgency`: high | medium | low — time-sensitivity, independent of priority (a high-priority project can be low urgency if it can wait; a low-priority project can still be urgent).
  - `disputed`: optional flag (true/absent) — set when a project's record itself is contested or unresolved; independent of status, priority, and urgency.
  - `source`: path(s) to where the real content/data lives (a git repo, a folder of docs, a spreadsheet) — this framework links to it, doesn't duplicate it.
  - `last_updated`: date of the most recent ledger entry.
  - `components`: optional structured block (git/docs/changelog/live-artifact status, each with a verification date) — see `guidelines/tracking-protocol.md`.
- **ledger.md** — short dated entries, newest first, never rewritten, just appended to. This is the history and the "what's the status" answer in one place.

## Guidelines

The working rules — what a tracked project should contain, how it's checked, the Start → Work → Check → Update loop, and git/access hygiene — are now **canonically maintained in the shared ALFA+OMEGA repo** (git-tagged, currently **v2.0**; see `adr/0010-canonical-guidelines-shared-resources-repo.md`): `project-standard.md`, `tracking-protocol.md`, `workflow.md`, `checklists.md`, and `git-and-access.md`. The copies under `guidelines/` here are superseded pointer-stubs — edit the canonical set in ALFA+OMEGA, not here.

Ledger holds itself to the same standard — see `SPEC.md`, `CHANGELOG.md` (currently v0.6), and `ROADMAP.md`.

## The Ledger toolkit — a built, functional extension

What `ROADMAP.md` first listed as future — a scan engine, keyword gap-finding, a live dashboard — is **now built**, and lives in the shared repo at **`ALFA+OMEGA/skillsets/ledger/`** (Python, standard library only — no install, no internet, no Claude required; Claude just runs the same commands when asked). It reads every unit plus the live git/docs of each tracked project into one `ledger-state.json` snapshot, then reports on it:

```
python3 /Users/mklvsky/AI/ALFA+OMEGA/skillsets/ledger/ledger.py audit    # full red/amber/green gap report
python3 …/ledger.py gaps stalling     # filter: urgent | stalling | blocked | drift | nogit | locks | untracked
python3 …/ledger.py dashboard         # build reports/dashboard.html — open it in a browser
python3 …/ledger.py doctor <project>  # a compliance catch-up .md for one project
python3 …/ledger.py stats             # portfolio fun-facts
```

Outputs go to `ALFA+OMEGA/reports/` (human) and `ALFA+OMEGA/tmp/` (json), both git-ignored. **Full usage, config, and how the dashboard works:** `ALFA+OMEGA/skillsets/ledger/README.md`. Scan-engine design and the health/movement model are recorded in `adr/0011-scan-engine-and-state-model.md`.

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

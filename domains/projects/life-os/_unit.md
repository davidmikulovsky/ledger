---
domain: projects
unit: life-os
type: maintenance
status: active
priority: medium
started: 2026-07-14
last_updated: 2026-07-15
source:
  - "this folder (self-referential — life-os tracks itself as a unit too)"
---

# life-os (this framework, tracking itself)

The tracking framework itself, treated as a project with its own progress worth tracking — same pattern as everything else in here, applied reflexively. Lives at the root of the pen drive; this unit just gives it a place in the index so its own backlog (mostly infrastructure/hardening work, not content) doesn't get lost among the domains it tracks.

## Built so far

- Core structure: `domains/<domain>/<unit>/_unit.md` + `ledger.md` pattern, front-matter schema (type/status/priority/source), root `_index.md` rollup.
- Domains scaffolded: business, projects (populated); health, sport, nutrition, relationships, career (empty, ready).
- Seed content: Egraine (parent + 4 sub-ventures, corrected against real source docs — decision log, strategic plan), Jascandi.
- Git-tracked locally on the pen drive since 2026-07-14 (3 commits so far).

## Open backlog for the framework itself

- **Off-drive backup (in progress, decided 2026-07-15):** Option A chosen — a bare git repo over SSH on the existing Coolify VPS (the same box Jascandi runs on), pushed to as a second remote. Purely a backup, no UI. Option B (Gitea/Forgejo via Coolify's one-click deploy, full browsable UI) noted as a future upgrade if the no-UI backup proves limiting — not needed now.
  - **Status: not yet executed.** This needs your action, not mine — it requires SSH access to your VPS, which I don't have and shouldn't be given via chat. I can walk you through the exact commands interactively (you run them, tell me the result, I log it here) whenever you're ready.
- `_index.md` regeneration is currently manual (I rewrite it by hand when asked) — flagged earlier as a later automation step once the unit count grows. Still true, still deferred.
- No domains outside business/projects have any units yet — health, sport, nutrition, relationships, career are all empty. Not a problem, just the honest state: this framework is currently exercised on one life area (business) and one hobby project, not yet on the personal-life domains it was originally designed for.

## Why this unit exists

So "what's left to build in the tracking system itself" has the same clear answer as any other domain, rather than living only in chat history.

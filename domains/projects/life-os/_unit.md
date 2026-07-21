---
domain: projects
unit: life-os
type: maintenance
status: active
priority: medium
started: 2026-07-14
last_updated: 2026-07-21 (migrated to persistent local storage; ADR log established)
source:
  - "this folder (self-referential — tracks itself as a unit too)"
---

# life-os (this framework, tracking itself)

Naming note (2026-07-21): "life-os" is being retired as the framework's public name — see ledger — pending David's pick from proposed alternatives. This unit's folder path/id stays `life-os` for continuity until the rename is finalized everywhere at once, to avoid half-renamed references.

The tracking framework itself, treated as a project with its own progress worth tracking — same pattern as everything else in here, applied reflexively. This unit gives its own backlog (mostly infrastructure work, not content) a place in the index so it doesn't get lost among the domains it tracks.

## Built so far

- Core structure: `domains/<domain>/<unit>/_unit.md` + `ledger.md` pattern, front-matter schema (type/status/priority/source), root `_index.md` rollup.
- Domains scaffolded: business, projects (populated); health, sport, nutrition, relationships, career (empty, ready).
- Seed content: Egraine (parent + 4 sub-ventures, corrected against real source docs — decision log, strategic plan), Jascandi.
- **ADR log established (2026-07-21)** at `adr/` — governance decisions about the framework itself, separate from per-project ledgers. ADR-0001 (read-only boundary on tracked projects — hard rule, see below) and ADR-0002 (local-only storage/hosting) in place.
- **Storage migrated 2026-07-21**: pen drive → persistent local SSD (`/Users/mklvsky/AI/LIFE_OS`). Verified via `git log` diff that all 5 prior commits are byte-identical between old and new location — nothing lost. Pen drive is still connected/available and now serves as an incidental second copy, not the primary.

## Hard rule, now enforced (ADR-0001)

This framework never writes, edits, or otherwise modifies any file in a tracked project's own source location — only reads it. Corrections apply only to this framework's own files. Verified retroactively that this was already true in practice for every past correction (e.g. the Egraine rebuild) before being made an explicit rule. See `adr/0001-read-only-boundary-on-tracked-projects.md` for the full record.

## Open backlog for the framework itself

- **Rebrand, in progress (2026-07-21):** dropping "life tracking" / "life-os" framing in favor of a project-tracking framing that doesn't presuppose scope (apps, design, research, business, lifestyle — anything). Naming options being drafted; not yet finalized or applied to files.
- **Hosting — decided 2026-07-21 (ADR-0002), supersedes the 2026-07-15 GitHub-private plan:** local git only, on persistent storage, no remote. Revisit if an off-device backup need becomes real.
  - Note: the earlier "turn Medex/Egraine's docs folders into git repos, push to GitHub" plan is now in tension with ADR-0001 if read literally — doing that *as part of this framework's operation* would mean this framework modifying those projects' own folders. Treat any future work like that as a separate, explicit, user-directed task on that project — not something this framework initiates on its own.
- `_index.md` regeneration is currently manual (I rewrite it by hand when asked) — flagged earlier as a later automation step once the unit count grows. Still true, still deferred.
- No domains outside business/projects have any units yet — health, sport, nutrition, relationships, career are all empty. Not a problem, just the honest state: this framework is currently exercised on one life area (business) and one hobby project, not yet on the personal-life domains it was originally designed for.

## Why this unit exists

So "what's left to build in the tracking system itself" has the same clear answer as any other domain, rather than living only in chat history.

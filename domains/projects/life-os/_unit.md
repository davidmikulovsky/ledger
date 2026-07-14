---
domain: projects
unit: life-os
type: maintenance
status: active
priority: medium
started: 2026-07-14
last_updated: 2026-07-15 (hosting decision finalized)
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

- **Off-drive backup / source-of-truth hosting — decided 2026-07-15, final (for now).** Landed on **GitHub private** rather than self-hosting, after working through the actual risk tradeoffs:
  - Initial idea (Option A: bare git over SSH on the existing Coolify VPS) turned out not to deliver the isolation it promised — Coolify already runs on that same box for Jascandi, and Coolify itself has a demonstrated critical-RCE track record (5 CVSS-10.0 CVEs in 2025/2026 alone). A bare git repo co-located with Coolify inherits that risk regardless of whether Coolify is used to deploy the git server itself.
  - Option B (Gitea/Forgejo via Coolify) would have added a second layer of DIY-patched CVE surface on top of that (Gitea/Forgejo had their own critical auth-bypass and registry-exposure CVEs in 2026).
  - A genuinely isolated second VPS (no Coolify, just `sshd`+`git`) was the only self-hosted option that actually avoided this, but means new infrastructure to provision, pay for, and patch indefinitely.
  - Verdict: not worth it yet. **GitHub private** for Medex and Egraine's decision logs/task trackers (mirroring how Jascandi already works — GitHub as source of truth, nothing sensitive with its master copy sitting on the self-managed VPS), with 2FA as the one non-negotiable control. Revisit self-hosting **if/when company growth justifies owning dedicated infrastructure** — David's own framing, logged verbatim as the trigger condition.
  - Medex and Egraine's docs folders aren't git repos yet at all (checked 2026-07-14) — turning them into repos and pushing to private GitHub repos is the concrete next step, not yet done.
- `_index.md` regeneration is currently manual (I rewrite it by hand when asked) — flagged earlier as a later automation step once the unit count grows. Still true, still deferred.
- No domains outside business/projects have any units yet — health, sport, nutrition, relationships, career are all empty. Not a problem, just the honest state: this framework is currently exercised on one life area (business) and one hobby project, not yet on the personal-life domains it was originally designed for.

## Why this unit exists

So "what's left to build in the tracking system itself" has the same clear answer as any other domain, rather than living only in chat history.

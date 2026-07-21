---
domain: projects
unit: jascandi
type: maintenance
status: active
priority: low
started: 2026 (v1), v2.1 as of July 2026
last_updated: 2026-07-21 (canonical location confirmed)
source:
  - "/Users/mklvsky/AI/PROJECTS/Jascandi/web (git repo, origin: github.com/davidmikulovsky/jascandi) — confirmed canonical 2026-07-21, working tree clean, HEAD b905b08"
  - "Google Drive: Projects/jascandi-backup-2026-07-21-v2.zip — snapshot backup, David's own copy, not read by Ledger"
components:
  git:
    present: true
    path: "/Users/mklvsky/AI/PROJECTS/Jascandi/web"
    remote: "github.com/davidmikulovsky/jascandi"
    branch: "main"
    head: "b905b08"
    working_tree: "clean"
    verified: "2026-07-21"
    how: "git log/status, direct"
  readme:
    present: true
    verified: "2026-07-21"
    how: "read"
  docs:
    present: true
    location: "docs/ (business: manifesto, operations, services) + technical/ (project/technical: jascandi-reference, networking, changelog, workflow)"
    verified: "2026-07-21"
    how: "read"
  changelog:
    present: true
    location: "technical/changelog.md"
    verified: "2026-07-21"
    how: "read"
  decision_log:
    present: false
    note: "changelog + git history covering this role so far; no separate decision log/ADR exists"
  live_artifact:
    present: true
    url: "https://jascandi.com"
    status: "live"
    verified: "2026-07-21"
    how: "fetched directly"
---

# Jascandi

Creative and branding studio — side project/personal hobby, not a committed business yet. Explicitly optionality-first: might spin up if clients/collaborations appear, might get sold, might get shelved as dormant. Tracked as `maintenance` type rather than a goal with an endpoint, since the whole point is it doesn't need to resolve to anything.

## What it actually is (from source docs)

A multidisciplinary brand/digital studio positioned around client outcomes ("we're launching a company," "our site no longer fits") rather than a menu of services. Four named offers: **origin** (new venture identity), **renewal** (rebrand), **reveal** (launch/product moment), **keep** (ongoing retainer). Fit-before-scope filter for taking on clients — explicitly designed to say no early rather than take bad-fit work.

## Location — resolved (2026-07-21)

Multiple copies existed across the pen drive, `Documents/PROJECTS`, and `Documents/PROJECTS_v0` during the broader project-folder consolidation. David checked all of them directly and confirmed `/Users/mklvsky/AI/PROJECTS/Jascandi/web` is the most recent, git-verified version — working tree clean, `HEAD` at `b905b08`, matches `origin/main`. This is now the single canonical source; other copies are being deleted on David's end, with a snapshot already saved to Google Drive (`Projects/jascandi-backup-2026-07-21-v2.zip`) first. That Drive backup is David's own safety copy — not something Ledger reads from or treats as a source.

## Current state (from README + changelog, as of 2026-07-21)

Landing page (single-file `index.html`, no build step) is live via Coolify + Cloudflare on a VPS, self-hosted fonts, auto-deploying on every push to `main`. **Status per README: "v2.2 — complete as of July 2026."** No known open bugs, per the project's own changelog.

v2.2 (2026-07-14) was a real security fix: the `Dockerfile` had been using `COPY . .`, which meant `docs/`, `technical/`, `README.md`, `LICENSE`, and the `Dockerfile` itself were all reachable over HTTP alongside the actual site — not just internal docs, but the deployment config too. Fixed with an explicit served-files allowlist (`index.html`, `robots.txt`, `assets/`, `fonts/`), a `.dockerignore` backstop, and an `nginx.conf` adding real response security headers (CSP with `frame-ancestors 'none'`, `nosniff`, `Referrer-Policy`, `Permissions-Policy`). Screen-reader pacing (`aria-hidden`) was synced to the visual intro sequence in the same pass. A follow-up commit the same day fixed a build break the security fix had introduced (`.dockerignore` had accidentally excluded `nginx.conf` from the build context itself, not just the served output — Coolify correctly rejected the broken deploy rather than shipping it).

2026-07-21: documentation catch-up pass — added `technical/changelog.md` (plain-language project history, explicitly not a git-log substitute) and `technical/workflow.md` (how to carry a change through build/git/docs without drift), corrected stale "open items" notes in `jascandi-reference.md` that were flagging already-resolved issues (real domain, `og:image` already set), and moved the Switzer font's license text into the repo itself (`licenses/Switzer-FFL.txt`) so it travels with the repo instead of living only in the external `Switzer_Complete/` vendor folder.

## Known cleanup items outside the repo itself

The stray orphan `.git` at the project root — **resolved, confirmed gone 2026-07-21.** `Switzer_Complete/` (full font vendor package) and `versions_archive/` (pre-git dated HTML snapshots) still sit outside `web/`, not deployed, kept for reference only — no urgency there.

## Live verification (2026-07-21)

Fetched `jascandi.com` directly rather than trusting the docs' claim — confirmed live and correct: page loads, title/meta description match ("Selective partnerships only"), OG/Twitter card tags and image present, canonical URL correct, no internal doc paths exposed (the security fix from v2.2 is holding in production).

## Status and priority — reviewed 2026-07-21, per the new vocabulary in `guidelines/project-standard.md`

These are two separate axes, not one combined read, and that distinction resolves what used to be an ambiguous single status:

- **`status: active`** — real, current work is happening: the canonical-location resolution, the v2.2 security fix, and the documentation catch-up pass all happened this week. Whatever else is true about this project, "is anyone touching it right now" has a clean, factual answer, and it's yes.
- **`priority: low`** — set by Ledger, per David's explicit direction to review: not because the project is unfinished or neglected, but because there's no real business or client stakes behind it yet. It's a well-maintained hobby project, and that's a perfectly coherent combination — active *and* low priority, not a contradiction. Was previously invented as `dormant-capable`, a hedge that tried to encode both axes into one field; the real fix was separating them, not finding a better single word.

Priority here is a starting call for David to confirm or correct, per the review step in `guidelines/checklists.md` — not a final judgment.

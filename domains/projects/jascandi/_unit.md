---
domain: projects
unit: jascandi
type: maintenance
status: dormant-capable
priority: low
started: 2026 (v1), v2.1 as of July 2026
last_updated: 2026-07-21 (canonical location confirmed)
source:
  - "/Users/mklvsky/AI/PROJECTS/Jascandi/web (git repo, origin: github.com/davidmikulovsky/jascandi) — confirmed canonical 2026-07-21, working tree clean, HEAD b905b08"
  - "Google Drive: Projects/jascandi-backup-2026-07-21-v2.zip — snapshot backup, David's own copy, not read by Ledger"
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

## Known cleanup items outside the repo itself (not urgent, from the project's own changelog)

A second, separate git repo sits at the project root (`Jascandi/.git`, branch `master`, no remote — the same stray orphan flagged in the 2026-07-21 multi-location git scan). The project's own changelog independently confirms this is a single superseded legacy checkpoint, safe to remove. `Switzer_Complete/` (full font vendor package) and `versions_archive/` (pre-git dated HTML snapshots) sit outside `web/`, not deployed, kept for reference only.

## Is this "active"?

Ambiguous by design, which is fine — it's a hobby/optionality project. Recent commit activity says it's getting attention; the "no clients yet" framing in your description says it's pre-revenue. Marked `dormant-capable` rather than `active` or `paused` so status doesn't force a false read either way — update this field whenever the real situation changes (a client/collab appears, or you consciously shelve it).

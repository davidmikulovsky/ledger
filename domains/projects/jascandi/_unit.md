---
domain: projects
unit: jascandi
type: maintenance
status: dormant-capable
priority: low
started: 2026 (v1), v2.1 as of July 2026
last_updated: 2026-07-14
source:
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/Jascandi/web (git repo)"
---

# Jascandi

Creative and branding studio — side project/personal hobby, not a committed business yet. Explicitly optionality-first: might spin up if clients/collaborations appear, might get sold, might get shelved as dormant. Tracked as `maintenance` type rather than a goal with an endpoint, since the whole point is it doesn't need to resolve to anything.

## What it actually is (from source docs)

A multidisciplinary brand/digital studio positioned around client outcomes ("we're launching a company," "our site no longer fits") rather than a menu of services. Four named offers: **origin** (new venture identity), **renewal** (rebrand), **reveal** (launch/product moment), **keep** (ongoing retainer). Fit-before-scope filter for taking on clients — explicitly designed to say no early rather than take bad-fit work.

## Current state (from git log + README, as of 2026-07-14)

Landing page (single-file `index.html`, no build step) is live via Coolify on a VPS, self-hosted fonts, deployed from the `main` branch. **Status per README: "v2.1 — complete as of July 2026."** Repo is actively maintained — last commit was yesterday (2026-07-13): a docs reorganization splitting business-facing docs (`docs/`: manifesto, operations, services) from technical docs (`technical/`: design/decision history, networking config).

Recent work (last ~10 commits): favicon + apple-touch-icon, SEO basics (robots.txt, og-image, twitter card), manifesto/operations/services docs written, a `?night=` URL param for testing the day/night theme logic, and the v2.1 change itself (which half of the site's founding duality leads by day vs. night).

## Is this "active"?

Ambiguous by design, which is fine — it's a hobby/optionality project. Recent commit activity says it's getting attention; the "no clients yet" framing in your description says it's pre-revenue. Marked `dormant-capable` rather than `active` or `paused` so status doesn't force a false read either way — update this field whenever the real situation changes (a client/collab appears, or you consciously shelve it).

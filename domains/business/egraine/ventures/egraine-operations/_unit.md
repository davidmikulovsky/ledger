---
domain: business
unit: egraine-operations
parent_unit: business/egraine
type: maintenance
status: active
priority: medium
started: unknown — ongoing
last_updated: 2026-07-14
source:
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/egraine/01-Docs"
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/egraine/05-Outputs/egraine-cleanup-and-recommendations.md"
---

# Egraine Operations (parent site, supply & distribution, B2B)

Covers the egraine.com corporate site, its own supply/distribution operations, and the B2B partner program docs — the parent-brand layer, separate from any individual venture.

## Current state (from the site cleanup report, source of most recent activity here)

A cleanup pass removed 48 unused files (~19MB) and fixed several live bugs: a dead script tag causing silent 404s on every page, a dead footer link, a broken image path (case-sensitivity bug that only worked by luck on Mac/Windows filesystems), and a broken image reference from a trailing-space filename.

**Open recommendations from that report, not yet actioned:**
- SEO: every page shares the same generic `<title>Egraine</title>` and empty meta descriptions — needs per-page titles/descriptions.
- Content freshness: `careers.html` lists specific job openings with no posting date — needs confirmation these are still open; `news.html` needs a currency check.
- Structural: decide fate of the removed "Events & Beauty Guides" page (build it or drop permanently); confirm `distribution.html` didn't lose content that was only in the now-deleted `distribution+uriage.html`.
- Performance: several images are 1–3MB unoptimized (biggest single speed win available); stack still runs jQuery 1.11.2 (2014) and old Bootstrap — not urgent, but a known future redesign item.
- Housekeeping: git history on this repo is minimal (2 commits) — recommended committing more granularly going forward.

**Not yet reviewed:** B2B-Distribution docs (partner/affiliate framework, tiered margin structure, partner onboarding, partner brand book) and Brand-Identity docs (voice/visual guide, ESG policy, tagline options) — exist but haven't been summarized into this ledger yet.

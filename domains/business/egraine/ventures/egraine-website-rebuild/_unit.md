---
domain: business
unit: egraine-website-rebuild
parent_unit: business/egraine
type: sprint
status: active
priority: high
urgency: medium
started: 2026-07-08
last_updated: 2026-07-21 (vocabulary v2 — urgency added)
source:
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/egraine/00-Decision-Log/Egraine-Decision-Log.xlsx"
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/egraine/01-Docs"
  - "04-Webpage/New-Build/ (Astro rebuild, not directly inspected in this pass)"
---

# Egraine website rebuild (Pillar 1)

Renamed from "Egraine Operations" — that name undersold what this actually is: the active execution of Strategic Plan Pillar 1 (Website Redesign & Digital Architecture), not general corporate housekeeping. This is a real, in-progress rebuild of egraine.fi, not the older cleanup-only picture this unit previously described.

## Sequence so far

1. **Cleanup pass on the legacy site** (2026-07-08): removed 48 unused files (~19MB), fixed 4 live bugs (a dead script causing silent 404s on every page, a dead footer link, a case-sensitivity image-path bug, a trailing-space filename bug). This is what the earlier version of this unit was built from (`05-Outputs/egraine-cleanup-and-recommendations.md`) — accurate as far as it went, but it's step one of a much bigger rebuild, not the whole picture.
2. **Full rebuild scaffolded in Astro** ("Option B") at `04-Webpage/New-Build/`: 5 pages (Home, About, Distribution, Careers, Contact), design tokens matched to the finalized brand guide (Navy #0F044C, Terracotta #C97C4B). Build verified structurally (served + curled each page) — no visual/screenshot QA done yet (sandbox had no root access for headless-browser tooling).
3. **Several rounds of direct revision** based on your feedback: real hero imagery restored, Careers postings corrected (Sales Rep reverted to the real sourced listing after an invented Cosmetologist posting was wrongly substituted), repetitive CTAs de-duplicated, full legal entity names and sourced partner detail added to Distribution copy, six "Why Partner" subpages built and linked.
4. **A real-photography swap** into the Medex/THANN distribution subpages was tried and reverted same day (2026-07-10) — currently back on placeholder imagery there.

## Open items — real gaps, not yet closed

- **Legal pages** (Privacy Policy, Cookie Policy, Terms & Conditions) are drafted and live but explicitly **not reviewed by a lawyer** — flagged prominently in the pages themselves and here again.
- **Contact form has no real backend** — currently points at a placeholder Formspree endpoint; submissions will silently fail until a real form ID/service is wired up.
- **"How to Become a Partner" page** — backlog, not built. Needs real input on partnership process/benefits/support before drafting.
- **Partner-facing document portal** (price lists, templates, guidelines) — backlog, not scoped. Needs a decision on static downloads vs. gated portal.
- **Careers: Relationship Manager / Community Builder posting** — first draft with no source listing, needs your review of the actual responsibilities/requirements before it's real.
- **`footer-logo.png`** — stray unrelated template asset in the Logos folder ("FUN WEATHER"), not an Egraine mark, safe to delete, not urgent.
- **Template library** (social assets, POS/price list, email signature, certificate, partner pitch deck) — follow-on design project, not started; to be produced by an external designer per the approved Partner Marketing Guidelines doc.

## Not this unit

Social media & content (Pillar 2, not started) and the broader B2B document set (Pillar 3, mostly done — tracked at the parent Egraine unit level) are separate threads, not part of this website rebuild.

## Urgency — proposed 2026-07-21, for your review

`urgency: medium` — real open gaps (unreviewed legal pages, unwired contact form) that block full launch confidence, but no hard external deadline forcing this week. Flagging this as a genuine judgment call rather than an obvious read — could reasonably be `high` if you're targeting a near-term launch date not captured in the sources reviewed. Confirm or correct.

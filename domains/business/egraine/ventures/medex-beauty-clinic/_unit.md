---
domain: business
unit: medex-beauty-clinic
parent_unit: business/egraine
type: sprint
status: active
priority: high
started: 2026-07-10
last_updated: 2026-07-14
source:
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/Medex/01_Decision Log/Decision Log.md"
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/Medex/02_Tasks & Roadmap/Task Tracker.md"
  - "medex.fi (Shopify store, live)"
---

# Medex Beauty Clinic

Physical, client-facing clinic + retail, live Shopify store at medex.fi (Helsinki). Correction from the Egraine Decision Log: this isn't simply "an Egraine venture" in the sense of something Egraine built and owns outright — Medex is a separate operating project, named after Egraine's distribution partnership with Medex Bio Science Cosmetics (Germany), but run as its own business with its own decision log and task tracker. It's also now the physical home for THANN-branded treatments and rituals, since THANN's own spa location was dissolved (see `../thann/_unit.md`). Currently mid-way through a focused SEO/site-hygiene sprint that started 2026-07-10, tracked via a Decision Log (D-001 through D-016 so far) and a Task Tracker (Quick Wins / Strategic Investments / Content Pages / Process). Both source files are the live source of truth — this unit summarizes state, doesn't replace them.

## Current state (as of 2026-07-14, derived from source Task Tracker)

**Done this sprint:** all 7 Quick Wins except QW-2 (homepage meta description partially done — text drafted, waiting on your manual approval/paste in Shopify Admin); all 3 initial Strategic Investments (SI-1 treatment landing pages, SI-2 domain strategy, SI-3 template); all 5 Content Pages (Sustainability, Products Distribution, Ethics & Compliance, Careers, Cookie Policy); SI-8 (theme publish).

**Open / not started:**
- QW-2 — homepage meta description: needs your 1-minute manual paste in Shopify Admin.
- SI-9 — full bilingual translation (Finnish/English, +maybe Swedish) — you're doing this personally, not started.
- SI-4 — reviews/testimonials page with structured data (existing 4.7/5, 59 reviews not surfaced on-site at all).
- SI-5 — informational blog content cadence (blog is currently ~100% promotional).
- SI-6 — audit 50+ zero-inventory active product listings (restock or unpublish).
- SI-7 — decide bilingual approach for rest of store (open question).
- PA-2 — populate Design & Brand folder (waiting on you for guidelines/fonts/colors/spec sheets).

**Needs your action specifically (not a Claude/dev task):**
- Manually publish the "Reformation 15.0.0 (active draft)" theme (id 201006907740) to make the Contact page navy-button fix (D-016) live.
- Configure the medexbeautyclinic.com → medex.fi DNS redirect (D-002) — needs registrar/DNS access outside Shopify.
- Paste the drafted homepage meta description (QW-2).

## Notable technical baseline

PageSpeed (2026-07-10): homepage 68/69 Perf desktop/mobile, 54 Best Practices both — flagged as the weakest spot, likely tied to 5 active app embeds, not yet investigated further.

## Working theme state (see D-011)

Live: "Reformation 15.0.0 (working copy) - July 2026". Active draft for new edits: "Reformation 15.0.0 (active draft)", id 201006907740 (contains the unpublished navy contact-button fix, D-016).

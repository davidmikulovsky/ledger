---
domain: business
unit: egraine
type: maintenance
status: active
priority: high
started: unknown (Oy entity) — strategic reset kicked off 2026-07-08
last_updated: 2026-07-14
source:
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/egraine/00-Decision-Log/Egraine-Decision-Log.xlsx"
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/egraine/01-Docs"
  - "/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/egraine/05-Outputs"
sub_units:
  - ventures/medex-beauty-clinic
  - ventures/thann
  - ventures/eden-eva
  - ventures/skinthea   # DISPUTED — see note below
  - ventures/egraine-website-rebuild
---

# Egraine Oy

Parent entity: Nordic (Finland-based) exclusive distributor of premium cosmetic/skincare brands, and holder of the group's IP and trademarks. Multi-year, open-ended build — the objective is a robust corporation, not a project with an end date.

## The real group structure (per Egraine Decision Log + Strategic Plan, 2026-07-08)

This corrects an earlier version of this unit that treated Medex/Thann/SkinThea as generic "sub-brand ventures" without the actual ownership/relationship model. The real structure:

- **Egraine Oy** — parent. Nordic distributor of cosmetic/skincare brands; holds group IP & trademarks. Exclusive distributor for two manufacturing partners: **Medex Bio Science Cosmetics** (Germany, Handelsregister HRB 208050) and **THANN-Oryza Co., Ltd.** (Bangkok, Thailand, founded 2002, majority-owned by Japan's Rohto Pharmaceutical).
- **Medex Beauty Clinic** (medex.fi) — physical, client-facing clinic. Its name comes from the Medex Bio Science Cosmetics partnership, but it's a separate operating project with its own site/decision log/task tracker (see `ventures/medex-beauty-clinic`). Now also the physical home for THANN-branded treatments and rituals.
- **THANN** (thann.fi) — formerly a standalone day spa; the physical location is dissolved (decision 2026-07-08). Operates online-only now: e-commerce + gift cards. Treatments/rituals are redeemed in person at Medex. Keeps its own distinct visual identity (dark green + matte orange) on thann.fi only — Egraine, as distributor, doesn't reshape THANN's brand.
- **Eden's Eva** (edenseva.com) — dormant venture, newly surfaced from the decision log (not mentioned in your original brief to me). Original site (verkkokauppaedenseva.fi) discontinued; IP retained; a new domain (edenseva.com) was acquired but sits unused, pending a defined use case. Explicitly out of scope for the current 12-month plan — "revisit after Q2."
- **SkinThea** — **disputed.** You described this to me as a future venture. The Decision Log (rows 23–24) instead calls it "a leftover/typo — only Uriage is confirmed" and drops it from the live Distribution page as an "unrealized project." I haven't resolved this either way — see `ventures/skinthea/_unit.md` for both sides. Needs your call.
- **In-clinic treatment brands** — Sunekos, Dermapen, Restylane, Profhilo: used *within* Medex/THANN treatments, explicitly **not** part of Egraine's external distribution business. Not tracked as units.

## Strategy: the 4 pillars (adopted 2026-07-08, from Egraine_Oy_Strategic_Plan)

1. **Website Redesign & Digital Architecture** — rebuild egraine.fi as a clear parent/B2B hub; separate the distributor story from Medex/THANN's consumer-facing sites; decide Eden's Eva's fate.
2. **Social Media & Content Strategy** — from 4 thinly-maintained channels to a focused set with real cadence and per-platform purpose.
3. **B2B Partners & Distribution Network** — real sales materials, a proper inquiry funnel, documented agreements, new partner pipeline.
4. **Brand Voice, Tone & Visual/Verbal Identity** — one coherent brand system, shared foundation with room for Medex/THANN to feel distinct.

## 12-month roadmap

- **Q1 Foundation** (~Jul–Sep 2026): brand voice & visual guide, information architecture, distribution audit, content pillars.
- **Q2 Build** (~Oct–Dec 2026): egraine.fi redesign & launch, medex.fi/thann.fi refresh, partner deck, Eden's Eva decision.
- **Q3 Activate** (~Jan–Mar 2027): social relaunch with content calendar, B2B outreach, first performance check-in.
- **Q4 Scale & Review** (~Apr–Jun 2027): full KPI review, partner network expansion, content optimization, Year 2 planning.

## Status by pillar (as of 2026-07-14, derived from Decision Log)

- **Pillar 4 (Brand Identity) — essentially done for v1.** Brand Voice & Visual Identity Guide v1 approved and live. Full 3-brand color system finalized: Egraine Navy #0F044C + Terracotta #C97C4B; Medex Navy #0F044C + Gold #C2A361; THANN Dark Green #1F3B2C + Matte Orange #C1651B. Logo recolored to match. Taglines finalized for all three brands + B2B CTA.
- **Pillar 3 (B2B & Distribution) — v1 docs complete, all approved and live:** Shipping & Delivery Framework, Partner Onboarding & Training Program, Partner Marketing Guidelines & Brand Book, Tiered Margin Structure (Starter/Growth/Premier), Egraine ESG & Sustainability Policy, and a Partner/Influencer/Affiliate Collaboration Framework (kept internal-only on the site, one contact-page line). Open: a "How to Become a Partner" page is backlog/not built; a partner document portal is backlog/not scoped; template library itself (social, POS, email sig, deck) is a follow-on design project not yet started.
- **Pillar 1 (Website) — in progress, substantial rebuild underway.** Legacy egraine.fi cleaned up (48 files removed, 4 live bugs fixed — see `ventures/egraine-website-rebuild`), then a full rebuild scaffolded in Astro (Option B) with 5 pages (Home/About/Distribution/Careers/Contact) plus 6 "why partner" subpages. Two real gaps still open: legal pages (Privacy/Cookie/Terms) are drafted but explicitly **not lawyer-reviewed**; the contact form is built but **not connected to a real backend** (placeholder Formspree endpoint). A real-photography swap was tried and reverted same day (2026-07-10) — placeholders still in place on the Medex/THANN distribution subpages.
- **Pillar 2 (Social Media & Content) — not started.** No decision-log activity yet.

## Open decisions needing you specifically

- **SkinThea** — real or dropped? (see disputed note above)
- **Eden's Eva** — park with a holding page, or scope a relaunch? Plan says revisit after Q2.
- Two Careers postings need your review: Sales Representative (sourced from a real prior listing) and Relationship Manager/Community Builder (first draft, no source listing).
- Legal pages need a qualified Finnish/EU lawyer before anything goes live.
- Contact form needs a real form-backend ID before submissions will work.
- `footer-logo.png` is a stray unrelated template asset ("FUN WEATHER") sitting in the Logos folder — flagged for removal, not urgent.

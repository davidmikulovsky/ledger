---
domain: business
unit: egraine
role: parent
type: maintenance
status: active
priority: high
urgency: medium
started: unknown (Oy entity) — strategic reset kicked off 2026-07-08
last_updated: 2026-07-23 (ADR-0012 tier conversion — eden-eva/skinthea moved from members: to mentions:, their standalone unit files retired)
source:
  - "/Users/mklvsky/AI/PROJECTS/Egraine (git repo, remote github.com/davidmikulovsky/egraine, branch main) — canonical"
  - "Superseded: /Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/egraine/* — per the project's own README this is now backup-only; caused a real git divergence on 2026-07-14, merged back 2026-07-22"
members:
  - business/medex-beauty-clinic
  - business/thann
  # egraine-website-rebuild deliberately excluded — not a family member, see redundancy note below
mentions:
  - "eden-eva — dormant venture, no real folder or repo; original site (verkkokauppaedenseva.fi) discontinued, IP retained, unused domain (edenseva.com) acquired; revisit after Q2 per strategic plan. Converted from a full unit 2026-07-23 (ADR-0012 Tier 2)."
  - "skinthea — real venture idea, deliberately hibernated, no real folder or repo; no third-party brand partner named, resource-constrained rather than dead; optional objective, not on current roadmap. Converted from a full unit 2026-07-23 (ADR-0012 Tier 2)."
components:
  git:
    present: true
    path: "/Users/mklvsky/AI/PROJECTS/Egraine"
    remote: "github.com/davidmikulovsky/egraine"
    branch: "main"
    working_tree: "clean, in sync with origin/main (`git status --short --branch` shows `main...origin/main` with no ahead/behind). The live .git/index.lock found at audit time is gone — re-verified directly this session, not just re-claimed."
    verified: "2026-07-23 (audit) + 2026-07-23 same-day follow-up (re-verified)"
    how: "ran git log/status/update-index directly via device bridge, twice same day"
  readme:
    present: true
    verified: "2026-07-23"
    how: "read"
  docs:
    present: true
    location: "01-Docs/ (Strategy-Plans, Website, Social-Content, B2B-Distribution, Brand-Identity)"
    verified: "2026-07-23"
    how: "read (directory listing + README)"
  decision_log:
    present: true
    location: "00-Decision-Log/Egraine-Decision-Log.md"
    verified: "2026-07-23"
    how: "read directly — migrated 2026-07-23 from the old .xlsx (now archived at 00-Decision-Log/Archive/), newest-first, 60 entries reviewed down through #36"
  live_artifact:
    present: true
    url: "https://egraine.fi"
    status: "DOWN — SSL certificate error (hostname mismatch), from a Coolify 3.x→4.x upgrade on its Hostinger VPS per the project's own README. Confirmed independently this session by fetching the URL directly, not just taken from the README's word."
    verified: "2026-07-23"
    how: "fetched directly — certificate verify failed, hostname mismatch for egraine.fi"
---

# Egraine Oy

Parent entity: Nordic (Finland-based) exclusive distributor of premium cosmetic/skincare brands, and holder of the group's IP and trademarks. Multi-year, open-ended build — the objective is a robust corporation, not a project with an end date.

## Field migration — 2026-07-23 (ADR-0012)

`sub_units:` retired in favor of `role: parent` + `members:` (a rollup list, not ownership — matches what `ledger.py` already reads as `parent` on the child side). This is a field-name fix only, not a folder move — the child units still physically sit under `ventures/` in this tree; whether to also promote them to flat top-level units is a separate, deliberately deferred decision (see "Open decisions" below). `egraine-website-rebuild` was dropped from the list entirely — it isn't a family member, it's Egraine's own internal Pillar 1 tracking (see the redundancy note further down).

## Tier conversion — 2026-07-23, later same day (ADR-0012)

Per David's explicit approval, Eden's Eva and SkinThea are converted from full Tier-1 units to `mentions:` entries. Neither has ever had real folder or repo activity of its own — both exist only as entries in the Egraine Decision Log — so a standalone `_unit.md`/`ledger.md` pair was overhead without upside; this is exactly the "children's children / orphans" case ADR-0012 designed the `mentions:` tier for. Their standalone unit files (`ventures/eden-eva/_unit.md`, `ventures/eden-eva/ledger.md`, `ventures/skinthea/_unit.md`, `ventures/skinthea/ledger.md`) have been moved to `LEDGER/_to_delete/` rather than deleted outright (the device bridge can move but not delete) — their full history is preserved there and also summarized in the `mentions:` entries above and in this unit's "real group structure" section below. David can delete that folder natively whenever convenient. Nothing about either venture's actual status changed — both are exactly as dormant/hibernated as before, this only changes how Ledger represents them.

## Full audit — 2026-07-23

Ledger's own record of this unit had drifted significantly behind the real project — this unit's `ledger.md` hadn't been touched since 2026-07-15, while the project's own decision log has ~45 further entries running through today. Findings, verified vs claimed kept explicit per `tracking-protocol.md`:

- **Source was stale (verified).** `source:` pointed at the pen-drive Egraine spreadsheet/docs paths. The project's own README now explicitly documents that copy as backup-only (it caused a real git divergence on 2026-07-14, merged back into the canonical copy on 2026-07-22) and names `/Users/mklvsky/AI/PROJECTS/Egraine` as canonical. Repointed.
- **Decision log migrated (verified).** `Egraine-Decision-Log.xlsx` is retired and archived; `Egraine-Decision-Log.md` is now the sole canonical record, newest-first. Read directly this session.
- **Live site is down (verified independently, not just claimed).** egraine.fi returns a certificate hostname-mismatch error — confirmed by fetching it directly this session, matching what the project's own README already says (Coolify 3.x→4.x upgrade broke it). Nothing in Ledger reflected this until now. A full Astro rebuild (`04-Webpage/Site/`) is underway to replace the broken live site rather than repair it, with an 8-phase cutover plan drafted (`01-Docs/Website/Cutover-Execution-Plan-v1.md`) but not yet executed — the new site isn't live anywhere yet.
- **A live git lock is present** (`.git/index.lock`, 0 bytes) as of this check — per the git-lock policy this blocks the next commit if it's not stale. Left alone (own-repo write requires David's go-ahead), but worth clearing once confirmed no git process is running.
- **Group model still not promoted.** `sub_units:` nesting is unchanged from the pre-ADR-0007 convention (flat units + `parent:`/`portfolio_members:` links) — a known, still-open Phase 2 item, not something this audit fixed.
- **Worth a look, not resolved here:** the real website-rebuild work (Astro site, mobile-nav fixes, SEO fixes, the cutover plan) now appears to live directly inside this repo's `04-Webpage/Site/`, not in a separate project. Whether the `egraine-website-rebuild` sub-unit is still tracking something distinct, or has effectively merged into Egraine's own repo, wasn't checked this pass (out of scope for auditing Egraine itself) — worth a `report egraine-website-rebuild full` to reconcile.

Everything else checked out: git remote/branch confirmed, working tree clean and in sync with origin (aside from the lock above), README is current and unusually thorough about its own compliance state (it documents the exact framework this Ledger installation uses, its canonical-copy rule, and a real resolved multi-copy divergence incident).

## Follow-up verification — 2026-07-23, later same day

David ran a separate Cowork session directly inside the Egraine repo and sent over a proposal document with further findings. Re-verified independently rather than taken on trust, since Ledger's own read-only boundary means it can check but not rely on another session's say-so:

- **Git lock: confirmed cleared.** Re-ran `git status`/`git update-index --refresh` directly — clean, `main...origin/main` with no ahead/behind, no lock files in `.git/`. The proposal's claim that it was moved to `_to_delete/git-index.lock.stale-2026-07-23` checks out — that file is there.
- **New finding, confirmed:** `_to_delete/` in the Egraine repo has accumulated stale lock files from past device-bridge sessions — 81 of them by direct count (the proposal estimated "70+"), harmless where they sit but worth David clearing natively at some point, since the bridge can only move files there, never delete them.
- **`egraine-website-rebuild` redundancy — flagged, not resolved.** The proposal's read matches what this audit already found: the real website-rebuild work (Astro site, SEO/nav fixes, the cutover plan) all lives inside this repo, with no separate location. Worth a `report egraine-website-rebuild full` to formally confirm and decide whether to retire/merge that unit — not done here, since retiring a unit is a structural call, not a byproduct of auditing its parent.
- **Correction to the proposal's ADR-0007 section — important.** The proposal assumed Thann/Medex might already be promoted to the flat ADR-0007 model (`parent:` link, top-level unit) and asked to match "whatever the real Thann file uses." Checked directly: **neither has been promoted.** Thann's unit still carries `parent_unit: business/egraine` under `domains/business/egraine/ventures/thann/` — the pre-ADR-0007 nested convention, unchanged since Thann's 2026-07-22 source/priority fix (which touched those fields only, not the group-model structure). So the proposed frontmatter swap (`sub_units:` → `portfolio_members:`, adding `parent:`/`relationship:` to each child) isn't a sync-up with something already done elsewhere — applying it now would be the actual ADR-0007 restructuring itself, including a real folder move (`domains/business/egraine/ventures/thann/` → `domains/business/thann/` or similar) for every child unit. That's exactly the kind of restructuring Ledger doesn't do as a side effect of another task — left as a proposal for David's explicit go-ahead, not applied.
- **Urgency recommendation, not applied.** The proposal leans toward `high` given the confirmed outage — consistent with what this audit already flagged as worth a fresh call. Still `medium` here; still David's decision.

## The real group structure (per Egraine Decision Log + Strategic Plan, 2026-07-08)

This corrects an earlier version of this unit that treated Medex/Thann/SkinThea as generic "sub-brand ventures" without the actual ownership/relationship model. The real structure:

- **Egraine Oy** — parent. Nordic distributor of cosmetic/skincare brands; holds group IP & trademarks. Exclusive distributor for two manufacturing partners: **Medex Bio Science Cosmetics** (Germany, Handelsregister HRB 208050) and **THANN-Oryza Co., Ltd.** (Bangkok, Thailand, founded 2002, majority-owned by Japan's Rohto Pharmaceutical).
- **Medex Beauty Clinic** (medex.fi) — physical, client-facing clinic. Its name comes from the Medex Bio Science Cosmetics partnership, but it's a separate operating project with its own site/decision log/task tracker (see `ventures/medex-beauty-clinic`). Now also the physical home for THANN-branded treatments and rituals.
- **THANN** (thann.fi) — formerly a standalone day spa; the physical location is dissolved (decision 2026-07-08). Operates online-only now: e-commerce + gift cards. Treatments/rituals are redeemed in person at Medex. Keeps its own distinct visual identity (dark green + matte orange) on thann.fi only — Egraine, as distributor, doesn't reshape THANN's brand.
- **Eden's Eva** (edenseva.com) — dormant venture, newly surfaced from the decision log (not mentioned in your original brief to me). Original site (verkkokauppaedenseva.fi) discontinued; IP retained; a new domain (edenseva.com) was acquired but sits unused, pending a defined use case. Explicitly out of scope for the current 12-month plan — "revisit after Q2." **Converted to the `mentions:` tier 2026-07-23 (ADR-0012)** — see the `mentions:` field above; its former standalone unit file is preserved in `LEDGER/_to_delete/`.
- **SkinThea** — a real venture idea, deliberately hibernated. Concept formed, no third-party brand named yet, resource-constrained rather than dead. Its brief appearance on the live Distribution page (implying active work) was the actual mistake, since corrected by removal; the idea itself stays as an optional objective, not on the current roadmap. (Uriage, dropped from the same page, is unrelated — a separate real partnership that was paused/discontinued.) **Also converted to the `mentions:` tier 2026-07-23 (ADR-0012)**, same reasoning as Eden's Eva.
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

## Status by pillar (as of 2026-07-23, updated at full audit — see full detail in the audit section above)

- **Pillar 1 (Website) — much further along, but the live site is currently down.** The legacy egraine.fi is broken (SSL error post-Coolify-upgrade); rather than repair it, the plan is to finish and launch the Astro rebuild (`04-Webpage/Site/`) on a fresh instance. Since the 07-14 snapshot: mobile navigation fixed, legacy URL redirects mapped, duplicate H1/meta and generic page titles fixed, sitemap/robots.txt/canonical/OG/JSON-LD added, custom 404 added, unused `playwright` dependency dropped. An 8-phase cutover plan is drafted and ready to execute but hasn't started. Two proposals awaiting David's decision: egraine.fi's SEO relationship to the already-indexed medex.fi/thann.fi, and whether to add Finnish-language coverage.
- **Pillars 2–4** — not re-checked this pass; no reason from the decision log to believe they've moved since 07-14.

## Open decisions needing you specifically

- **Eden's Eva** — park with a holding page, or scope a relaunch? Plan says revisit after Q2.
- Two Careers postings need your review: Sales Representative (sourced from a real prior listing) and Relationship Manager/Community Builder (first draft, no source listing).
- Legal pages need a qualified Finnish/EU lawyer before anything goes live.
- Contact form needs a real form-backend ID before submissions will work.
- `footer-logo.png` is a stray unrelated template asset ("FUN WEATHER") sitting in the Logos folder — flagged for removal, not urgent.
- Two open proposals from the 2026-07-23 SEO strategy doc (egraine.fi/medex.fi/thann.fi SEO relationship; Finnish-language coverage) — awaiting your review per the project's own decision log.
- Whether to physically promote Thann/Medex to flat top-level units (ADR-0012's field rename is done; the folder move is a separate, still-open decision — see "Promoting Thann/Medex — consequences" below for what that would actually involve) and whether to retire/merge `egraine-website-rebuild` into this unit's own Pillar 1 tracking. (The live git lock from the audit is resolved — cleared and re-verified. Eden's Eva/SkinThea's tier conversion is now done — see above.)

## Promoting Thann/Medex — consequences, for your decision

Renaming fields (done) is reversible and costs nothing. Physically promoting Thann and Medex to flat top-level units (`domains/business/thann/`, `domains/business/medex-beauty-clinic/` instead of nested under `domains/business/egraine/ventures/`) is a different kind of change — here's what it would actually involve and change:

- **What moves:** each unit's `_unit.md` and `ledger.md` — a straightforward folder move within Ledger's own tree, not a write to either project's real source. Low mechanical risk on its own.
- **What has to be updated in lockstep:** `_index.md`'s domain column, any relative links between the two ledger.md files and egraine's own, and `egraine/_unit.md`'s `members:` list (still correct either way, since `members:` doesn't encode a path, just a `domain/unit` key — but worth double-checking after any move).
- **What it actually buys:** nothing functional today. `ledger.py` already reads `parent:`/`members:` regardless of physical nesting — `load_units()` walks the entire `domains/` tree via `os.walk`, so a unit under `ventures/` and a unit at the top level are discovered identically. The promotion is purely cosmetic/organizational, not a functionality unlock.
- **What it signals, though:** ADR-0007's whole point was that a family member should be structurally indistinguishable from an independent unit, so it can be spun off (sold, discontinued, re-parented) by dropping a link rather than physically extracting it from a nested tree. Leaving Thann/Medex nested is not wrong today, but it does mean a future spin-off would require the folder move anyway, just done later and possibly under time pressure. Promoting now is "pay the cost early and calmly"; leaving it nested is "defer the cost until it's forced."
- **What doesn't change either way:** what Thann and Medex actually are, their git repos, their own decision logs, their priority/urgency/status. This is purely about where their Ledger-side tracking files live.
- **My read:** low urgency, no functional downside to waiting, but also low cost to do now while it's a calm, non-forced decision rather than a rushed one during an actual spin-off. Your call — I'd lean toward doing it opportunistically rather than urgently.

## Urgency — proposed 2026-07-21, for your review (now with new context)

`urgency: medium` was set by Ledger on 2026-07-21 as a first read — ongoing multi-year build, no single imminent deadline. That was before this session confirmed the production site is actually down. Left at `medium` here rather than changed unilaterally, but flagging plainly: a real production outage is exactly the kind of development that might change your answer — worth a fresh call rather than carrying the old proposal forward untouched.

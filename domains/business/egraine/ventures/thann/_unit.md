---
domain: business
unit: thann
role: child
parent: business/egraine
relationship: distributed-brand
type: maintenance
status: active
priority: high
urgency: medium
disputed: false
started: physical spa dissolved 2026-07-08 (per decision log — see history below)
last_updated: 2026-07-23 (reconciliation, later same day — git lock cleared, urgency drift resolved)
source:
  - "/Users/mklvsky/AI/PROJECTS/Thann (git repo, remote github.com/davidmikulovsky/thann, branch main) — canonical"
  - "thann.fi (live site — directly inspected 2026-07-23)"
components:
  git:
    present: true
    path: "/Users/mklvsky/AI/PROJECTS/Thann"
    remote: "github.com/davidmikulovsky/thann"
    branch: "main"
    working_tree: "clean, 5 ahead of origin/main (David to push when convenient). The blocking `.git/index.lock` is confirmed cleared — verified directly, re-checked this session. A harmless `objects/maintenance.lock` remains (per git-and-access.md, this one never blocks commits) — not urgent."
    verified: "2026-07-23 (re-verified, later same day)"
    how: "ran git log/status directly via device bridge"
  readme:
    present: true
    verified: "2026-07-23"
    how: "read directly — extensive, current through today's Phase 1 execution entry"
  docs:
    present: true
    location: "01-Docs/ (Brand-Identity, Business-Context, Ecommerce, Strategy-Plans, Phase-0-Audit, open-questions.md)"
    verified: "2026-07-23"
    how: "read directly (directory listing + open-questions.md)"
  decision_log:
    present: true
    location: "00-Decision-Log/ledger.md"
    verified: "2026-07-23"
    how: "read directly — dozens of entries, extremely active, most recent dated today"
  live_artifact:
    present: true
    url: "https://thann.fi"
    status: "live, still showing pre-fix content (full physical-shop-and-spa description, address, hours; no schema.org visible) — per the project's own decision log this is confirmed stale, not a live business-model conflict. A full set of fixes (Phorest-widget defer, DaySpa/FAQ schema, 165 product alt-texts, Phase-1 copy/price corrections) is staged on an unpublished draft theme ('Vessel — Working Copy') awaiting David's publish."
    verified: "2026-07-23"
    how: "fetched directly"
---

# THANN

Corrected from an earlier version of this unit, which described THANN as an "e-shop under development." That was wrong — per the Egraine Decision Log (2026-07-08), THANN is an established brand whose physical spa location was dissolved and which now operates purely online.

## What it actually is

THANN-Oryza Co., Ltd. (Bangkok, Thailand, founded 2002, majority-owned since early 2026 by Japan's Rohto Pharmaceutical — cross-verified independently by Thann's own repo, not just Egraine's decision log) is a manufacturing partner brand for which Egraine Oy is the exclusive Nordic distributor — not an Egraine-owned venture built from scratch. On the consumer side: thann.fi operates as an online store for e-commerce and gift cards; the physical spa is discontinued, with a temporary, explicitly-non-permanent phase-out arrangement delivering a subset of services (mostly massages, body scrubs, gift vouchers) via Medex Beauty Clinic staff from the old THANN premises. THANN keeps its own distinct visual identity (dark green #1F3B2C + matte orange #C1651B, Thai wilderness/citrus positioning) on thann.fi only — Egraine, as distributor, deliberately doesn't reshape THANN's brand perception.

## Reconciliation — 2026-07-23, later same day

Two items flagged in this morning's full audit are now resolved, verified directly (not taken on David's word alone):

- **Git lock cleared.** The blocking `.git/index.lock` found earlier is gone — re-checked directly this session. Only the harmless `objects/maintenance.lock` remains, which per `git-and-access.md` doesn't block commits. Repo is clean, 5 commits ahead of `origin/main`, David to push.
- **Urgency drift resolved.** THANN's own README now reads `Urgency: medium (lowered 2026-07-23 per David's own instruction to review once Phase 1 completed — see 01-Docs/open-questions.md item 4)` — matching Ledger's `urgency: medium` exactly. No more mismatch between what Ledger declares and what the project's own record says.

## Full audit — 2026-07-23

This unit had drifted **significantly** behind the real project — Ledger's record here hadn't reflected anything since the 2026-07-22 "full check," while THANN's own repo (`/Users/mklvsky/AI/PROJECTS/Thann`, confirmed to exist and be extensively active) has since run an entire Phase 0 (audit) and most of Phase 1 (brand/copy recovery) of its own Recovery & Revamp Plan, with dozens of decision-log entries. Verified directly this session, not assumed from any prior Ledger note:

- **Source was stale (verified) — now fixed.** `source:` still pointed at the old pen-drive Egraine spreadsheet and a bare "thann.fi (site)" note, never actually repointed to THANN's own repo despite a 2026-07-22 ledger entry claiming this had been done. Repointed for real this time, to the canonical git repo.
- **Disputed flag — resolved at the source, cleared.** The 2026-07-22 conflict (decision log said the physical spa was dissolved; the live site described a full operating shop+spa) is explicitly resolved in THANN's own decision log and `open-questions.md`: David confirmed directly which is true (spa discontinued, services moved to Medex as a temporary phase-out), and the live site's contrary content is confirmed **stale copy awaiting a fix**, not a genuine unresolved conflict. Clearing `disputed` reflects that resolution, verified directly against the project's own record — not a Ledger guess.
- **Massive real progress not previously reflected here, now caught up:** Phase 0 content/SEO/PageSpeed audits completed; a draft Shopify theme ("Vessel — Working Copy") has the Phorest booking-widget defer fix, DaySpa/FAQPage JSON-LD, and alt text on all 165 product images already applied and verified — all staged, none published yet (that step is explicitly David's call); Phase 1 copy/price fixes executed against the approved brand decisions (canonical hours, price formats, the Stress Relief €165 correction, the Medex booking-handoff sentence) across several theme files and two live Shopify Page/Product writes, all verified post-write. A family-declaration block (`Role: child`, `Parent: Egraine`, `Relationship: distributed-brand`) was independently added to THANN's own README on the project side — consistent with, and predating Ledger seeing, this session's own ADR-0012 field migration.
- **Live site check (2026-07-23, fetched directly):** thann.fi still shows the old physical-shop-and-spa content — consistent with the project's own account that the fixes are staged but not yet published. Not a new problem, just confirms the "staged, not live" state is accurate as of today.
- **No guidelines copy present** in THANN's own repo (no `project-standard.md`/`workflow.md`) — consistent with the same gap already flagged across the whole Egraine family; the `GUIDELINES-STALE` check still can't fire for this unit. Known, not new.
- **No `CHANGELOG.md`** at the repo root — not a defect on its own (project-standard.md treats missing docs on a still-growing project as normal, git being the one hard requirement), but worth noting given how much real history now lives only in the decision log.

## Compliance pass (audit depth)

- `type: maintenance` still fits — an ongoing sub-brand with no fixed end date, cycling through real work in bursts (matches `workflow.md`'s description of a maintenance unit).
- `status`/`priority`/`urgency`/`disputed` are now internally consistent (active + high + medium + not disputed — no contradiction), and now also consistent with the project's own self-declaration (no drift).
- Structure otherwise matches what `project-standard.md` expects at this unit's maturity: git (hard requirement) present and healthy, README current, real docs, a genuinely active decision log. The only real gap is the missing local guidelines copy, already tracked as a known, accepted limitation across the whole family (not something to fix here without David's separate go-ahead, per ADR-0001).

## Open, still needing David specifically

- Whether/when to publish the "Vessel — Working Copy" draft theme, which already has the PageSpeed/SEO fixes and Phase 1 copy corrections staged and verified.
- The two items THANN's own execution brief explicitly deferred to David: hiding the FI/SV language switchers, and any store-wide money-format setting change.
- 5 commits sitting ahead of `origin/main` — push whenever convenient.
- The long-term strategic fork (rebrand-and-relocate vs. permanent online-only) — deliberately deferred by David himself, tracked but not blocking.

## What would sharpen this unit further

Now largely resolved by this audit and reconciliation — the main open item is simply staying current with THANN's own decision log going forward, since it moves fast.

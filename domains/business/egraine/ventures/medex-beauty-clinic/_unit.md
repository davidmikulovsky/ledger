---
domain: business
unit: medex-beauty-clinic
role: child
parent: business/egraine
relationship: distributed-brand
type: sprint
status: active
priority: high
urgency: medium
started: 2026-07-10
last_updated: 2026-07-23 (reconciliation, later same day — urgency updated to match source, git locks cleared)
source:
  - "/Users/mklvsky/AI/PROJECTS/Medex (git repo, remote github.com/davidmikulovsky/medex, branch main) — canonical, confirmed by direct comparison against 3 other candidate folders"
  - "medex.fi (Shopify store, live)"
components:
  git:
    present: true
    path: "/Users/mklvsky/AI/PROJECTS/Medex"
    remote: "github.com/davidmikulovsky/medex"
    branch: "main"
    working_tree: "clean, 0 ahead / 0 behind origin/main. Both the `.git/index.lock` and `objects/maintenance.lock` found in the earlier audit are confirmed cleared — re-checked directly, no locks remain."
    verified: "2026-07-23 (re-verified, later same day)"
    how: "ran git log/status directly via device bridge"
  readme:
    present: true
    verified: "2026-07-23"
    how: "read directly — explicitly self-declares this folder as the canonical copy"
  docs:
    present: true
    location: "01-Tasks-Roadmap/ (Task-Tracker.md, Phase-1-Execution-Brief.md), 02-SEO-Marketing/, 03-Design-Brand/ (mostly MISSING-asset placeholders, flagged by the project itself), 05-Reference-Research/, 06-Content-Drafts/"
    verified: "2026-07-23"
    how: "read directly (directory listing + Task-Tracker.md + CLAUDE.md)"
  decision_log:
    present: true
    location: "00-Decision-Log/Medex-Decision-Log.md"
    verified: "2026-07-23"
    how: "read directly — 242 lines, D-001 through D-021, newest entry dated today"
  live_artifact:
    present: true
    url: "https://medex.fi"
    status: "live. Confirmed live: hours/phone on the Contact page and footer nav match the approved canonical values. **Discrepancy found, not yet reconciled:** the homepage's separate \"Customer Support\" hours banner still reads the old placeholder \"Mon - Sat, 10am - 6pm\" on two independent direct fetches this session — this contradicts the project's own decision log (D-020/D-021), which states this exact banner was corrected to the canonical hours and confirmed live. Currency selector (EUR + 6 others) also still shows CZK/DKK/HUF/PLN/RON/SEK all enabled, consistent with D-021's correction that these should stay (not a discrepancy — matches source)."
    verified: "2026-07-23"
    how: "fetched directly, twice, independently"
---

# Medex Beauty Clinic

Physical, client-facing clinic + retail, live Shopify store at medex.fi (Stockmann, 7th floor, Aleksanterinkatu 52, Helsinki). Run by David Mikulovský and Dominika Jamborová under **Egraine Oy** (parent — Nordic distributor for Medex Bio Science Cosmetics and THANN). Distinct from *Medex Bio Science Cosmetics*, the independent product brand Egraine distributes — this unit is the family's own clinic venture. Also the temporary physical home for THANN's phased-out spa services (gift-voucher redemptions, some massages/scrubs) — see `../thann/_unit.md`.

## Reconciliation — 2026-07-23, later same day

Per David's explicit instruction, two items from this morning's full audit are now resolved:

- **Urgency updated in Ledger to `medium`**, matching the project's own record — David lowered it once Phase 1 closed, and Ledger was carrying the stale pre-Phase-1 `high`. No more drift between what Ledger declares and what Medex's own README/decision log say.
- **Git locks cleared.** Both the `.git/index.lock` and `objects/maintenance.lock` found in the earlier audit are confirmed gone — re-checked directly, repo is clean and in sync with `origin/main`.

Not addressed in this pass, still open (see below): the homepage hours-banner discrepancy, and the `type: sprint` vs. `maintenance` question.

## Source-of-truth reconciliation — 2026-07-23

David linked four candidate folders and asked for a direct comparison before auditing:

- `/Users/mklvsky/Documents/PROJECTS/Medex`, `/Users/mklvsky/Documents/PROJECTS_v0/Medex`, and `/Volumes/SAMSUNG 128 PEN-DRIVE/PROJECTS/Medex` — **byte-identical to each other** (README and decision log both match exactly via md5). No git. Old naming convention (`01_Decision Log`, `02_Tasks & Roadmap`). These are backup/duplicate copies of the same pre-git snapshot from around 2026-07-10, not independent work.
- `/Users/mklvsky/AI/PROJECTS/Medex` — git-initialized 2026-07-23, clean and in sync with `origin/main`, an active decision log running through today, the new numbered-pillar naming convention, and its own README explicitly self-declares: *"Canonical copy: `/Users/mklvsky/AI/PROJECTS/Medex` on David's Mac — the only copy that should be edited or committed to."* Confirmed as source of truth; `source:` repointed here (was still pointing at the old pen-drive paths, never corrected until now).

## Full audit — 2026-07-23

This unit's Ledger record was almost entirely stale — everything below "Current state (as of 2026-07-14)" in the previous version of this file predates a huge amount of real work:

- **Source was wrong (verified) — now fixed.** Pointed at pen-drive paths for a project that has since moved into its own proper git repo.
- **Massive real progress not previously reflected:** the original SEO-audit-driven sprint (Quick Wins, Strategic Investments, Content Pages — see Task Tracker) closed out through mid-July, then a full **Phase 1 "Truth & Consistency Pass"** ran 2026-07-23: canonical hours/price-format/phone/naming fixes applied across the live theme, a theme-drift issue found and resolved (a content block that would have been silently deleted had the wrong working copy been published), a markets/currency investigation, and the new v2 theme **published live** the same day. Git, decision log, and task tracker are all current through today.
- **A real discrepancy found on live re-check, not previously known:** the project's own decision log states the homepage's "Customer Support" hours banner was corrected and confirmed live (D-020, reconfirmed in D-021's final audit). Fetching medex.fi directly this session, twice, independently, still shows the **old placeholder text** ("Mon - Sat, 10am - 6pm") in that banner — contradicting the project's own "confirmed live" claim. This may be a different theme section than the one D-020 actually touched (the Contact page's own hours are confirmed correct), or it may be a genuine gap in the project's own verification. Flagged here rather than adjudicated — this is exactly the kind of claimed-vs-verified gap `tracking-protocol.md` exists to catch, and it isn't Ledger's call to resolve inside Medex's own theme.
- **Type — compliance flag, not changed here.** This unit is typed `sprint`, which per `workflow.md` implies a real end. In practice this project has now run two open-ended "phases" back to back (the original sprint, then Phase 1) with a Phase 2 backlog already forming — the same ongoing, cyclical shape Thann's unit has, which is typed `maintenance`. Worth considering the same re-type here, but that's a judgment call for you, not applied unilaterally.

## Compliance pass (audit depth)

- `status: active` — confirmed, matches.
- `priority`/`urgency` — internally consistent with each other, and now consistent with the project's own source (no drift remaining).
- `type: sprint` vs. actual shape — still flagged above, still not resolved.
- Structure otherwise matches `project-standard.md` for this unit's maturity: git (hard requirement) present and healthy, README current and unusually explicit about its own canonical status, active decision log. `03-Design-Brand/` is intentionally sparse (MISSING-asset placeholders) — the project's own docs already flag this as pending brand assets from David, not a gap Ledger needs to raise separately.
- No local guidelines copy (`project-standard.md`/`workflow.md`) in this repo either — same known, accepted, family-wide limitation as Thann and Egraine.

## Current state (superseding the 2026-07-14 snapshot below)

**Phase 1 (Truth & Consistency Pass) — closed 2026-07-23.** All Definition-of-Done items confirmed live per the project's own final audit: unified hours (with the live-banner caveat above), Belkyra price range corrected, phone format unified, naming/nav corrected, currency selector reconciled (no removals needed — Medex ships to all the countries currently enabled), craft/grammar fixes applied. New theme "Reformation v2 - working copy" is now the published live theme.

**Phase 2 backlog (not started, explicitly deferred):** Sweden market/region + currency-display strategy (needs a real shipping/carrier/tax decision, not a safe default); a disabled Contact-page map-pin caption typo (invisible on live site, low priority); SI-4 (reviews/testimonials structured data), SI-5 (blog content cadence), SI-6 (zero-inventory listing audit), SI-7 (broader bilingual approach), SI-9 (full bilingual translation — David doing personally); PA-2 (populate Design & Brand folder — waiting on David for guidelines/fonts/colors).

## Open, needing David specifically

- **The live homepage hours-banner discrepancy** (see Full audit above) — worth a direct look at medex.fi to confirm whether this is a real gap in Medex's own Phase-1 close-out or a different section than what was actually fixed.
- Whether `type: sprint` should become `maintenance`, matching Thann's pattern, given the now-established cyclical Phase 1 → Phase 2 shape.
- Phase 2 planning itself — Sweden market strategy and the rest of the backlog above.

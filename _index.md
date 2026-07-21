# Ledger — index

Rolled-up view across every domain. Regenerate by asking any time ("update the index") — it's derived from each unit's `_unit.md`, not maintained separately by hand.

_Last generated: 2026-07-21 (v7 — guideline system + versioning, ADR-0003; Jascandi canonical location + live verification)_

| Domain | Unit | Type | Status | Priority | Last updated |
|---|---|---|---|---|---|
| business | egraine (parent, 4-pillar strategy) | maintenance | active | high | 2026-07-14 |
| business | egraine / medex-beauty-clinic | sprint | active | high | 2026-07-14 |
| business | egraine / thann | maintenance | active | medium | 2026-07-14 |
| business | egraine / eden-eva | goal | dormant | low | 2026-07-14 |
| business | egraine / skinthea | goal | hibernated | optional | 2026-07-15 |
| business | egraine / egraine-website-rebuild | sprint | active | high | 2026-07-14 |
| projects | jascandi | maintenance | dormant-capable | low | 2026-07-21 |
| projects | ledger (this framework, v0.2) | maintenance | active | medium | 2026-07-21 |
| health | — | — | no units yet | — | — |
| sport | — | — | no units yet | — | — |
| nutrition | — | — | no units yet | — | — |
| relationships | — | — | no units yet | — | — |
| career | — | — | no units yet | — | — |

## Governance

Decisions about Ledger itself live in `adr/` as ADRs (currently 3 — read-only boundary, local hosting, project-standard/tracking-protocol). How Ledger operates day to day is now written down in `guidelines/` (`project-standard.md`, `tracking-protocol.md`, `workflow.md`), and Ledger's own spec/version history is in `SPEC.md` / `CHANGELOG.md` (currently v0.2) / `ROADMAP.md`.

## Needs your call directly (not just execution)

- **Medex / Egraine hosting:** the pattern of "turn their docs folders into git repos, push to GitHub" is still logged as a want, but per ADR-0001 it can't happen as something Ledger initiates on its own — it would mean Ledger modifying those projects' own folders. Whenever you want this done, ask for it as its own explicit task, separate from tracking.
- **Eden's Eva** — dormant asset (edenseva.com), park with a holding page or scope a relaunch — deferred to "revisit after Q2" per the strategic plan, so no action needed yet, just don't forget it.
- **Medex:** publish the "active draft" Shopify theme to make the navy contact-button fix live; paste the drafted homepage meta description; configure the medexbeautyclinic.com DNS redirect.
- **Egraine website rebuild:** legal pages (Privacy/Cookie/Terms) need a real lawyer review before they're trustworthy; contact form needs a real backend (currently a placeholder endpoint); Relationship Manager job posting needs your review (first draft, no source listing).
- **Thann:** site itself (thann.fi) hasn't actually been inspected yet — only its business model is known from the decision log.

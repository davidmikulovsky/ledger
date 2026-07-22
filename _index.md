# Ledger — index

Rolled-up view across every domain. Regenerate by asking any time ("update the index") — it's derived from each unit's `_unit.md`, not maintained separately by hand.

_Last generated: 2026-07-22 (v0.6 Phase 0 — governance ADRs 0007–0011 accepted, guidelines consolidated into ALFA+OMEGA)_

| Domain | Unit | Type | Status | Priority | Urgency | Last updated |
|---|---|---|---|---|---|---|
| business | egraine (parent, 4-pillar strategy) | maintenance | active | high | medium | 2026-07-21 |
| business | egraine / medex-beauty-clinic | sprint | active | high | high | 2026-07-21 |
| business | egraine / thann | maintenance | active | medium | low | 2026-07-21 |
| business | egraine / eden-eva | goal | dormant | low | low | 2026-07-21 |
| business | egraine / skinthea | goal | dormant | low | low | 2026-07-21 |
| business | egraine / egraine-website-rebuild | sprint | active | high | medium | 2026-07-21 |
| projects | jascandi | maintenance | active | low | low | 2026-07-21 |
| projects | ledger (this framework, v0.6) | maintenance | active | medium | medium | 2026-07-22 |
| team | ai-lab (personal & team AI adoption) | maintenance | active | high (provisional) | medium | 2026-07-22 |
| personal / career | — | — | no units yet | — | — | — |
| personal / health | — | — | no units yet | — | — | — |
| personal / nutrition | — | — | no units yet | — | — | — |
| personal / relationships | — | — | no units yet | — | — | — |
| personal / sport | — | — | no units yet | — | — | — |

Urgency values marked "proposed" in each unit's own `_unit.md` are Ledger's first read, not yet confirmed by David — same review pattern as priority.

## Governance

Decisions about Ledger itself live in `adr/` as ADRs (currently 11 — read-only boundary, local hosting, project-standard/tracking-protocol, status/priority vocabulary v1, domain restructure + vocabulary v2, ledger admin/reporting skill design, group representation & spin-off model, child-safety write boundary, git-lock & folder-access policy, canonical guidelines/shared-resources repo, scan engine & state model). How Ledger operates day to day is defined in the four guideline documents, now canonically maintained in the shared **ALFA+OMEGA** git repo (ADR-0010) — `project-standard.md` (including the canonical `status`/`priority`/`urgency` vocabulary), `tracking-protocol.md`, `workflow.md`, `checklists.md`; the copies under `guidelines/` here are superseded pointer stubs. Ledger's own spec/version history is in `SPEC.md` / `CHANGELOG.md` (currently v0.6) / `ROADMAP.md`.

## Needs your call directly (not just execution)

- **Urgency values across every unit** are Ledger's proposed first read (see each `_unit.md`'s "Urgency — proposed" section) — confirm or correct, same as priority was in v0.3.
- **Medex / Egraine hosting:** the pattern of "turn their docs folders into git repos, push to GitHub" is still logged as a want, but per ADR-0001 it can't happen as something Ledger initiates on its own — it would mean Ledger modifying those projects' own folders. Whenever you want this done, ask for it as its own explicit task, separate from tracking.
- **Eden's Eva** — dormant asset (edenseva.com), park with a holding page or scope a relaunch — deferred to "revisit after Q2" per the strategic plan, so no action needed yet, just don't forget it.
- **Medex:** publish the "active draft" Shopify theme to make the navy contact-button fix live; paste the drafted homepage meta description; configure the medexbeautyclinic.com DNS redirect.
- **Egraine website rebuild:** legal pages (Privacy/Cookie/Terms) need a real lawyer review before they're trustworthy; contact form needs a real backend (currently a placeholder endpoint); Relationship Manager job posting needs your review (first draft, no source listing).
- **Thann:** site itself (thann.fi) hasn't actually been inspected yet — only its business model is known from the decision log.

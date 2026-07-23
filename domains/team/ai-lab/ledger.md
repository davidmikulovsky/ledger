# AI-LAB — ledger

Newest first.

---
**2026-07-23 (reconciliation, second pass)** — The first pass set `priority: medium` in Ledger, but that created a real `DRIFT` flag against AI-LAB's own README, which still declares `priority: high (provisional...)`. Per David's instruction, Ledger now inherits the project's own declared values instead: `priority: high`, `urgency: medium` (unchanged) — both taken directly from the README. Drift cleared.

---
**2026-07-23 (reconciliation)** — Per David's instruction: `priority` cleaned from `high (provisional — team efficiency + rollout initiative)` (prose embedded in the field, not a valid enum value) to a clean `medium`; `urgency` confirmed `medium`, unchanged. Git re-verified: the single unstaged edit flagged in the 07-22 check is now committed (`HEAD` moved a8cbf95 → c8a4613), no locks present, working tree clean.

---
**2026-07-22** — New unit created in Ledger, in a new `team` domain (David's explicit choice, over folding this into `personal` or splitting it into two units — this project is squarely about team/org capability, distinct from individual life domains). Synced from AI-LAB's own real source, read directly: `README.md`, `CHECKLIST.md`, `SETUP.md`, `technical/changelog.md`, `technical/decision-log.md`, git log/status. Confirmed the project's own synced `docs/guidelines/` matches Ledger's current v0.4 vocabulary exactly (status/priority/urgency as three independent axes) — this project was built to follow Ledger's principles from day one, verified directly rather than taken on the project's own word for it.

Real state as of this entry: project created 2026-07-22 (corrected model-selection report → 4-phase curriculum + team rollout plan), git initialized same day (4 commits, no remote yet), Phase 1's local Mac track underway (K.1-K.2 done), core Phase 1 lessons and Phases 2-4 not yet started (though fully detailed). See `_unit.md` for full current-state breakdown.

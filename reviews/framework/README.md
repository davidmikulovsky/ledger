# Framework reviews

Dated snapshots of Ledger's own health and the plans that came out of them. The point of keeping them here (rather than only in chat) is **comparison over time**: when the next evaluation runs, drop it in alongside the previous one, diff the two, and you can see plainly what drifted, what got fixed, and what initiative drove each round of change — i.e. every decision traces back to the real gap it was correcting.

## Contents

- `2026-07-22-framework-evaluation.md` — first full framework audit (at v0.5). Rated design vs. data-fidelity vs. enforceability; found the Thann declared-vs-reality drift, three untracked projects, Medex's missing git, systemic git-lock cruft, guideline-copy drift risk, and the parent/child safety gap.
- `2026-07-22-v0.6-rollout-plan.md` — the plan that answered that audit: one scan-engine spine + five thin readers (dashboard, gap keywords, weekly checkup, catch-up reports, project→Ledger pull), five ADRs to ratify (0007–0011), six phases. Decisions locked: linked/spin-off-ready group model, simple-static dashboard first, weekly checkup, start with Phase 0+1.

## Convention

Filename: `YYYY-MM-DD-<kind>.md` where kind is `framework-evaluation` or a plan/decision name. Newest work references the prior evaluation it's responding to, so the chain of "gap → decision → fix" stays legible.

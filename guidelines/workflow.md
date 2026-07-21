# Workflow

*The working loop a tracked project moves through. A recommended default shape, not a fixed process — adapt it per project, per the notes below. Companion documents: `project-standard.md` (what a project should contain), `tracking-protocol.md` (how a tracker checks it), `checklists.md` (concrete steps per stage).*

## The loop

```
        ┌──────────────────────────────────────────────┐
        ▼                                                │
     START ──▶ WORK ──▶ CHECK ──▶ UPDATE ──┬─▶ END
   (scratch or                              │
    new version)                            └─▶ NEW VERSION ─┐
                                                                │
        ◀───────────────────────────────────────────────────┘
```

- **Start** — from scratch (a new project) or from a new version (an existing project taking on its next chunk of scope). Either way: `project-standard.md`'s minimum bar applies — at least git, ideally a one-line README. See `checklists.md` for the concrete step list.
- **Work** — happens entirely inside the project itself. A tracker built on this workflow has no role here and no visibility into it in real time, per the read-only boundary described in `tracking-protocol.md` — this is the phase a tracker only ever sees after the fact.
- **Check** — work gets reviewed against `tracking-protocol.md`: what changed, does it hold up, is anything now stale (docs, changelog, status claims). This can be the project owner reviewing it directly, a separate session working in the project, or a tracker reading the result afterward.
- **Update** — the project's own record gets brought current (its README, changelog, decision log — by the project itself, never by an external tracker) and, separately, the tracker's own record of it gets synced to reflect it.
- From Update, one of two things happens: loop back to **Work** (more to do on this version), or the cycle closes — either **End** (the project, or this phase of it, is genuinely done) or **New Version** (this chunk is complete, the next one starts, back to Start).

## This is a recommendation, not a mandate

Different unit types move through this loop differently, and that's expected — it maps onto the `type` field units already carry:

- **`sprint` / `milestone` / `goal`** units have a real End — the loop terminates, the unit's status moves to `done`.
- **`maintenance`** units — most relationships, most ongoing businesses, most open-ended personal or hobby projects — never hit End by design. They cycle Work → Check → Update indefinitely, or sit idle between cycles (`dormant`, not broken — see the status vocabulary in `project-standard.md`). "New Version" for these might just mean "the next thing worth doing," not a formal release.
- **`plan`** units might not have real Work yet — they can sit at Start/planning for a long time before anything downstream happens, and that's a normal state, not a stall.

If a project's real shape doesn't fit this loop well, don't force it — this exists to give most projects a common vocabulary (what phase is this in), not to standardize away real differences between a sprint and an open-ended venture.

## Where this shows up in a unit's files

A unit's `ledger.md` entries are, in effect, a record of Check/Update cycles over time — each entry is roughly "here's what Work produced, here's what Checking it found, here's the Update." Nothing new to build for this; it's already the shape those entries take.

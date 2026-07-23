---
domain: team
unit: ai-lab
type: maintenance
status: active
priority: high
urgency: medium
started: 2026-07-22
last_updated: 2026-07-23 (reconciliation — priority/urgency inherited from the project's own README to eliminate drift)
source:
  - "/Users/mklvsky/AI/AI-LAB (git repo, local only, no remote yet) — verified directly: HEAD c8a4613, branch main, working tree clean"
components:
  git:
    present: true
    path: "/Users/mklvsky/AI/AI-LAB"
    remote: "none — local only, adding one is an open item"
    branch: "main"
    head: "c8a4613"
    working_tree: "clean, no locks — the one unstaged edit from the previous check is now committed"
    verified: "2026-07-23"
    how: "git log/status, direct"
  readme:
    present: true
    verified: "2026-07-23"
    how: "read directly — confirms priority: high (provisional), urgency: medium, status: active, type: maintenance"
  docs:
    present: true
    location: "docs/knowledge-base (model/hardware analysis), docs/curriculum (4 phases), docs/team-rollout (process + domain template), docs/guidelines (synced copy of Ledger's own guidelines)"
    verified: "2026-07-22"
    how: "read + ls"
  changelog:
    present: true
    location: "technical/changelog.md"
    verified: "2026-07-22"
    how: "read"
  decision_log:
    present: true
    location: "technical/decision-log.md"
    verified: "2026-07-22"
    how: "read"
  live_artifact:
    present: false
    note: "not applicable — this is a learning/process program, not a deployed product"
---

# AI-LAB — personal & team AI adoption

David's hybrid AI learning program (local models + Claude remote) and the base for rolling AI adoption out to the team, domain by domain. Not a coding project — a learning/process project, explicitly structured (by its own decision log) to follow Ledger's own guidelines rather than invent a bespoke tracking shape. First unit in a new `team` domain — created 2026-07-22 alongside this tracking entry, since this project is squarely about team/org capability building, distinct from both `business` (specific ventures) and `personal` (individual life domains).

## Reconciliation — 2026-07-23, second pass

The first reconciliation pass set `priority: medium` in Ledger, cleaning up the messy prose-embedded field value — but that created a real `DRIFT` flag, since AI-LAB's own README still declares `priority: high (provisional...)`. Per David's instruction, Ledger now **inherits** the project's own declared values instead of picking a different one: `priority: high`, `urgency: medium` (unchanged) — both taken directly from the project's own README line: *"Current status (2026-07-22): `active` · priority: `high` (provisional — team efficiency + rollout initiative) · urgency: `medium`..."* This clears the drift while keeping "provisional" as context in prose rather than embedded in the field itself, consistent with how priority/urgency proposals are handled everywhere else in Ledger.

Git re-verified clean in the same pass as before: the single unstaged edit is now committed (`HEAD` `a8cbf95` → `c8a4613`), no locks present.

## What it actually is (from source docs)

Grew out of a corrected AI model-selection/hardware analysis report (`docs/knowledge-base/`) — the original analyst report had a disqualifying hardware error and invented numbers; the corrected version is grounded in Anthropic's published pricing and real hardware research, with sourced fact kept explicitly separate from labeled estimate. That report grew an appendix (a 9-lesson local-AI curriculum), which then grew into a full 4-phase program:

- **Phase 1 — Foundations**: 3 core lessons (hybrid mental model, Claude model selection, cost/token literacy) plus a parallel, optional 9-step local Mac track (Ollama/LM Studio, prompting, a local coding assistant, speech-to-text/text-to-speech, local image gen, local RAG, a capstone pipeline).
- **Phase 2 — Model Mastery & Optimization**: building a personal benchmark set, advanced prompting for reliability, reading model releases critically. Fully detailed, not started.
- **Phase 3 — Agentic Workflows & Skills**: what Claude Skills are, building a custom skill, subagents/orchestration, MCP connectors, a capstone agentic workflow. Fully detailed, not started.
- **Phase 4 — Team Rollout**: personal-teaching lessons (preparing to teach, first domain session, feedback loop, scaling beyond the first domain) plus a rollout process and per-domain onboarding template, already drafted. Explicitly gated: per the lessons' own framing, not realistically startable until Phase 3 is done — "can't teach what you haven't internalized yet."

## Current state (verified 2026-07-22, from source directly; git re-verified 2026-07-23)

**Setup — done:** folder structure, knowledge-base report, all 4 phases of curriculum (Phase 1 fully written, Phases 2-4 detailed into lesson files same day at David's request), notes system + index, team-rollout process draft, git initialized with real commit history.

**Phase 1 — in progress:**
- Core lessons 1-3 (hybrid mental model, model selection, cost/token literacy): not started.
- Local Mac track: K.1 (Ollama/LM Studio environment) and K.2 (first local model, chat & compare) both done 2026-07-22 — David substituted a GUI tool called "Bionic" for the originally-recommended LM Studio, judged an equivalent fit for the same job. K.3-K.9 not started.

**Phases 2-4:** fully detailed into lesson files, zero lessons started — expected, since the curriculum is explicitly sequential and Phase 1 isn't closed out.

**Open items, not yet done:**
- Git remote (GitHub/GitLab) — recommended in `SETUP.md`, not required to keep working, David's call.
- Phase 1 core lessons 1-3.
- Local track K.3 onward.
- The explicit 3-way local-vs-Haiku comparison flagged in K.2 as still worth doing, not currently blocking.

## Does this follow Ledger's own principles? — yes, verified directly, not just claimed

This project's own `technical/decision-log.md` records an explicit 2026-07-22 decision to adopt Ledger's guidelines rather than invent new structure, and synced a literal copy into `docs/guidelines/`. Checked directly against Ledger's current v0.4 vocabulary (`guidelines/project-standard.md` in this repo) — the synced copy matches exactly: same three independent axes (status/priority/urgency), same four-value status enum, same three-value priority/urgency enums. The one deliberate addition — a `notes/` folder and `docs/team-rollout/` area, neither explicitly named in the standard — is exactly the kind of extension `project-standard.md` invites ("add it with the same shape... rather than forcing it into an existing category"), not a deviation from it.

**Worth knowing, not acted on:** this is the one project in the whole portfolio with its own local copy of the guidelines (`docs/guidelines/`) — unlike the Egraine family, where placing a copy was explicitly declined. That copy was synced against v0.4/pre-ADR-0012 vocabulary; it hasn't been checked against the new v2.1 ALFA+OMEGA stamp. Not touched here — that would be a write to AI-LAB's own repo, same boundary as everywhere else.

One real platform note, not a project failure: git couldn't be initialized from inside the sandbox at first (the sync mode blocked delete/rename), and the decision log is candid about that rather than hiding it — resolved same day once David granted file-delete permission for the folder.

## Read-only boundary (ADR-0001)

This unit and its ledger only ever read AI-LAB's own files — nothing here was written to AI-LAB's source. AI-LAB's own content (README, checklist, changelog, decision log, notes) is written and updated by/through direct work on that project, not by Ledger.

# Ledger Framework Evaluation — does it still hold?

*Prepared 2026-07-22, at v0.5. Read-only pass across `/Users/mklvsky/AI/` — LEDGER, ALFA+OMEGA, PROJECTS/*, AI-LAB. No tracked source was modified (ADR-0001 respected). Every factual claim below is labelled **verified** (checked this session) or **claimed** (a doc says it, not independently confirmed), per Ledger's own tracking-protocol.*

---

## 1. Verdict up front

The **design** is genuinely good and holds up as complexity grows. The **data inside it** has started drifting from reality, and the **enforcement layer that would catch that drift is designed but not built**. You caught this at exactly the right moment: the framework isn't broken, but it's one or two more projects away from becoming the "untraceable mess" you're worried about, and the first concrete contradiction has already appeared (Thann — see §4A).

| Layer | Rating | One-line |
|---|---|---|
| Governance / conceptual design | **8.5 / 10** | ADRs, read-only boundary, three-axis vocabulary, append-only, claimed-vs-verified — all sound and portable. |
| Data fidelity (does Ledger match reality?) | **4 / 10** | A live contradiction on Thann; a "high-priority active sprint" (Medex) that has no git; several units mis-sourced. |
| Coverage (is everything tracked?) | **4.5 / 10** | 3 real projects on disk are absent from the index — one of them your most governance-mature repo. |
| Enforceability / migration | **3.5 / 10** | Adoption is manual and divergent; no scaffolder, no linter, no "what changed" detector. |
| Operational git hygiene | **4 / 10** | Systemic lock-file cruft from the device bridge; two repos have live locks that will block the next commit. |

**Overall: a strong architecture whose reality-sync and enforcement haven't kept pace with the project count.** That's a fixable, well-timed problem, not a design failure.

---

## 2. The map — how these projects actually relate

This is what the filesystem says (verified by reading each folder), which matters because it differs from what Ledger models.

**The Egraine group (business):**

- **Egraine Oy** — the parent. Nordic (Helsinki) exclusive distributor of premium cosmetics/skincare, holder of the group's IP and trademarks. Run by David Mikulovský and Dominika Jamborová. Lives at `PROJECTS/Egraine` (its own git repo, Astro site rebuild in progress).
- **Medex Beauty Clinic** (medex.fi) — a physical, client-facing clinic. Named from the *Medex Bio Science Cosmetics* (Germany) manufacturing partnership. Its own project at `PROJECTS/Medex`. Now also the temporary physical home for THANN treatments.
- **THANN** (thann.fi) — Thai wellness brand (THANN-Oryza Co., Bangkok; majority-owned by Rohto Pharmaceutical). Egraine is its exclusive Nordic distributor. Physical spa discontinued; online store + gift cards only, treatments redeemed at Medex as a temporary phase-out. Its own project at `PROJECTS/Thann`.
- **Eden's Eva** (edenseva.com) — dormant venture, IP retained, domain parked. No folder — correctly held as a concept.
- **SkinThea** — hibernated venture idea, no third-party brand named yet. No folder — correctly held as a concept.

The real relationship on disk is **sibling repos that share a parent brand**: `Egraine`, `Medex`, and `Thann` are three peer folders, each independently version-controlled, with the child projects treating Egraine's folder as *read-only reference* (Thann's own `CLAUDE.md` spells this out: "Egraine's parent-brand docs are read-only reference, not something this repo edits"). Ledger, by contrast, models them as **nested ventures** under one Egraine unit. Both are defensible; they just don't match each other (see §4C).

**Standalone projects:**

- **Jascandi** (`PROJECTS/Jascandi`) — a design/services site. Git lives one level down at `Jascandi/web/.git`; `shareable-docs/` and `versions_archive/` sit outside version control. Tracked, low/low. A clean small-project example.
- **Ozuvox** (`PROJECTS/Ozuvox/ozuvox-v2`) — a Next.js marketing site ("Growth Systems Studio"). **No git. Not tracked in Ledger at all.**
- **project-cars** (`PROJECTS/project-cars`) — a car-buying decision framework + tool. The most governance-mature repo you have: **26 ADRs**, a spec at v3.2, a 33 KB changelog, its own handover protocol. **Not tracked in Ledger at all.**
- **dives-enterprises** (`PROJECTS/dives-enterprises`) — a landing page (git present, README is literally "Landing page."). **Not tracked in Ledger at all.**

**Meta / infrastructure:**

- **LEDGER** — the tracker itself, and a self-tracked unit (`projects/ledger`).
- **ALFA+OMEGA** — the *canonical* home of the four guideline docs (`project-standard`, `tracking-protocol`, `workflow`, `checklists`).
- **AI-LAB** — your hybrid AI-adoption learning program + team-rollout base. Tracked as `team/ai-lab`. The best-behaved project in the whole set (see §3).

---

## 3. What's working (so the criticism has a baseline)

- **The three-axis vocabulary (status / priority / urgency) + disputed flag is the strongest single design choice.** The Eisenhower split (importance vs. time-sensitivity) is exactly right, and the collapse from 7→4 statuses and 5→3 priorities in v0.4 made it *smaller and more honest* at once. It'll drive the priority/status visualizations on the roadmap with no data-model change.
- **The read-only boundary (ADR-0001) is load-bearing and has held.** Every correction so far landed only in Ledger's own files. It's the reason a wrong guess about a project never corrupts the project.
- **Claimed-vs-verified is a real discipline, not decoration** — and it's already propagating *into* the projects (Thann's `CLAUDE.md` item 4 re-states it verbatim). That's the framework successfully teaching a habit downstream.
- **The ADR log is excellent.** Numbered, append-only, supersede-in-place (ADR-0004's vocabulary superseded by 0005 without deleting 0004). This is governance that *aids* decisions rather than obscuring them — the opposite of ceremony.
- **Ledger holds itself to its own standard** (SPEC, CHANGELOG, ROADMAP, git) — the "if a tracked project needs a spec, so does the tracker" reflex is what keeps it honest.
- **AI-LAB is the proof the model works when actually followed**: three independent axes in the README, correct `maintenance` typing, git-as-record-of-truth, a `current-lesson` symlink as a next-action pointer, dated/greppable notes. If every project looked like AI-LAB, this evaluation would be one line.

---

## 4. The cracks (grouped, most-serious first)

### 4A. Tracker-vs-reality drift — the headline problem

**Thann is the canary.** The `PROJECTS/Thann` repo — which has its own README and CLAUDE.md dated 2026-07-22 — states **Status: active · Priority: high (approved) · Urgency: high (raised 2026-07-22 for Phase 0)**. Ledger's `thann` unit says **priority: medium · urgency: low**. That is a direct, current contradiction: the project's own source-of-truth and the tracker disagree on two of the three axes.

Worse, **Ledger's `thann` unit is pointed at the wrong source.** Its `source:` is the Egraine decision-log spreadsheet on the SAMSUNG pen drive + `thann.fi` — it has no idea the `PROJECTS/Thann` repo (with a full Phase-0 audit, an SEO audit, a recovery plan, and its own dated `00-Decision-Log/ledger.md`) even exists. So Ledger is summarizing a stale secondhand view of Thann while the real, actively-worked repo sits untracked beside it. (This session already flagged the disputed live-site/decision-log conflict and set `disputed: true`; the priority/urgency contradiction and the mis-sourcing are *additional* and still open.)

This is the exact failure mode you asked to catch early. It didn't come from a bad design — it came from **no routine that re-checks a unit against its real source**. The `full`/`sync`/`audit` verbs that would catch it are designed (ADR-0006) but unshipped and unrun.

### 4B. Coverage gaps — three real projects are invisible to the index

`_index.md` (last generated 2026-07-22) does not include **Ozuvox**, **project-cars**, or **dives-enterprises**. project-cars is the sharpest miss: 26 ADRs and a v3.2 spec, i.e. more internal governance than most of the tracked units, yet Ledger has never heard of it. This is precisely what the *Ledger-wide `audit`* is meant to surface ("units present on disk but absent from `_index.md`, or vice versa") — and again, that verb exists on paper only.

### 4C. Model mismatch — nested ventures vs. sibling repos

Ledger models Medex and Thann as `business/egraine/ventures/*` (children nested inside the Egraine unit). On disk they are **peer folders**, each its own git repo, cross-referencing Egraine read-only. As the group grows this strains in concrete ways:

- A nested `_unit.md` can't cleanly carry a child that has its *own* independent git history, remote, changelog, and version track — the `components:` schema assumes one repo per unit.
- The parent's `sub_units:` list and the children's real `source:` repos can drift independently (they already have — the Thann child's real repo isn't referenced anywhere in the parent).
- "Sibling that shares a parent brand" is a real relationship the current schema can't express except by nesting, which implies an ownership/containment that the filesystem doesn't have.

Not a crisis, but the single place where "large & complex parent structure" (your Egraine case) outgrows what "small & straightforward" (Jascandi) needs. Worth an explicit decision (ADR) on how the group is represented before adding a fourth venture.

### 4D. Git — one hard-requirement violation, and systemic lock cruft

Git is the *one* non-negotiable in `project-standard.md`. Findings:

- **Medex has no git at all** — and Ledger tracks it as `active, priority high, urgency high, sprint`. A high-priority active sprint with no version control is the one gap the standard says to flag loudly. **Ozuvox** also has no git (and is untracked). **dives-enterprises** has git but a two-word README.
- **Systemic lock-file corruption from the device bridge.** Verified across repos: Thann (many `HEAD.lock.stale.*` / `index.lock.stale.*` + live `index.lock` and `HEAD.lock` + `tmp_obj_*` + both `main` and `master` branches), project-cars (22 stale-lock files, 94 `tmp_obj_*`, 1 live lock), Egraine (2 live locks + tmp objects), Jascandi's `web/.git` (live `index.lock`), and **LEDGER itself** (`_to_delete/` full of `*.lock.stale`, `HEAD.lock.stale`, `index.lock.stale`). AI-LAB's README diagnoses the root cause plainly: the folders sync into the sandbox "in a mode that blocks delete/rename by default," which breaks `git init`/commit and leaves locks that `device_bash` then can't `rm` (so cleanup = move-to-`_to_delete`-and-rename). **Two repos (Thann, project-cars) have a live `index.lock` right now, which will block their next git write until it's removed.** This is friction between git and the Cowork device bridge, not a bug in Ledger — but it's degrading real repos and deserves a standing cleanup step.

### 4E. Convention divergence — the enforceability gap

The same concept has a different name and location in every project (all verified):

| Concept | Thann | Medex | Egraine | project-cars | AI-LAB | Jascandi |
|---|---|---|---|---|---|---|
| "why" record | `00-Decision-Log/ledger.md` | `01_Decision Log/Decision Log.md` | `00-Decision-Log/…xlsx` | `docs/decisions/ADR-*.md` | `technical/decision-log.md` | — |
| "what" record | git | (none: no git) | git log | `docs/CHANGELOG.md` | `technical/changelog.md` | `web/technical/changelog.md` |
| Claude brief | `CLAUDE.md` | — | `STRUCTURE-README.md` | `docs/HANDOVER.md` | `README.md` | `web/README.md` |
| Folder numbering | `00-`/`01-` | `01_`/`02_` | `00-`/`01-` | `docs/` subdirs | `docs/`+`technical/` | flat |

`project-standard.md` deliberately says "when something exists, it lives somewhere predictable" — but in practice locations are **not predictable across projects**, because adoption is manual and each project reflects whenever it was set up. This is the structural reason your instinct is correct that "sometimes the changelog isn't updated, sometimes git isn't committed, sometimes the README isn't." There is currently **no mechanism that detects those omissions** — no scaffolder to make a new project conform, no linter to check an existing one, no "these files changed but the changelog didn't" diff. The standard is advisory; nothing makes it stick.

### 4F. Parent/child safety — and a near-miss that already happened

You asked specifically that a sub-venture have no authority to delete parent content. Two findings:

- The principle **exists only as per-project prose, not as an enforced rule.** Thann's `CLAUDE.md` (item 3) says treat `../Egraine` as read-only — good, but that's one project's own file, not a framework guarantee. Nothing structurally stops a child session from writing into a parent/sibling folder.
- **It has already gone wrong once.** Egraine's `STRUCTURE-README.md` documents a cleanup pass that deleted 48 files (~19 MB) and left the git working tree with "all the original root-level files … deleted, but not committed." It was only safe because a backup existed. That's the exact "accidentally delete files by cross-referencing" risk you named — and it's the mirror image of ADR-0001: the read-only boundary protects tracked sources *from Ledger*, but nothing protects a project (or its parent) *from a destructive session working inside it*.

---

## 5. Direct answers to your checklist

**Is the framework still applicable?** Yes — conceptually it scales fine. The vocabulary, boundary, and append-only history are as valid across 10 projects as across 2. What hasn't scaled is *keeping the records true* and *keeping coverage complete*, because both are still manual.

**Is it easily enforced / migrated to?** No — this is the weakest axis. There's no scaffold ("make me a conformant project skeleton"), no lint ("does this project meet the standard"), and no auto-detection of drift. Only AI-LAB and Thann have really adopted the conventions; the rest are heterogeneous. Migration today means hand-editing each project, which is why it's partial.

**Applicable to both large and small?** Small (Jascandi, dives) fits comfortably — "absence is normal" does its job. Large strains in two spots: the Egraine *group* outgrows single-parent nesting (§4C), and project-cars' *maturity* (26 ADRs, 3 independent version tracks) exceeds what one `_unit.md` + `ledger.md` can summarize — a very-mature project probably needs the unit to *point at* the project's own ADR/spec index rather than restate it.

**Do the ADRs help or obscure?** For Ledger, they clearly help — they're the best-maintained part of the system. One watch-item: project-cars shows the opposite failure mode (ADR-per-micro-decision, 26 and counting). ADRs earn their keep for *genuine, hard-to-reverse* decisions; when every tweak becomes one, they add ceremony. Keep Ledger's bar ("a decision about how the framework itself operates") and don't let unit-level work spawn ADRs.

**Skillset — applicable, and can we reuse more?** The `ledger` skill is well-designed but **designed-only, not shipped or tested** — so right now the query layer that would make all of this routine doesn't actually run. Your instinct to add time-window and filtered reports is right and partly anticipated (see §6). On reuse: the installed `product-management:*`, `marketing:*`, `sales:*` skills are *deliverable generators*, not trackers — they should **consume** Ledger output, not replace its core. `product-management:stakeholder-update` and `product-management:metrics-review` are the two most natural complements (feed them a unit's `ledger.md`). Don't rebuild tracking inside them.

**Should the skill be sharable into projects, not just Ledger?** Yes, and it nearly is already: Thann has its own dated `00-Decision-Log/ledger.md` in the same spirit. Design the `report`/`log` verbs to run against *any* folder that follows the standard — Ledger's units *or* a project repo — so "status of Thann" works whether you're standing in Ledger or in the Thann repo.

**Enforceable consistency / a "what changed" detector?** This is the highest-value missing piece and it's cheap to build because git is already the hard requirement. `git status --porcelain` + comparing file mtimes against the last commit date gives a reliable "these things changed but the changelog/README/decision-log didn't" report per project. Your "`/update <keywords>`" idea is sound; I'd shape it as a **run-on-demand consistency check** rather than an automatic hook — the device-bridge/git-lock friction (§4D) makes commit hooks fragile, so a deliberate command you run at end-of-session is more robust than a hook that silently fails.

---

## 6. Skills to build (in priority order)

1. **`ledger audit` — actually ship and run it first.** It already *defines* the checks that would have caught §4A/§4B/§4D (mis-sourced units, on-disk-but-unindexed projects, stale `verified:` dates, git violations). Shipping this one verb converts most of this report into a repeatable command. Highest leverage by far.
2. **A consistency / "what-needs-logging" check** (your `/update` idea): per project, `git status` + mtime-vs-last-commit → "changelog stale, README status line stale, N files uncommitted." Runs at any depth in a repo. Prevents §4E omissions.
3. **Time-window reporting** (your last-week / last-month / last-year idea): trivial because every `ledger.md` entry is dated and append-only — a report that reads across units and filters entries by date range. Add as `report … since:<date>` or a `portfolio changed:<window>` filter. Genuinely missing from the current grammar.
4. **A `new`-project scaffolder that enforces the standard**: `git init`, a conformant folder skeleton, a `CLAUDE.md`/README stub with the three axes, a decision-log file with the *canonical name* — so new projects stop diverging (§4E) at creation.
5. **Reuse, don't rebuild:** wire `product-management:stakeholder-update` / `metrics-review` as optional *formatters* on top of Ledger data.

---

## 7. Recommendations, sequenced

**Now (fidelity + safety):**

- Reconcile **Thann**: point the unit's `source:` at `PROJECTS/Thann`, and resolve the priority/urgency contradiction (the project says high/high; Ledger says medium/low — the project is almost certainly right, but it's your call). This session already set `disputed: true` for the live-site conflict; fold this in.
- **Onboard the three untracked projects** (Ozuvox, project-cars, dives-enterprises) or explicitly decide they're out of scope and note *that* — either way, stop them being silently invisible.
- Flag **Medex's missing git** as the real gap it is (it's a high-priority active sprint). Fixing it is a separate, explicit, user-directed task per ADR-0001 — not something the tracker does on its own.
- Add a **git-lock cleanup step** to your workflow (remove stale `*.lock`/`tmp_obj_*`; Thann and project-cars have *live* locks blocking their next commit right now).

**Next (enforcement):**

- Ship `ledger audit`, then the consistency check and time-window report (§6 1–3).
- Write an **ADR on group representation** (nested vs. sibling for Egraine/Medex/Thann) so the model matches reality before a fourth venture is added.
- Write a **child-safety rule** (the mirror of ADR-0001): a session working in a child/sibling project treats parent and sibling folders as read-only, and destructive operations (bulk delete, `git rm`) always require explicit confirmation + a verified backup, never a side effect. The Egraine 48-file near-miss is the motivating case.

**Later (hygiene):**

- Pick a **single source of truth for the guidelines.** Right now three byte-identical copies exist (ALFA+OMEGA — the "canonical" one, which has *no git* — plus LEDGER/guidelines and AI-LAB/docs/guidelines) with no sync mechanism. They agree today (verified: identical md5s); they will drift the moment one is edited. Put the canonical copy under git and make the others explicit synced/symlinked copies, or reference rather than duplicate.
- Add a canonical-filename convention for the decision-log/changelog so §4E stops reproducing.

---

## 8. Bottom line

The framework holds. Its ideas are good enough that projects are voluntarily adopting them (Thann, AI-LAB), which is the real test. What's failed to keep pace is *operational*: the records have drifted from reality because nothing re-checks them, coverage has gaps because nothing audits for them, and consistency varies because nothing enforces it — and the very skill that would fix all three is designed but not yet running. Build the `audit` + consistency + time-window verbs, decide the Egraine group's representation, add the child-safety rule, and the "untraceable mess" risk goes away. You flagged this at the right time.

*Sources: LEDGER `_index.md`, `SPEC.md`, `CHANGELOG.md`, `adr/0001`, `adr/0005`, `adr/0006`, `guidelines/*`, unit files for egraine/thann/ledger; ALFA+OMEGA + AI-LAB guideline copies (md5-compared); PROJECTS/{Thann,Medex,Egraine,Ozuvox,project-cars,dives-enterprises,Jascandi} READMEs/CLAUDE.md/structure + recursive file listings; AI-LAB README. All reads were non-destructive.*

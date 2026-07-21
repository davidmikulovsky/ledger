# Checklists

*Concrete, step-by-step versions of `workflow.md`'s loop. Optional in the sense that nothing breaks if a step gets skipped — but the point of writing these down is so skipping one is a choice, not an accident. Check off what applies; ignore what doesn't fit this particular project.*

## Start (new project, or a new version of an existing one)

- [ ] `git init` done — or, for a new version of an existing project, confirmed the existing repo and remote are the ones actually being worked from (see the multi-copy caution in `tracking-protocol.md`).
- [ ] A README exists, even one line: what this is, current status, how to run/deploy it if that applies.
- [ ] Provisional priority and status set (see the vocabulary in `project-standard.md`) — a rough first guess is fine, it gets reviewed later, not fixed forever.
- [ ] If this project is being tracked by something external: a record created there, pointed at this project's real location. The tracker's record links to the project — it never becomes a second copy of the project's content.
- [ ] First real commit made (not a placeholder — something that reflects actual starting content).

## Work

*This phase happens inside the project. Nothing here needs a tracker's involvement — these are habits worth keeping regardless.*

- [ ] Commit as work happens, not in one pass at the end — small, real commits are what make history worth having later.
- [ ] If the README's status line has drifted from reality, fix it when noticed rather than letting it accumulate staleness.
- [ ] A decision worth remembering later gets written down somewhere — a commit message at minimum, a decision log entry if one exists for this project.

## Check

- [ ] Git state confirmed directly: branch, latest commit (hash, date, message), working tree clean or not.
- [ ] README and docs re-read against what's actually true right now — not assumed still accurate because they were once written correctly.
- [ ] Anything claimed as live, deployed, or working gets verified directly (fetch the URL, run the thing) rather than trusted from a doc — see the claimed-vs-verified discipline in `tracking-protocol.md`.
- [ ] Checked for other copies of this project (an old backup, a synced folder, a second machine) and confirmed none of them have silently diverged from the one being treated as canonical.
- [ ] What's missing against `project-standard.md` noted plainly — this is a fact to record, not a problem to apologize for.

## Update

- [ ] The project's own record — README, changelog, decision log — brought current, by the project itself.
- [ ] If tracked externally: that record synced separately, from what Check actually found, never copied uncritically from what Work claimed to have done.
- [ ] Priority and status reviewed honestly: has either actually changed, or has time just passed? Don't bump status to `active` just because something happened recently, or drop priority just because a project's gone quiet for a while — check both axes independently against their real definitions.
- [ ] Decide: loop back to **Work** (more to do this version), or move to closing.

## End (or New Version)

- [ ] If this is a real end: status set honestly to `done` (the goal was reached) or `ended` (work stopped, regardless of outcome) — these mean different things, pick the one that's actually true.
- [ ] If continuing into a new version: a changelog entry added, a version marker bumped if this project uses one.
- [ ] Either way, a closing or transition note exists somewhere real — a changelog line, a final commit message, a decision log entry — so the reason isn't only in someone's memory six months from now.

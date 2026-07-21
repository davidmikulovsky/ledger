# Tracking Protocol

*How a tracker reads a project against `project-standard.md`. This is the tracker's side of the contract — what to look for, how to record it, and how to be honest about what's actually been checked versus what's merely claimed somewhere. Written to stand on its own, independent of any specific tracking tool. See `checklists.md`'s Check/Update sections for this protocol as concrete steps.*

## The core discipline: claimed vs. verified

The single most important habit in this protocol, learned directly from a real case (a project's own README claiming "live" — true, but not confirmed until the actual URL was fetched and checked, at which point it turned out to be accurate — the point isn't that the claim was wrong, it's that it hadn't been checked yet). Every piece of information recorded about a project falls into one of two categories, and the record should say which:

- **Verified** — directly checked this session: ran `git log`/`git status`, fetched a live URL, read the actual file. Trustworthy as of the date checked, no further than that.
- **Claimed** — a source document *says* something is true (a README's "Status: live," a changelog's "no known bugs") but nobody has independently confirmed it this session. Still useful, still worth recording — just don't present it with the same confidence as something verified.

Never upgrade a claim to verified without actually checking. This sounds obvious and gets skipped constantly under time pressure — it's the entire reason this section exists.

## What to check, per project

Walk the project against `project-standard.md`'s categories. For each one present, verify it if practical; if not present, record that plainly — per that standard, absence is normal, not a defect (except git).

- **Git** — presence, remote (if any), current branch, latest commit (hash + date + message), working tree state (clean or has pending changes). This is the one category worth checking thoroughly every time, since it's the hard requirement and the thing most likely to have silently diverged if a project has ever existed in more than one copy (an old backup, a synced folder, a second machine) — worth explicitly checking for multiple copies and comparing commit history between them, not just trusting the one in front of you.
- **README** — present or not, and whether it looks current (stale status lines are common and worth flagging, not just parroting).
- **Docs / specs** — what exists, roughly what it covers, whether it looks current.
- **Changelog / decision log** — what exists; pull recent entries into the unit's own ledger rather than just noting the file exists.
- **Live artifact** — if the project claims to be deployed somewhere, that claim is exactly the kind of thing worth actually fetching and checking rather than trusting, per the discipline above.

## The components data structure

Each unit's `_unit.md` front-matter can carry a `components:` block — a structured, at-a-glance record of the categories above. This is optional (a brand-new unit won't have one yet) and additive (fill in what's known, leave the rest out rather than guessing). Schema:

```yaml
components:
  git:
    present: true
    path: "/absolute/canonical/path"
    remote: "github.com/owner/repo"   # or "none — local only"
    branch: "main"
    head: "abc1234"
    working_tree: "clean"              # clean | uncommitted-changes | unknown
    verified: "2026-07-21"
    how: "git log/status, direct"
  readme:
    present: true
    verified: "2026-07-21"
    how: "read"
  docs:
    present: true
    location: "docs/"
    verified: "2026-07-21"
    how: "read"
  changelog:
    present: true
    location: "technical/changelog.md"
    verified: "2026-07-21"
    how: "read"
  decision_log:
    present: false
  live_artifact:
    present: true
    url: "https://example.com"
    status: "live"
    verified: "2026-07-21"
    how: "fetched directly"
```

Every entry needs `verified` (a date) and `how` (what kind of check — reading a file is weaker evidence than running git or fetching a live URL; say which). A component with `present: false` needs nothing else — that's the whole point, absence is a one-line fact, not a paragraph.

This list of component types isn't fixed. A project might have a component type nothing above anticipates (a Shopify theme, a CI pipeline, a dataset) — add it with the same shape (`present`, `verified`, `how`, plus whatever fields make sense) rather than forcing it into an existing category.

## Cadence

Ad hoc by default: the project owner reports changes, or asks for a re-check against the real source, and the tracker re-checks against this protocol at that point — not on a fixed schedule, not automatically, unless a specific tracking system layers scheduled checks on top of this protocol.

## The boundary, restated

Everything in this protocol is about *reading*. Any tracking system built on this protocol should hold to a hard read-only boundary against tracked projects' own source — see the specific tracking system's own governance for the formal record of that rule (in this deployment: `adr/0001-read-only-boundary-on-tracked-projects.md`). Verifying a live URL or running `git log`/`git status` are read operations; nothing in this protocol authorizes writing to a tracked project's own files.

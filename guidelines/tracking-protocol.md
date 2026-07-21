# Tracking Protocol

*How Ledger reads a project against `project-standard.md`. This is Ledger's side of the contract — what to look for, how to record it, and how to be honest about what's actually been checked versus what's merely claimed somewhere.*

## The core discipline: claimed vs. verified

The single most important habit in this protocol, learned directly from a real case (Jascandi's README claiming "v2.2, live" — true, but not confirmed until the actual URL was fetched and checked). Every piece of information Ledger records about a project falls into one of two categories, and the unit files should say which:

- **Verified** — Ledger (or David) directly checked it this session: ran `git log`/`git status`, fetched a live URL, read the actual file. Trustworthy as of the date checked, no further than that.
- **Claimed** — a source document *says* something is true (a README's "Status: live," a changelog's "no known bugs") but nobody has independently confirmed it this session. Still useful, still worth recording — just don't present it with the same confidence as something verified.

Never upgrade a claim to verified without actually checking. This sounds obvious and gets skipped constantly under time pressure — it's the entire reason this section exists.

## What to check, per project

Walk the project against `project-standard.md`'s categories. For each one present, verify it if practical; if not present, record that plainly — per that standard, absence is normal, not a defect (except git).

- **Git** — presence, remote (if any), current branch, latest commit (hash + date + message), working tree state (clean or has pending changes). This is the one category worth checking thoroughly every time, since it's the hard requirement and the thing most likely to have silently diverged across copies (see: the pen-drive/SSD/Documents triple-copy discovery on Egraine and Jascandi, 2026-07-21).
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

Ad hoc by default, matching how Ledger already operates: David reports changes, or asks to "sync [unit] from source," and Ledger re-checks against this protocol at that point — not on a fixed schedule, not automatically. A scheduled/automatic check-in is a plausible future direction (see `ROADMAP.md`), not current behavior.

## The boundary, restated

Everything in this protocol is about *reading*. See `adr/0001-read-only-boundary-on-tracked-projects.md` — this document does not create any exception to that rule. Verifying a live URL or running `git log`/`git status` are read operations; nothing in this protocol authorizes writing to a tracked project's own files.

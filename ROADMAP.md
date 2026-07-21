# Ledger — Roadmap

*Future directions. Nothing on this page is built. This exists so ambition has a place to live that isn't chat history, and so "not built yet" reads as a plan, not a gap in the design. Move an item here into `CHANGELOG.md` when it actually ships — don't backfill this page to make it look further along than it is.*

## Reporting skills

A set of Claude skills, each generating a specific kind of report from what Ledger already tracks:

- **Financial/sales pulls per project** — for units with numeric data available (sales figures, metrics, KPIs), a skill that pulls current numbers from the real source and produces a short, current summary rather than requiring a manual read-through.
- **Quick visualization** — turn a pulled number set into a chart/table on demand, for a single project or a comparison across a few.
- **Short reports, single or multi-project** — a skill that reads across one or several units' `_unit.md`/`ledger.md` files and produces a digestible status report — closer to what `_index.md` does today, but generated on demand with more narrative than a table row.

## Live feed / app surface

Longer-term: project updates feeding into something reviewable at a glance without a chat session — a lightweight dashboard or app view over the `domains/` structure, refreshed from real sources on some cadence rather than only when asked. The `components` data structure (see `guidelines/tracking-protocol.md`) is a deliberate first step toward this — a consistent, structured shape that a future dashboard could read directly, if this gets built.

## Notifications

Push updates out rather than requiring a pull: a phone or email notification when something tracked changes meaningfully, or when a scheduled check-in finds something worth flagging (a stale claim, a unit gone quiet, a component that stopped verifying cleanly). Would likely build on the scheduled-task capability already available in this environment, once there's a defined "what's worth notifying about" — that definition doesn't exist yet.

## Scheduled/automatic checking

Right now, Ledger only checks a project when asked (see `guidelines/tracking-protocol.md`, cadence section). A scheduled pass — periodically re-verifying `components` entries, flagging ones that have gone stale — is a natural extension once there are enough tracked units for "did I forget to check on X" to become a real problem rather than a hypothetical one.

## Not planned, just noted

Anything that would require Ledger to write to a tracked project's own source is out of scope by design, not by oversight — see `adr/0001-read-only-boundary-on-tracked-projects.md`. Automation on this roadmap means *reading and reporting* faster/more often, never *acting* inside a tracked project.

# ADR-0002: Storage location and hosting model

**Status:** Accepted — supersedes the 2026-07-15 "GitHub private" hosting decision for this framework's own storage
**Date:** 2026-07-21

## Context

The framework originally lived on a pen drive, git-tracked locally, with a separate decision (2026-07-15) to eventually push it — and Medex/Egraine's own docs — to private GitHub repos rather than self-host, given the real risk tradeoffs worked through at the time (Coolify's own critical-RCE history, co-location risk with the existing Jascandi VPS, Codeberg evaluated and set aside as a marginal fit). That GitHub push was decided but never executed.

David has since migrated the framework's location from the pen drive to a local SSD-backed folder (`/Users/mklvsky/AI/LIFE_OS`) — more persistent than removable media, still fully local. He's chosen **local git only** as the answer to the hosting question for now, rather than pushing to GitHub or anywhere remote.

## Decision

This framework's git history lives **locally only**, on persistent local storage, with no remote (GitHub, self-hosted VPS, or otherwise) at this time. This is a deliberate, revisit-when-needed choice, not an oversight — cloud/remote backup gets reconsidered if and when an actual need for it shows up (device loss risk becomes real, collaboration requires it, etc.), rather than being built preemptively.

This decision is specific to *this framework's own storage*. It says nothing about how Medex, Egraine, or any other tracked project should host their own material — per ADR-0001, this framework has no say or role in that; those are separate decisions made directly within those projects.

## Consequences

One fewer moving part to maintain (no remote credentials, no push/pull discipline, no third-party custody question) — the entire earlier GitHub-vs-self-host-vs-Codeberg analysis becomes moot for now, kept in the ledger as a record of the reasoning rather than an active plan. The tradeoff: no off-device backup exists right now. If this SSD-backed location is lost, corrupted, or the machine fails, the framework's history goes with it — a real, accepted risk given the current stage, revisited if it stops being acceptable.

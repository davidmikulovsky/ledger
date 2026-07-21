# Jascandi — ledger

Newest first.

---
**2026-07-21 (later)** — Two follow-ups verified directly, not just read from docs: the stray orphan `.git` at the project root is confirmed gone (David cleaned it up). Fetched `jascandi.com` live — confirmed working, correct title/meta/OG tags, no internal files exposed. Both items closed.

**2026-07-21** — David checked all Jascandi copies across the pen drive, `Documents/PROJECTS`, and `Documents/PROJECTS_v0` directly and confirmed `/Users/mklvsky/AI/PROJECTS/Jascandi/web` as the canonical, most up-to-date, git-verified copy (clean working tree, HEAD `b905b08`, matches GitHub origin). Backed up to Google Drive first (`Projects/jascandi-backup-2026-07-21-v2.zip`); other local copies being deleted on David's end. Re-read README and changelog: project has moved to v2.2 since Ledger last looked (a real security fix — the Dockerfile was serving the entire repo over HTTP, not just the site, now fixed with an allowlist + nginx security headers), plus a documentation catch-up pass adding `technical/changelog.md` and `technical/workflow.md`. `source:` updated to the new canonical path.

**2026-07-14** — Unit created in life-os, built from `git log` and README/docs in the linked repo. No client/collab activity yet per your description; site itself (v2.1) is complete and live. Most recent repo activity (2026-07-13) was a docs reorg separating business docs from technical docs — housekeeping, not new scope.

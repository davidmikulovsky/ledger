# life-os — ledger

Newest first.

---
**2026-07-15 (later)** — Hosting decision finalized: **GitHub private**, not self-hosted, for now. Worked through the actual risk chain — the original bare-git-on-Coolify-VPS idea doesn't isolate from Coolify's own demonstrated critical-RCE history since Coolify already runs on that box for Jascandi; a full Gitea/Forgejo stack adds a second DIY-patched CVE layer on top; a truly isolated second VPS would work but isn't worth new infrastructure right now. Decision: keep Medex/Egraine decision logs and task trackers on GitHub private (same pattern as Jascandi already uses), 2FA required, revisit self-hosting when company growth justifies owning dedicated infrastructure. Concrete next step (not yet done): turn Medex's and Egraine's docs folders into real git repos and push to private GitHub repos.

**2026-07-15** — Decided on off-drive backup approach: Option A (bare git repo over SSH on the existing Coolify VPS) now, Option B (Gitea/Forgejo via Coolify one-click, full UI) as a later upgrade only if needed. Not yet executed — needs you to run the SSH/git commands on your end (I don't have VPS credentials). Created this unit to track the framework's own progress, same pattern as every other tracked thing. **Superseded same day — see entry above.**

**2026-07-14** — Framework built: domain structure, front-matter schema, README, root index, seed units for Egraine and Jascandi. Git-initialized and committed locally.

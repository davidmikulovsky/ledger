# ADR-0012: Family/group schema, delivery mechanism, and orphan tiering

**Status:** Accepted
**Date:** 2026-07-23

## Context

ADR-0007 decided the *shape* of the parent/child relationship (a link, not nesting) but left three things unresolved, surfaced while reconciling the Egraine family:

1. **Field-name mismatch.** ADR-0007's text says `parent:` + `portfolio_members:`. Every real unit file (Egraine, Thann, Medex, Eden's Eva, SkinThea) still uses the pre-ADR-0007 `parent_unit:` / `sub_units:` fields. Checked directly against `ledger.py`: it reads `u.get("parent")` — meaning it already expects ADR-0007's field name, but since no file uses it, the scan engine has been silently reading `parent: None` for every child unit. `portfolio_members`/`members` is not read by any code at all; the rollup was only ever prose.
2. **No delivery path into tracked projects.** ADR-0007 lives only in `LEDGER/adr/`, a folder no tracked project ever reads. `project-standard.md` — the one document actually copied into every project — already has a "When projects form a family" section (added at guidelines v2.0), but it describes the *principle* in prose without a concrete field schema, so a project has no way to know what to actually write down.
3. **No tier for non-project entities.** Eden's Eva and SkinThea are tracked as full `_unit.md`/`ledger.md` pairs despite having no real folder or repo — they're a domain name and an idea, respectively. This forces them through the same machinery as a real project (declared `source:`, generating `SOURCE-MISSING`-style noise) for something that was never meant to be tracked as one.

## Decision

**1. Canonical field names** (retires `parent_unit:`/`sub_units:`, supersedes the unimplemented `portfolio_members:` name):

```yaml
role: independent | parent | child   # every trackable unit states this explicitly
parent: business/egraine              # present only if role: child — exactly one
relationship: distributed-brand       # optional, only alongside parent:
members:                              # present only if role: parent — a rollup, not ownership
  - business/thann
  - business/medex-beauty-clinic
```

**2. Two-tier model.** *Trackable units* (own real, git-trackable folder) get a full `_unit.md`/`ledger.md`, flat in `domains/`. *Mentions* (no real folder — a domain sitting unused, a placeholder, an idea, an arrangement noted only in text) are recorded as a `mentions:` list inside the nearest real unit's own frontmatter, not as their own unit:

```yaml
mentions:
  - name: "Eden's Eva"
    type: domain   # domain | link | placeholder | folder | idea
    note: "edenseva.com acquired, unused, revisit after Q2"
```

Promotion from mention to trackable unit happens the moment something gets a real folder — a visible, deliberate upgrade rather than an ambiguous in-between state.

**3. Delivery.** The schema and its rules live in `project-standard.md` (the doc actually copied into every project), not only in this ADR. `tracking-protocol.md` gets a parallel `family:` entry in the `components:` schema, plus a full `_unit.md` frontmatter reference — previously this schema existed only implicitly in `ledger.py`'s code and ADR-0007's one example, with no single doc stating it.

**4. Folder-naming conventions**, codified in `project-standard.md`: project root folders use PascalCase (the existing majority convention — Egraine, Thann, Medex, Ozuvox; two historical kebab-case exceptions grandfathered, not renamed retroactively). Internal pillar folders use `NN-Title-Case-With-Hyphens` (`00-Decision-Log`, `01-Docs`, …) — already independently adopted by both Egraine and Thann; this makes it the documented rule rather than an accident two projects happened to agree on.

**5. Version stamp bumped 2.0 → 2.1** across all five guideline docs, specifically so the existing `GUIDELINES-STALE` drift check in `ledger.py` can detect this change in any project that later gets a local copy. Leaving the stamp at 2.0 while changing the content would make the drift check blind to this exact update.

**6. `ledger.py` needs two new checks to actually enforce this**, not just store it — proposed as a separate patch, not bundled into this ADR:
- `MEMBER-MISMATCH` — a parent lists a member whose own file doesn't declare that parent back, or vice versa.
- `ORPHAN-PARENT` — a unit declares a `parent:` that doesn't resolve to any real unit.

## Consequences

The field rename is non-breaking — `parse_front_matter()` has no fixed schema, so units without the new fields parse exactly as before. `parent` starts resolving correctly the moment a file says `parent:` instead of `parent_unit:`, with no code change required for that part alone. `members:` and the two new flags require the `ledger.py` patch to actually be applied before they do anything beyond documentation.

**Known gap, not resolved by this ADR:** checked directly — none of Egraine, Thann, or Medex currently hold a local copy of `project-standard.md` or `workflow.md` in their own repo. `GUIDELINES-STALE` cannot fire for any of them, regardless of version number, until an initial copy is placed. Placing a file inside a tracked project's own repo is a write to that project and needs David's explicit go-ahead per ADR-0001/`git-and-access.md` — tracked as an open follow-up, not something this ADR authorizes on its own.

## Cross-reference

Refines ADR-0007. The core decision there — link, not containment — is unchanged; this locks the field names ADR-0007 left ambiguous and gives the model an actual path into the projects it's meant to describe.

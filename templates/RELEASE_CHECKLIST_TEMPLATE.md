# Release Record — Template

**Purpose:** Record the specific, tagged state being released, per `core/VVBM.md`
Stage 9. This is a per-release record, distinct from
`checklists/RELEASE_READINESS_CHECKLIST.md`, which is the reusable gate completed
*before* this record is filled in — that checklist is referenced here, not repeated.
**When to Use:** At the moment of release, after
`checklists/RELEASE_READINESS_CHECKLIST.md` has been completed with no unresolved
items.
**Instructions:** Fill every Required Field. Do not create this record before the
Release Readiness Checklist has passed.

## Required Fields

- **Version:**
- **Release date:**
- **Git tag:**
- **Summary of changes** (link to the `CHANGELOG.md` entry):
- **Release Readiness Checklist completed** (link, and confirmation of no
  unresolved items):
- **Released by:**

## Optional Fields

- **Known, accepted gaps carried into this release** (with rationale):
- **Rollback reference** (per `core/GIT_STANDARD.md` Rollback topic):

## Completion Criteria

- `checklists/RELEASE_READINESS_CHECKLIST.md` shows no unresolved items.
- The Git tag exists and matches the released state.
- `CHANGELOG.md` has a corresponding entry.

# Git Simplicity & Lowest-Risk Standard

**Standard type:** Core (mandatory)
**Purpose:** Defines the version-control principles every VESM project follows, so
that history is trustworthy, mistakes are recoverable, and releases are traceable —
regardless of which specific Git workflow (trunk-based, GitHub Flow, Git Flow, or
otherwise) a project uses.

This standard deliberately does not mandate one branching workflow. It describes
principles that hold across workflows; a project chooses the workflow that fits its
size and risk profile and applies these principles within it.

## The Ten Topics

Each topic below has a distinct scope; several concern related concerns (Recovery
vs. Rollback, Commit Quality vs. History Preservation) and each states what it
covers that the others do not.

---

### 1. Repository Integrity

- **Purpose:** The repository's history and current state are treated as a record of
  truth, not a disposable convenience.
- **Rules:** Destructive operations (force-push, history rewrite) on shared or
  public branches are avoided; where genuinely necessary, they require explicit,
  documented justification and coordination with anyone who could be affected.
- **Common Mistakes:** Force-pushing to a shared branch to "clean up" history without
  checking who else depends on it.
- **Verification:** Before any destructive operation, confirm no one else has
  unpushed work depending on the history being altered.

### 2. Branch Strategy

- **Purpose:** Work in progress is isolated from stable, releasable history in a way
  that matches the project's actual size and risk — without adopting a workflow's
  full ceremony where it isn't needed.
- **Rules:** A branching approach is chosen deliberately (per
  `constitution/CORE_PRINCIPLES.md`, Principle 5: Simplicity over unnecessary
  complexity) and applied consistently; it is not changed mid-project without
  reason.
- **Common Mistakes:** Adopting a complex multi-branch model for a small solo
  project; working directly on a shared stable branch for a project large enough
  that this creates risk for collaborators.
- **Verification:** The chosen strategy is documented somewhere a new contributor
  can find it, and actual practice matches what is documented.

### 3. Commit Quality

- **Purpose:** Individual commits are meaningful, self-contained units that make
  history useful for review and later investigation.
- **Rules:** A commit represents one coherent change with a message explaining what
  changed and why; unrelated changes are not bundled into a single commit.
- **Common Mistakes:** Commits like "fix" or "wip" with no explanation; a single
  commit mixing an unrelated refactor with a feature change, making later review or
  rollback of either one difficult.
- **Verification:** A commit's message and diff are checked against each other —
  does the message actually describe what the diff does?

### 4. Tagging

- **Purpose:** Specific, significant points in history — releases in particular —
  are marked so they can be found and referenced without searching commit history.
- **Rules:** Every release (`core/VVBM.md`, Stage 9) is tagged at the moment of
  release, using a consistent, documented naming scheme tied to
  `constitution/VERSION_POLICY.md`.
- **Common Mistakes:** Releasing without tagging, so the released state can only be
  approximately reconstructed later; inconsistent tag naming across releases.
- **Verification:** The tag exists, points to the exact commit that was released,
  and follows the project's documented naming scheme.

### 5. Release Management

- **Purpose:** A release is traceable to a specific, verified, documented state of
  the repository — never released from an undocumented or ad hoc state.
- **Rules:** Release Preparation (`core/VVBM.md`, Stage 8) is complete, and
  `CHANGELOG.md` is updated, before the Release stage tags and publishes.
- **Common Mistakes:** Publishing a release from a branch or state that doesn't
  match what was actually verified.
- **Verification:** The published release artifact and the tagged commit are
  confirmed identical.

### 6. Recovery

- **Purpose:** Before a risky operation, a path back to a known-good state is
  established and confirmed to actually work — not assumed to exist.
- **Rules:** A recovery path (a backup, a known-good tag, an untouched clone) is
  identified and its viability confirmed before performing any operation with
  destructive potential.
- **Common Mistakes:** Assuming "Git always has a way to undo it" without having
  actually confirmed a specific recovery path for the specific operation about to
  be performed.
- **Verification:** The recovery path is tested — not just believed to exist —
  before the risky operation proceeds.
- **Boundary:** Recovery is the *preparation* made before a risky operation; Rollback,
  below, is the *action taken* after something has already gone wrong.

### 7. Rollback

- **Purpose:** When a change turns out to be wrong after being merged or released,
  it can be reversed cleanly, without collateral damage to unrelated work.
- **Rules:** Changes are structured (per Commit Quality, above) so that a specific
  change can be identified and reversed independently of unrelated changes made
  around the same time.
- **Common Mistakes:** A bad change bundled with unrelated ones (violating Commit
  Quality), making it impossible to revert cleanly without also reverting unrelated
  work.
- **Verification:** A rollback of a specific change is confirmed to remove exactly
  that change's effect, and nothing else.

### 8. Lowest-Risk Decision Making

- **Purpose:** Where multiple version-control approaches would achieve the same
  goal, the one with the smallest potential for irreversible harm is chosen.
- **Rules:** This is the version-control application of
  `core/GS99.999.md`'s Risk Awareness principle: an operation's reversibility is
  considered explicitly before it is performed, not discovered afterward.
- **Common Mistakes:** Choosing a faster but destructive operation (e.g., a
  history rewrite) over a slower but safe one (e.g., a new commit that corrects the
  issue) without weighing the difference.
- **Verification:** For any operation with destructive potential, a lower-risk
  alternative was explicitly considered and the choice to proceed anyway (if made)
  is justified.

### 9. History Preservation

- **Purpose:** The record of how the system came to be — not just its current
  state — remains available, since it is often needed for Investigation
  (`core/VVBM.md`, Stage 4) and Post Release Review (Stage 10).
- **Rules:** History is not rewritten or truncated in ways that destroy the ability
  to trace when and why a change was made, beyond what Repository Integrity already
  restricts.
- **Common Mistakes:** Squashing or rewriting history in a way that loses the
  reasoning behind intermediate decisions, later needed during an investigation.
- **Verification:** A past decision or defect can still be traced to the commit and
  rationale that produced it.

### 10. Repository Verification

- **Purpose:** The repository's claimed state is confirmed to actually be
  reproducible, not merely assumed to be correct because it "should" be.
- **Rules:** Before and after significant operations — and always before a Release
  (`core/VVBM.md`, Stage 9) — the repository is checked out fresh from its recorded
  state and confirmed to match what is expected.
- **Common Mistakes:** Assuming a tagged release is reproducible without ever
  actually testing a fresh checkout of it.
- **Verification:** A fresh checkout of the tagged release state produces a system
  matching what was verified during Quality Gate.

---

## Relationship to Other Core Standards

- `core/VVBM.md` Stages 8 and 9 (Release Preparation, Release) are when this
  standard's Tagging, Release Management, Recovery, and Repository Verification
  topics are applied.
- `core/GS99.999.md`'s Risk Awareness principle is the general engineering
  discipline that this standard's Lowest-Risk Decision Making topic applies
  specifically to version control.
- `core/VQS.md` does not depend on any specific version-control practice; this
  standard governs the mechanics of shipping verified work, not what qualifies as
  quality.

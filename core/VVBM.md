# VVBM — Vision Verified Build Mode

**Standard type:** Core (mandatory)
**Purpose:** Defines the complete execution methodology every VESM project follows —
ten stages, in order, from locking the objective to reviewing the outcome after
release.

VVBM operationalizes the principles in `constitution/CORE_PRINCIPLES.md`,
particularly Evidence over assumptions, Verification over confidence, Architecture
over implementation, and Mission over feature creep. Where a rule here seems
arbitrary on its own, its rationale is explained there. VVBM does not restate those
principles — it defines how they are applied while doing the work.

## The Ten Stages

The stages below are followed in order, once per development cycle. No stage is
skipped, and no stage beyond these ten is added without going through
`constitution/CHANGE_POLICY.md` — the list is deliberately fixed. Several stages
sound similar to one another; each has an explicit, non-overlapping responsibility
so that VVBM does not accumulate near-duplicate rules for the same underlying idea.

---

### 1. Mission Freeze

- **Purpose:** Lock the objective and scope for this cycle before any design work
  begins.
- **Inputs:** The problem to be solved and whatever evidence supports it being worth
  solving (e.g. market or user evidence, an internal proposal, a defect report).
- **Outputs:** A completed `templates/MISSION_FREEZE_TEMPLATE.md`: a specific,
  testable statement of what is in scope and out of scope, agreed by whoever has
  authority to change it.
- **Rules:** No design or implementation may begin before this output exists. Once
  frozen, the mission changes only through a deliberate, documented re-freeze — never
  silently, mid-cycle.
- **Success Criteria:** The statement is specific enough to be checked against later,
  at Verification and Post Release Review, not just aspirational.
- **Common Mistakes:** Freezing a mission too vague to test later; treating the
  freeze as a formality rather than a real constraint on later work.
- **Verification Requirements:** The frozen mission is the reference point Quality
  Gate and Post Release Review check the finished work against — its existence and
  precision are verified there, not re-verified here.

### 2. Architecture First

- **Purpose:** Design the system's structure — components, responsibilities, data
  flow — before implementation code is written against it.
- **Inputs:** The frozen mission.
- **Outputs:** A completed `templates/ARCHITECTURE_TEMPLATE.md`: the design, the
  rationale for major decisions, and the alternatives considered and rejected.
- **Rules:** No implementation proceeds against a component whose design is not yet
  documented. If Implementation later reveals a gap in the design, the architecture
  document is updated first, before code changes to fill that gap.
- **Success Criteria:** The design is complete enough that Implementation can proceed
  without inventing structural decisions on the fly.
- **Common Mistakes:** Designing only in conversation or in one's head, without
  writing it down; over-designing beyond what the frozen mission requires.
- **Verification Requirements:** The architecture is checked for consistency with the
  frozen mission before Implementation begins.

### 3. Evidence First

- **Purpose:** Establish the standing discipline — applied continuously, not as a
  one-time deliverable — that any claim about the system's behavior, performance, or
  state must be backed by observable evidence, not assumption.
- **Inputs:** N/A — this is a continuous requirement applied throughout every other
  stage, not a discrete activity with its own inputs.
- **Outputs:** Evidence (logs, test output, reproduction steps) attached to claims
  made in every later stage.
- **Rules:** An assumption may direct where to look; it may never substitute for a
  conclusion. Fact, Assumption, and Recommendation are distinguished explicitly in
  any output that makes claims (see `ai_standard/AI_BEHAVIOR_STANDARD.md`).
- **Success Criteria:** Not assessed as its own gate — it is assessed implicitly by
  whether Investigation, Verification, and Quality Gate find evidence present when
  they check.
- **Common Mistakes:** Mistaking confidence for evidence; collecting evidence
  informally without recording it, so it cannot be checked later.
- **Verification Requirements:** Every later stage that requires evidence (4, 6, 7)
  is, collectively, the verification mechanism for this rule — it is not
  independently re-verified as a separate step.

### 4. Investigation

- **Purpose:** Diagnose unclear or broken behavior systematically before proposing a
  fix.
- **Inputs:** An observed problem or unexpected behavior.
- **Outputs:** A completed `templates/INVESTIGATION_LOG_TEMPLATE.md`, including a
  root cause supported by evidence.
- **Rules:** The full investigation procedure — verify, reproduce, identify root
  cause, test the simplest explanation first, escalate only if necessary — is
  defined once, in `ai_standard/PROBLEM_SOLVING_STRATEGY.md`, and is the sole
  authority for how this stage is carried out; it is not restated here.
- **Success Criteria:** A root cause is identified and evidenced — not merely a
  symptom addressed.
- **Common Mistakes:** Fixing symptoms instead of causes; repeating a fix that has
  already failed; skipping reproduction and diagnosing from memory or assumption.
- **Verification Requirements:** The investigation log's root-cause claim carries
  evidence, per Evidence First.

### 5. Implementation

- **Purpose:** Build the system according to the frozen architecture.
- **Inputs:** The architecture document.
- **Outputs:** A working system matching the documented architecture.
- **Rules:** Implementation never gets ahead of design — if a needed decision is not
  covered by the architecture, the architecture is updated first, in that order.
  Work outside the frozen mission's scope is not absorbed here, however easy it
  would be to add.
- **Success Criteria:** The system exists and matches the architecture document; any
  necessary deviation is reflected back into that document, not left undocumented.
- **Common Mistakes:** "While I'm in here" additions beyond the frozen mission;
  silently diverging from the documented architecture instead of updating it.
- **Verification Requirements:** Divergence between implementation and the
  architecture document is reconciled before Verification begins.

### 6. Verification

- **Purpose:** Confirm, with evidence, that the completed work does what the frozen
  mission and architecture said it would.
- **Inputs:** The implemented system, the mission, the architecture.
- **Outputs:** A completed `templates/VERIFICATION_REPORT_TEMPLATE.md`.
- **Rules:** A change without a verification report is treated as incomplete,
  regardless of the confidence of whoever built it.
- **Success Criteria:** The report shows a Pass, with each claim tied to specific,
  recorded evidence — not a general assertion that "it works."
- **Common Mistakes:** Verifying only the expected path and skipping edge cases;
  treating informal manual checking as verification without recording it.
- **Verification Requirements:** This stage *is* the verification requirement for
  Implementation. Its output is a direct input to Quality Gate.

### 7. Quality Gate

- **Purpose:** Assess the verified work as a whole against `core/VQS.md`'s quality
  dimensions — a project-level assessment, distinct from the per-change checking
  done at Verification.
- **Inputs:** Verification reports; the system as built.
- **Outputs:** A quality assessment covering every dimension defined in
  `core/VQS.md`. The specific acceptance criteria and evidence requirements for each
  dimension are defined there and are not restated here.
- **Rules:** Release Preparation does not begin until this assessment is complete.
  Gaps found here are logged as work items, not waved through.
- **Success Criteria:** Every VQS dimension has been assessed; any gap is either
  closed or explicitly and knowingly accepted, with the acceptance rationale
  recorded.
- **Common Mistakes:** Treating Quality Gate as a formality once "the real work" is
  done; skipping dimensions that are inconvenient to check, such as security.
- **Verification Requirements:** Governed entirely by `core/VQS.md`'s own
  per-dimension verification and evidence rules.

### 8. Release Preparation

- **Purpose:** Close remaining gaps and stabilize the system for release, without
  adding new scope.
- **Inputs:** Quality Gate results.
- **Outputs:** A system with all Quality Gate gaps closed or explicitly accepted, and
  release mechanics readied per `core/GIT_STANDARD.md`.
- **Rules:** New features are not accepted during this stage. Proposed new scope
  belongs to the next cycle's Mission Freeze, not this cycle's Release Preparation.
- **Success Criteria:** No open Quality Gate gap lacks a documented acceptance
  decision; a recovery/rollback path has been confirmed, not assumed.
- **Common Mistakes:** "Just one more feature" scope creep at the last minute;
  skipping recovery-path verification because release feels imminent.
- **Verification Requirements:** The recovery path is tested and confirmed per
  `core/GIT_STANDARD.md`'s Recovery and Rollback topics — not restated here.

### 9. Release

- **Purpose:** Ship the verified, stabilized system.
- **Inputs:** A completed Release Preparation stage.
- **Outputs:** A published, tagged release.
- **Rules:** Release occurs only once Release Preparation's exit criteria are met.
  The mechanics of releasing — tagging, publishing, traceability — are governed
  entirely by `core/GIT_STANDARD.md` and are not restated here.
- **Success Criteria:** The release is tagged, traceable to a specific verified
  state, and recorded in `CHANGELOG.md`.
- **Common Mistakes:** Releasing from an undocumented or unverified state; omitting
  the changelog entry.
- **Verification Requirements:** The release is confirmed reproducible from its
  tagged state, per `core/GIT_STANDARD.md`'s Repository Verification topic.

### 10. Post Release Review

- **Purpose:** Review, with evidence, whether the release achieved the frozen
  mission, and capture what was learned for future cycles.
- **Inputs:** The released system; evidence of its actual, observed outcome.
- **Outputs:** A short, evidence-based review recording whether the mission was met,
  any gap between intended and actual outcome, and lessons for future cycles.
- **Rules:** Findings that point to new work start a new Mission Freeze (Stage 1) for
  the next cycle. They are not patched into the cycle that has just closed — this
  preserves the boundary between cycles that Mission Freeze depends on.
- **Success Criteria:** The review exists, is evidence-based, and its findings, if
  any, are recorded where future cycles will find them — this is how VVBM
  operationalizes the Knowledge Preservation pillar of `core/GS99.999.md`.
- **Common Mistakes:** Skipping the review once release feels complete; treating a
  review finding as urgent enough to reopen the closed cycle instead of starting the
  next one properly, through Mission Freeze.
- **Verification Requirements:** Claims made in the review about real-world outcomes
  are themselves evidence-backed, per Evidence First.

---

## Core Rules vs. Advanced Rules

All ten stages above, and the rules stated within each, are Core Rules: mandatory for
any project claiming VVBM compliance, regardless of size or domain, and every one of
them applies at full weight in v1.0.0 — there is no Advanced-Rule variant reducing
that weight in this release. Guidance on scaling the rigor of a stage's outputs to a
project's size and risk is planned as a future Advanced Rule; see `ROADMAP.md`.

## Relationship to Other Core Standards

- `core/VQS.md` defines what Quality Gate checks for; VVBM defines only when that
  check happens in the sequence.
- `core/GS99.999.md` defines the engineering discipline behind how these stages are
  carried out — decision quality, consistency, integrity — rather than the stages
  themselves.
- `core/GIT_STANDARD.md` governs how Release and Release Preparation are technically
  carried out in version control.
- `ai_standard/PROBLEM_SOLVING_STRATEGY.md` is the sole authority for how
  Investigation (Stage 4) is performed.

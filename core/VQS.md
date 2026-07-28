# VQS — Verification Quality Standard

**Standard type:** Core (mandatory)
**Purpose:** Defines what "quality" and "release readiness" mean under VESM, and how
each is checked. VVBM's Quality Gate stage (`core/VVBM.md`, Stage 7) states *when*
this standard is applied; this document defines *what* it checks for.

VQS deliberately avoids numerical scoring. A single number obscures which dimension
actually has a problem and invites treating "quality" as one gate to clear rather
than eight distinct things to genuinely check. Each dimension below is assessed on
its own terms, with its own evidence.

## The Eight Quality Dimensions

Each dimension has a distinct, non-overlapping scope. Where two might seem to
overlap — for example, Testing and Correctness — the boundary is stated explicitly.

---

### 1. Correctness

- **Purpose:** The system does what it is specified to do, per the frozen mission
  and architecture.
- **Acceptance Criteria:** Documented, specified behavior is observed to occur;
  documented edge cases behave as specified.
- **Verification:** Verification reports from `core/VVBM.md` Stage 6, reviewed
  collectively against the full specification, not spot-checked in isolation.
- **Evidence:** Test output, reproduction steps, or direct observation tied to
  specific specified behaviors.
- **Typical Failures:** Behavior that matches the common case but diverges under
  specified edge cases; specification and implementation drifting apart silently.
- **Quality Indicators:** Every specified behavior has at least one piece of
  evidence confirming it; no known specified behavior is unaccounted for.
- **Boundary:** Correctness asks *whether the specified behavior occurs*. Testing,
  below, asks *how systematically that was checked* — the two are related but
  distinct: a system can be correct with thin evidence (weak Testing) or well-tested
  and still incorrect on an untested path.

### 2. Reliability

- **Purpose:** The system behaves consistently under expected and edge conditions,
  including repeated use and adverse conditions (e.g. bad input, resource limits,
  partial failures).
- **Acceptance Criteria:** The system does not degrade unpredictably under expected
  load or adverse but foreseeable conditions.
- **Verification:** Evidence of behavior under repeated, adverse, or boundary
  conditions — not only under a single clean run.
- **Evidence:** Logs or test output from adverse-condition runs; documented failure
  and recovery behavior.
- **Typical Failures:** Passing under ideal conditions but failing unpredictably
  under load, bad input, or partial failure of a dependency.
- **Quality Indicators:** Known failure modes have documented, predictable behavior
  (even if that behavior is "fails clearly and safely," not silent corruption).

### 3. Performance

- **Purpose:** The system meets stated performance expectations for its context.
- **Acceptance Criteria:** Stated performance expectations (if any exist for this
  project) are met, with the expectation itself documented in the architecture or
  mission, not invented at assessment time.
- **Verification:** Measurement against the stated expectation, not a general
  impression of speed.
- **Evidence:** Measured timings, resource usage, or throughput figures, compared
  against the documented expectation.
- **Typical Failures:** No performance expectation was ever stated, so "performance"
  cannot be meaningfully assessed; performance measured under unrealistic conditions.
- **Quality Indicators:** A stated expectation exists and measured behavior is
  compared directly against it.

### 4. Security

- **Purpose:** The system is free of known, addressable vulnerabilities appropriate
  to its risk profile.
- **Acceptance Criteria:** Known classes of vulnerability relevant to the system's
  context have been considered and addressed or explicitly, knowingly accepted.
- **Verification:** A documented review against relevant known vulnerability classes
  for the system's context (not a generic checklist applied regardless of context).
- **Evidence:** The review record itself, including what was checked and what was
  found.
- **Typical Failures:** No security review occurs because nothing "obviously"
  security-related was built; risk profile never established, so review scope is
  guessed rather than reasoned.
- **Quality Indicators:** A risk profile is stated, and the review scope matches it.

### 5. Maintainability

- **Purpose:** The system can be understood, changed, and extended without
  disproportionate effort.
- **Acceptance Criteria:** The architecture document (`core/VVBM.md`, Stage 2) still
  accurately describes the system as built; a practitioner unfamiliar with the
  recent history can locate the relevant part of the system from the documentation.
- **Verification:** Comparing the current architecture document against the system
  as it actually exists.
- **Evidence:** The architecture document itself, checked for drift against the
  implemented system.
- **Typical Failures:** Architecture documentation not updated as implementation
  evolved (see `core/VVBM.md` Stage 5's rule against undocumented divergence).
- **Quality Indicators:** Architecture document and implementation match; no
  undocumented structural decisions exist.

### 6. Testing

- **Purpose:** Verification coverage is proportionate to the system's risk.
- **Acceptance Criteria:** Higher-risk behavior (data loss, security, irreversible
  actions) has deeper verification coverage than low-risk behavior.
- **Verification:** A review of what has and has not been verified, mapped against
  risk, not just a count of tests.
- **Evidence:** The verification reports from `core/VVBM.md` Stage 6, plus an
  explicit statement of what was deliberately left unverified and why.
- **Typical Failures:** Coverage concentrated on what's easy to test rather than
  what's risky; no accounting of what was left unverified.
- **Quality Indicators:** Every high-risk behavior identified in the architecture has
  corresponding verification evidence.
- **Boundary:** Testing asks *how systematically the system was checked*; Correctness
  (above) asks *whether the specified behavior actually occurs*.

### 7. Documentation

- **Purpose:** The documentation a practitioner needs to use, operate, or extend the
  system exists, is accurate, and is complete.
- **Acceptance Criteria:** No placeholders, no "coming soon," no contradiction
  between documents, per `constitution/GOVERNANCE.md`'s maintenance philosophy.
- **Verification:** A read-through of the documentation set against the actual
  system, checking for gaps and inaccuracies.
- **Evidence:** The documentation itself, plus a record of what was checked against
  what.
- **Typical Failures:** Documentation describing an earlier version of the system
  that implementation has since outgrown; documentation that exists but was never
  checked against the system it describes.
- **Quality Indicators:** Documentation and system match; a new practitioner could
  use the documentation alone to understand or operate the system.

### 8. Release Readiness

- **Purpose:** Confirm that Dimensions 1–7 have all actually been checked — not
  assumed — before release.
- **Acceptance Criteria:** Every dimension above has an assessment on record, and
  every open gap has either been closed or explicitly, knowingly accepted.
- **Verification:** A single pass confirming each of the seven dimensions above has
  a completed assessment attached, per `checklists/VQS_CHECKLIST.md`.
- **Evidence:** The collected assessments and evidence from Dimensions 1–7.
- **Typical Failures:** One or more dimensions skipped under time pressure and the
  gap not noticed until after release.
- **Quality Indicators:** All eight dimensions show a completed assessment; no
  dimension is missing or marked "assumed fine."
- **Boundary:** Release Readiness does not introduce new quality criteria of its own
  — it verifies that the other seven were actually applied, not skipped.

---

## Relationship to Other Core Standards

- `core/VVBM.md` Stage 7 (Quality Gate) is when VQS is applied; VQS defines only
  what is checked, not when.
- `core/GS99.999.md` governs the discipline behind *how honestly* these assessments
  are conducted (see its Professional Integrity principle) — VQS does not restate
  that requirement here.
- `core/GIT_STANDARD.md` governs how a release is technically published once
  Release Readiness (Dimension 8) is satisfied.

# Changelog

All notable changes to VESM are documented here.
Format based on [Keep a Changelog](https://keepachangelog.com/), versioning per
`constitution/VERSION_POLICY.md`.


## [1.1.0] — Active Methodology

VESM v1.1 strengthens the methodology with explicit evidence, contract, failure-path, freeze, operational, optimization, and scaling controls.

### Added

- **Evidence-to-Claim Traceability Law** — verification claims must trace to concrete evidence.
- **Contract Boundary Verification Law** — important module boundaries are verified on both sides.
- **Failure-Path Symmetry Law** — important success paths have corresponding failure-path analysis.
- **Change-Surface Minimization Law** — corrective changes use the smallest sufficient verified surface.
- **Freeze Integrity Law** — post-freeze changes are explicitly classified.
- **Operational Reality Gate** — mathematical, implementation, adversarial, operational, and release readiness are assessed separately.
- **Verification Depth Scaling Law** — verification rigor scales with maturity and risk.
- **Performance-Without-Regression Rule** — optimization requires measured, repeatable, non-regressive improvement.
- **V1/V2 Scale Mode Boundary** — scaling begins with V2 only when measured operational evidence justifies it.
- Expanded adversarial verification and explicit uncertainty handling.

## [1.0.0] — Public Release

VESM v1.0.0 was developed component by component, each following VVBM applied to
VESM's own construction (Mission Freeze → Architecture → Implementation →
Verification), with an independent consistency and cross-reference audit performed
at the close of each component. See `releases/v1.0.0.md` for the full release
notes.

### Added

- **Constitution** (`constitution/`) — `constitution/VESM_CONSTITUTION.md`,
  `constitution/ENGINEERING_PHILOSOPHY.md`, `constitution/VISION_AND_MISSION.md`,
  `constitution/CORE_PRINCIPLES.md`, `constitution/TERMINOLOGY.md`,
  `constitution/GOVERNANCE.md`, `constitution/VERSION_POLICY.md`,
  `constitution/CHANGE_POLICY.md`.
- **Core Standards** (`core/`) — `core/VVBM.md` (ten-stage execution cycle),
  `core/VQS.md` (eight quality dimensions), `core/GS99.999.md` (eight
  engineering-discipline principles), `core/GIT_STANDARD.md` (ten vendor-neutral
  version-control topics).
- **Engineering Toolkit** — five templates (`templates/`) and four checklists
  (`checklists/`) covering every VVBM stage output and every VQS dimension.
- **AI Engineering Standard** (`ai_standard/`) — `ai_standard/AI_BEHAVIOR_STANDARD.md`
  and `ai_standard/PROBLEM_SOLVING_STRATEGY.md`, vendor-neutral behavioral
  requirements for any AI assistant participating in a VESM project.
- **Examples & Case Studies** — `examples/EXAMPLE_WALKTHROUGH.md`,
  `case_studies/CASE_STUDY_TEMPLATE.md`, `case_studies/REFERENCE_CASE_STUDY.md`.
- Root governance documents: `README.md`, `LICENSE` (CC BY 4.0), `CONTRIBUTING.md`,
  `CODE_OF_CONDUCT.md`, `ROADMAP.md`, `VERSION.md`, `releases/v1.0.0.md`.

### Changed (during development, prior to release)

- The original scaffold's `constitution/MISSION.md`, `constitution/VISION.md`,
  `constitution/PURPOSE.md` were consolidated into
  `constitution/VISION_AND_MISSION.md` and `constitution/ENGINEERING_PHILOSOPHY.md`.
- The original scaffold's `constitution/PROJECT_PHASES.md` was folded into
  `core/VVBM.md` as its ten-stage cycle, since the phase lifecycle is execution
  guidance, not a permanent constitutional principle.
- VVBM's stage list was finalized at ten stages (Mission Freeze, Architecture
  First, Evidence First, Investigation, Implementation, Verification, Quality Gate,
  Release Preparation, Release, Post Release Review), superseding an earlier
  seven-stage draft.
- VQS's dimension list was finalized at eight dimensions (adding Documentation to
  the original seven).

### Removed (scope decision for v1.0.0)

- `advanced/`, `certification/`, and `reference/` were removed from the v1.0.0
  release. All three were part of VESM's original repository design but were
  determined, on review, not to be required for an engineer to use the methodology
  today. They are recorded as v1.1 candidates in `ROADMAP.md`. Every reference to
  them from the Constitution and Core Standards was updated to reflect this —
  `constitution/VESM_CONSTITUTION.md`, `constitution/GOVERNANCE.md`,
  `constitution/TERMINOLOGY.md` (two references), and `core/VVBM.md`.

### Fixed

- A broken constitutional cross-reference in `constitution/ENGINEERING_PHILOSOPHY.md`
  to a "Market Evidence phase" that no longer existed after VVBM's stage list was
  finalized.
- Stale cross-references in `checklists/PHASE_CHECKLIST.md` and
  `checklists/RELEASE_READINESS_CHECKLIST.md` left over from the Constitution
  restructuring.
- An editing artifact in `case_studies/REFERENCE_CASE_STUDY.md`'s Lessons Learned
  section.
- All remaining `[SCAFFOLD]` and in-development status language removed
  repository-wide as part of Release Candidate preparation.

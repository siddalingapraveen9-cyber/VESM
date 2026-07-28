# Roadmap

Per VESM's own Release Discipline (`core/VVBM.md`, Stage 8–9 and
`constitution/CORE_PRINCIPLES.md`, Principle 8), v1.0.0's scope is frozen and this
document tracks **future** ideas only. Nothing below is in scope for v1.0.0, and
nothing below is a commitment — it is a record of ideas deferred rather than
absorbed into the current release, per `ai_standard/AI_BEHAVIOR_STANDARD.md`'s
Scope Control.

## Deferred from v1.0.0

These three areas were part of VESM's original repository design but were
deliberately excluded from v1.0.0 because they are not required for an engineer to
use the methodology today — see `releases/v1.0.0.md` for the "Minimum Complete
Product" reasoning behind that decision.

- **Advanced Rules** (`advanced/`) — optional, context-dependent extensions to each
  Core Standard. `constitution/GOVERNANCE.md` and each Core Standard already define
  how Advanced Rules would work; none have been written yet. A candidate example,
  noted during Core Standards development: guidance on scaling VVBM stage rigor
  (e.g., how lightweight a Mission Freeze may be) to a project's size and risk.
- **Certification** (`certification/`) — formal, checkable criteria for evaluating
  VESM compliance, beyond the process artifacts (templates, checklists) v1.0.0
  already requires.
- **Reference material** (`reference/`) — a repository-wide glossary and FAQ,
  beyond the constitutional terminology already defined in
  `constitution/TERMINOLOGY.md`.

## Other Candidate Future Versions

Ideas raised during development that were never in scope for v1.0.0 and remain
unevaluated:

- Optional companion CLI/validation tooling, kept as a separate, non-core project so
  the methodology itself remains tool-agnostic.
- Additional worked examples across different project types, beyond
  `examples/EXAMPLE_WALKTHROUGH.md` and `case_studies/REFERENCE_CASE_STUDY.md`.
- Localization of core documents.

## How an Item Moves Off This List

Per `constitution/CHANGE_POLICY.md`, an item here is only adopted into a future
version once it is proposed as a formal change and evaluated against that
document's acceptance criteria — appearing on this list is not, by itself,
approval.

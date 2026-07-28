# The VESM Constitution

## Status

This document, together with `ENGINEERING_PHILOSOPHY.md`, `VISION_AND_MISSION.md`,
`CORE_PRINCIPLES.md`, `TERMINOLOGY.md`, `GOVERNANCE.md`, `VERSION_POLICY.md`, and
`CHANGE_POLICY.md`, constitutes the **Constitution** of the Verified Engineering
System Methodology (VESM).

The Constitution is the supreme governing layer of VESM. Every Core Standard
(`core/VVBM.md`, `core/VQS.md`, `core/GS99.999.md`, `core/GIT_STANDARD.md`), every
Advanced Rule, template, checklist, and piece of guidance elsewhere in this
repository must be consistent with the Constitution. Where a conflict is found, the
Constitution prevails and the conflicting material is corrected, not the other way
around.

## Purpose of This Document

This document defines what VESM is, why it exists, what it does and does not attempt
to solve, and establishes the Constitution's authority over the rest of the
repository. It does not itself contain execution instructions — those belong to the
Core Standards — and it does not contain AI-specific instructions, which belong to
`ai_standard/`.

## What VESM Is

VESM is an engineering methodology: a disciplined, documented approach to building
software that can be applied by an individual, a team, or an organization, using any
programming language, framework, operating system, IDE, cloud provider, or AI
assistant — or none at all.

VESM is not a programming language. VESM is not an AI framework. VESM is not owned
by, or dependent on, any vendor.

## What VESM Is Not

To keep VESM's scope honest, this Constitution also states what VESM does not
attempt to be:

- VESM is not a project management framework (it does not schedule work, assign
  tasks, or manage teams).
- VESM is not a business methodology (it does not determine product-market fit,
  pricing, or go-to-market strategy).
- VESM is not a technology recommendation (it does not endorse specific languages,
  frameworks, or tools).
- VESM is not a certification of any individual's or organization's general
  competence — only of adherence to a specific, checkable set of engineering
  practices. Formal certification criteria are planned for a future release; see
  `ROADMAP.md`. In v1.0.0, adherence is evidenced by the completed artifacts the
  Core Standards and Engineering Toolkit already require (mission freezes,
  architecture documents, verification reports, and completed checklists).

## Why VESM Exists

Software engineering failures are frequently avoidable. They recur not because the
underlying technical problems are unsolvable, but because of a small, repeating set
of process failures: work starting before the objective is clear, implementation
beginning before the system is designed, claims of correctness made without
evidence, quality assessed informally or not at all, and version control operated in
ways that make mistakes irreversible.

VESM exists to give practitioners a methodology that directly counters each of these
failure modes, expressed independently of any particular technology stack, so it
remains useful as tools and vendors change.

## Authority and Precedence

Within this repository, documents are governed in the following order of authority:

1. **Constitution** (this document and its companions) — permanent, changes only
   under the process defined in `CHANGE_POLICY.md`.
2. **Core Standards** (`core/`) — mandatory, may evolve under `GOVERNANCE.md` without
   requiring constitutional change, provided they remain consistent with the
   Constitution.
3. **Advanced Rules, templates, checklists, examples, reference material** — optional
   or supporting material, may evolve more freely, provided they remain consistent
   with both the Constitution and the Core Standards.

## Amendment

This Constitution may be amended only through the process described in
`CHANGE_POLICY.md`, and only when a proposed change meets the acceptance criteria
defined there. Constitutional amendments are expected to be rare; a methodology whose
foundational principles change frequently has not yet found a stable foundation.

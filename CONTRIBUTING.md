# Contributing to VESM

VESM's contribution process follows its own governance, defined in
`constitution/GOVERNANCE.md` and `constitution/CHANGE_POLICY.md`. This document is
the practical, repository-level guide to that process — it does not redefine it.

## Before Proposing a Change

Read `constitution/CHANGE_POLICY.md`. Every proposal — whether to the Constitution,
a Core Standard, or supporting material — is checked against the six acceptance
criteria defined there. A proposal that does not yet address all six is not ready
to submit.

## How to Propose a Change

1. Open an issue describing: the problem the change addresses, the evidence that it
   recurs, the proposed change, and an assessment of the complexity it adds — the
   same structure `constitution/CHANGE_POLICY.md` requires of any proposal.
2. If the discussion supports moving forward, submit the change as a pull request
   referencing the issue.
3. The bar for approval scales with what is being changed, per
   `constitution/GOVERNANCE.md`: Advanced Rules and supporting material (templates,
   checklists, examples) are held to a lower bar than Core Rules; Core Rules are
   held to a lower bar than the Constitution itself, per
   `constitution/VESM_CONSTITUTION.md`'s statement of authority.

## Style Requirements

Every document in this repository:
- Uses vendor-neutral, technology-neutral language.
- Avoids marketing language and hype.
- Contains no placeholders, "TODO," or "coming soon" — a document is either
  complete or not yet merged.
- Cross-references other documents rather than duplicating their content, per
  `constitution/CORE_PRINCIPLES.md`, Principle 5 (Simplicity over unnecessary
  complexity).

## What Belongs Where

If you're unsure where a proposed addition belongs, `constitution/GOVERNANCE.md`'s
description of Core Rules versus Advanced Rules, and `constitution/TERMINOLOGY.md`,
are the starting points. If a proposal doesn't fit any existing document and isn't
yet ready for the current release cycle, it belongs in `ROADMAP.md` instead of a
new document, per `ai_standard/AI_BEHAVIOR_STANDARD.md`'s Scope Control.

## Versioning

Accepted changes are released according to `constitution/VERSION_POLICY.md`, and
recorded in `CHANGELOG.md`.

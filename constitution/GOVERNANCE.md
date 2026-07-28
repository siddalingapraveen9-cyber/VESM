# Governance

## Purpose of This Document

This document defines how VESM itself is governed: how rules are proposed and
approved, how Core Rules are distinguished from Advanced Rules, and the policies
covering deprecation, backward compatibility, breaking changes, and general
repository maintenance. The criteria a proposed rule must meet to be *accepted* are
defined in `CHANGE_POLICY.md`; this document defines the *process* around that
decision, not the acceptance criteria themselves.

## Core Rules vs. Advanced Rules

Every rule in a Core Standard (`core/`) is classified as either a Core Rule or an
Advanced Rule.

**Core Rules** are:
- Mandatory for any project claiming VESM compliance.
- Always applicable, regardless of project size, domain, or risk profile.
- Non-negotiable — a project may not selectively skip a Core Rule and still claim
  compliance.

**Advanced Rules** are:
- Context-dependent — applicable to some projects and not others.
- Applied only when doing so demonstrably benefits the project.
- Bound by Principle 5 (`CORE_PRINCIPLES.md`, "Simplicity over unnecessary
  complexity") — an Advanced Rule must never be adopted in a way that adds process
  cost disproportionate to its benefit.

When Advanced Rules exist, they live in `advanced/`, one file per Core Standard,
and are never merged into the Core Standard documents themselves. This separation is
intentional: a practitioner should be able to read a Core Standard in full and know
they have covered every mandatory requirement, without needing to first determine
which parts are optional. **v1.0.0 ships with no Advanced Rules** — every
requirement in the four Core Standards is a Core Rule. Advanced Rules are planned
for a future release; see `ROADMAP.md`.

## How Rules Are Proposed

A new rule — Core or Advanced — is proposed as a written change proposal that
includes: the problem it addresses, the evidence that the problem recurs, the
proposed rule text, and an assessment of the complexity it adds. The acceptance
criteria such a proposal must satisfy are defined in `CHANGE_POLICY.md`.

## How Rules Are Approved

A proposal to add or modify an **Advanced Rule** is approved once it is checked
against the `CHANGE_POLICY.md` criteria and found to satisfy them, and is
consistent with the Constitution and its own Core Standard.

A proposal to add, modify, or remove a **Core Rule** is held to the same criteria,
plus an additional requirement: because Core Rules are mandatory for every VESM
project, the evidence of a recurring problem and the case that the rule solves it
better than existing rules must be stronger, and the change must not contradict any
other Core Rule across any Core Standard.

A proposal to amend the **Constitution** itself is held to the highest bar described
in `CHANGE_POLICY.md` and is expected to be rare, per `VESM_CONSTITUTION.md`.

## Deprecation Policy

A rule, term, or document is deprecated — formally marked for future removal — before
it is removed outright, except where it is actively harmful to keep in place (for
example, a rule later found to encourage an unsafe practice). A deprecated item:

- Is marked as deprecated in place, with the reason and the replacement (if any).
- Remains valid to follow until the version in which its removal takes effect, per
  `VERSION_POLICY.md`.
- Is removed only in a release that documents the removal in `CHANGELOG.md`.

## Backward Compatibility Policy

Advanced Rules, templates, checklists, and reference material may change between
minor versions without a compatibility guarantee, since adopting them is optional.
Core Rules carry a stronger expectation of stability: a project compliant with a
given major version's Core Rules should not need structural rework to remain
compliant across minor or patch versions of the same major version. Any exception is
a breaking change and is handled accordingly.

## Breaking Change Policy

A change is a breaking change if a project or application of VESM that was
previously compliant or valid would no longer be, without modification, after the
change. Breaking changes:

- Are only made to Core Standards or the Constitution as part of a major version
  increment (see `VERSION_POLICY.md`).
- Must be documented in `CHANGELOG.md` with the specific prior behavior, the new
  behavior, and the rationale.
- Are evaluated under the same `CHANGE_POLICY.md` criteria as any other change, with
  the added requirement that the benefit must be shown to outweigh the cost imposed
  on existing compliant projects.

## Repository Maintenance Philosophy

Maintenance of the VESM repository follows the same principles VESM asks of the
projects that use it: changes are evidence-based, scope is frozen between releases,
and completion of a defined release is prioritized over continuous, unbounded
expansion. The repository's own component-by-component development — Constitution
first, then Core Standards, then supporting material — is itself an application of
`core/VVBM.md`'s Architecture First discipline, applied to VESM's own construction.

# Terminology

## Purpose of This Document

This document defines terms as they are used within the Constitution, so that
`VESM_CONSTITUTION.md`, `ENGINEERING_PHILOSOPHY.md`, `VISION_AND_MISSION.md`,
`CORE_PRINCIPLES.md`, `GOVERNANCE.md`, `VERSION_POLICY.md`, and `CHANGE_POLICY.md`
use each term consistently. It is scoped to constitutional terms. A broader glossary
covering terms used throughout the entire repository is planned for a future
release (see `ROADMAP.md`); until then, this document and each Core Standard's own
terminology are the authoritative definitions.

## Terms

**VESM (Verified Engineering System Methodology)** — The engineering methodology
defined by this repository as a whole: the Constitution, the four Core Standards, and
their supporting material.

**Constitution** — The set of eight documents in `constitution/` that together define
what VESM is, why it exists, its permanent principles, its terminology, and the
policies governing how it is governed and how it changes. The Constitution is the
highest authority in the repository, per `VESM_CONSTITUTION.md`.

**Core Standard** — One of the four mandatory standards defined in `core/`: VVBM,
VQS, GS99.999, and the Git Simplicity & Lowest-Risk Standard. Core Standards
translate constitutional principles into mandatory practice.

**Core Rule** — A rule, within a Core Standard, that is mandatory, always applicable,
and non-negotiable for any project claiming VESM compliance. See `GOVERNANCE.md` for
the full distinction from Advanced Rules.

**Advanced Rule** — A rule that extends a Core Standard but is applied only when it
is context-appropriate and beneficial; it is never assumed by default and must never
be adopted in a way that adds unnecessary complexity.

**Practitioner** — Any individual, team, or AI assistant applying VESM to engineering
work. VESM does not distinguish between human and AI practitioners in its
constitutional principles; both are held to the same standards, though additional,
AI-specific behavioral rules exist separately in `ai_standard/`.

**Mission Freeze** — The point at which a project's objective and scope are agreed
and locked for the duration of a development cycle, after which changes to that
objective are deferred rather than absorbed mid-cycle. Defined operationally in
`core/VVBM.md`; introduced as a constitutional concern by Principle 7 in
`CORE_PRINCIPLES.md`.

**Vendor Neutrality** — The property of a rule, standard, or piece of guidance that
it does not depend on any specific vendor's product, platform, or proprietary
terminology to be understood or followed.

**Compliance** — The state of a project having satisfied the Core Rules of all four
Core Standards, as evidenced by the artifacts those Standards and the Engineering
Toolkit already require (completed templates and checklists). Formal certification
criteria are planned for a future release (see `ROADMAP.md`). Compliance is a
statement about adherence to process, not a general judgment of a project's quality
or success.

**Breaking Change** — A change to a Core Standard or the Constitution that would
cause a previously compliant project or a previously valid application of VESM to no
longer be compliant or valid without modification. Governed by `VERSION_POLICY.md`
and `GOVERNANCE.md`.

**Deprecation** — The formal, announced retirement of a rule, term, or document,
distinct from its immediate removal, allowing practitioners time to adjust. Governed
by `GOVERNANCE.md`.

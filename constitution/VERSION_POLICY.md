# Version Policy

## Purpose of This Document

This document defines how VESM itself is versioned, so that practitioners can
reason about compatibility across releases of the methodology. It defines the
policy; the current version number and per-release status are tracked separately in
`VERSION.md` at the repository root, and the history of changes is recorded in
`CHANGELOG.md`.

## Versioning Scheme

VESM follows [Semantic Versioning](https://semver.org/): **MAJOR.MINOR.PATCH**.

- **MAJOR** — Incremented for a breaking change to a Core Standard or the
  Constitution, as defined in `GOVERNANCE.md`'s Breaking Change Policy. A project
  compliant with major version N is not guaranteed to remain compliant with major
  version N+1 without modification.
- **MINOR** — Incremented for backward-compatible additions: new Advanced Rules,
  templates, checklists, examples, or reference material, or non-breaking
  clarifications to a Core Standard that do not change its compliance requirements.
- **PATCH** — Incremented for corrections that do not change meaning: typo fixes,
  formatting, broken cross-references, or wording clarifications that resolve
  ambiguity without altering the underlying rule.

## What Is Versioned

The version number applies to the repository as a whole — the Constitution, the
four Core Standards, and their supporting material — not to individual documents.
A change to any one document that meets the MAJOR or MINOR threshold above triggers
a repository-wide version increment, recorded in `CHANGELOG.md`.

## Long-Term Evolution

VESM is expected to evolve as engineering practice evolves, but the Constitution is
designed to change far less frequently than the Core Standards, and the Core
Standards are expected to change less frequently than Advanced Rules, templates, and
examples. This graduated stability — from rarely-changing Constitution down to
frequently-refined supporting material — is what allows VESM to accumulate
improvements over time without destabilizing projects that already depend on it.

A major version increment is treated as a significant event, not a routine one. It
is used only when a breaking change is justified under `CHANGE_POLICY.md`'s
acceptance criteria and `GOVERNANCE.md`'s Breaking Change Policy — not as a way to
signal a large amount of new content, which is what minor versions are for.

## Pre-1.0.0 and 1.0.0 Status

Versions prior to 1.0.0 (if any exist in a given deployment of VESM) carry no
compatibility guarantee. From 1.0.0 onward, the guarantees described above apply.
The first public release of VESM is 1.0.0, as recorded in `VERSION.md`.

# Engineering Philosophy

## Purpose of This Document

This document explains the reasoning behind VESM: the philosophical stance it takes
on how good engineering happens, and the problems that stance is designed to address.
`CORE_PRINCIPLES.md` states the principles themselves; this document explains why
they were chosen.

## The Problem VESM Addresses

Most engineering failures are not caused by a lack of technical skill. They are
caused by process failures that are well known individually but frequently ignored
under time pressure:

- Work begins before the objective is agreed and fixed, so effort is spent solving
  the wrong problem or solving a problem that keeps changing shape.
- Implementation begins before the system's structure is designed, producing
  software that is difficult to reason about or change.
- Claims about what the system does are based on belief rather than evidence, so
  defects are missed or dismissed.
- Quality is assessed informally, inconsistently, or not until a project is already
  near release, when correction is most expensive.
- Version control is operated in ways that make mistakes destructive rather than
  recoverable.
- Scope expands continuously, so projects that could have finished do not.

VESM's philosophy is that these are process problems, not talent problems, and that
a disciplined, evidence-based process reduces their frequency regardless of who is
doing the work or what they are building it with.

## What VESM Deliberately Does Not Solve

A methodology that claims to solve every problem solves none of them well. VESM does
not attempt to determine whether a project is worth building, does not manage people
or schedules, does not recommend specific technologies, and does not replace domain
expertise. It assumes a project's worth has already been established — through
whatever evidence justified taking it on in the first place — and instead governs
*how* the resulting
engineering work is carried out.

## Philosophical Commitments

**Evidence over belief.** A claim about system behavior is only as good as the
evidence behind it. VESM treats unverified claims as unproven, not as false — but
also not as usable.

**Structure before substance.** Designing before implementing is not bureaucracy; it
is the cheapest point at which to catch a bad decision. The cost of a structural
mistake grows with every line of code written against it.

**Discipline as a multiplier, not an obstacle.** Process exists to make good outcomes
repeatable, not to slow work down for its own sake. Where a rule adds process cost
without improving outcomes, VESM's own principles call for removing it (see
`CORE_PRINCIPLES.md`, "Simplicity over unnecessary complexity").

**Neutrality as a requirement, not a preference.** A methodology that depends on a
particular vendor's tools stops being useful the moment that vendor's tools stop
being the right choice. VESM is written so that its guidance survives changes in
tooling, platforms, and AI providers.

**Finishing as a discipline.** An engineering practice that always defers "the
important part" to a future iteration produces systems that are perpetually
unfinished. VESM treats completion of a defined scope as a deliverable in its own
right, distinct from and no less important than adding capability.

## Relationship to Other Constitution Documents

This philosophy is realized as concrete, checkable rules in `CORE_PRINCIPLES.md`,
and those principles are in turn operationalized as mandatory practice in the Core
Standards (`core/`). This document exists so that when a Core Standard rule seems
arbitrary in isolation, its origin can be traced back to the reasoning here.

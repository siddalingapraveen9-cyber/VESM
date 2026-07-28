# Change Policy (Rule Evolution Policy)

## Purpose of This Document

This document defines the criteria a proposed change must satisfy to be accepted
into VESM, at any level — Constitution, Core Standard, or supporting material. It
is the acceptance test referenced by `GOVERNANCE.md`'s description of how rules are
proposed and approved.

## Acceptance Criteria

A proposed new or modified rule is accepted only if it satisfies **all** of the
following:

1. **It solves a recurring engineering problem.** A rule addressing a one-off
   situation belongs in a project's own documentation, not in VESM.
2. **It is supported by practical evidence.** The proposal must point to concrete
   instances — not hypothetical ones — where the absence of this rule caused or
   contributed to a problem.
3. **It does not duplicate an existing rule.** If an existing Core Rule, Advanced
   Rule, or constitutional principle already addresses the problem, the proposal
   should refine that existing rule rather than add a new, overlapping one.
4. **It does not contradict the Constitution.** Every rule must be traceable to one
   or more principles in `CORE_PRINCIPLES.md`; a rule that conflicts with a
   constitutional principle is rejected regardless of its other merits.
5. **It improves engineering quality more than it increases complexity.** This is a
   judgment call made explicit in the proposal itself: the proposer must state the
   complexity cost (process steps added, cognitive load, tooling required) and argue
   that the quality benefit exceeds it. Principle 5 (`CORE_PRINCIPLES.md`,
   "Simplicity over unnecessary complexity") governs this judgment.
6. **It includes a clear purpose, rationale, examples, and verification criteria.**
   A rule that cannot be explained, justified, illustrated, and checked is not yet
   ready to be adopted, however good the underlying idea may be.

## Additional Bar for Core Rules and Constitutional Amendments

Criteria 1–6 apply to every proposal. Proposals to add or change a **Core Rule**
must additionally demonstrate that the problem is common enough, and severe enough,
to justify making the rule mandatory for every VESM project rather than optional as
an Advanced Rule.

Proposals to amend the **Constitution** must additionally demonstrate that the
change reflects a principle intended to be permanent — not a rule specific to a
technology, a project type, or a point in time — since constitutional content is
held to the standard described in `VESM_CONSTITUTION.md` and `VERSION_POLICY.md`:
changed rarely, and only when the case for permanence is clear.

## What Happens to Rejected Proposals

A proposal that does not meet these criteria is not accepted, but is not necessarily
discarded. If it identifies a real but narrow or project-specific problem, it may be
retained as an example or case study (`examples/`, `case_studies/`) rather than as a
rule — demonstrating a good practice without imposing it universally. If it
describes a capability outside VESM's current scope entirely, it is recorded in
`ROADMAP.md` for future consideration rather than adopted immediately.

## Relationship to Governance

This document defines *what* is accepted. `GOVERNANCE.md` defines *who* decides and
*how* the decision is recorded, including the distinction between Core and Advanced
Rules, deprecation, and backward-compatibility handling for accepted changes.

# Problem Solving Strategy

**Standard type:** Supporting standard (the sole authority for how Investigation is
performed)
**Purpose:** Defines the diagnostic workflow followed whenever behavior is unclear,
unexpected, or broken. This is the authoritative procedure referenced by
`core/VVBM.md` Stage 4 (Investigation) and by
`ai_standard/AI_BEHAVIOR_STANDARD.md`'s Failure Recovery and Prohibited Behaviors
sections — neither restates it.

This document describes principles applicable across technologies and problem
types. It does not prescribe one specific debugging technique, tool, or language;
each step below is a requirement on *what* must happen, not *how* to do it in any
particular stack.

## The Workflow

Steps are followed in order. A step is not skipped because the cause "seems
obvious" — obvious causes are exactly the ones worth confirming quickly, not
skipping.

### 1. Understanding the Problem

Restate the problem in your own words before acting, and confirm that restatement
matches what was actually reported or observed. A problem solved quickly but
incorrectly understood is not solved.

### 2. Separating Facts from Assumptions

Apply the Fact / Assumption / Inference / Recommendation / Unknown distinction from
`ai_standard/AI_BEHAVIOR_STANDARD.md` to the problem itself: what is actually known
to be true about it, versus what is currently assumed. This separation is not
restated here — the distinction is defined once, there.

### 3. Gathering Evidence

Collect logs, output, and relevant context before forming a hypothesis. A hypothesis
formed before evidence is gathered tends to shape which evidence gets noticed
afterward — evidence comes first.

### 4. Reproducing the Issue

Establish a reliable way to trigger the problem. A problem that cannot be
reproduced cannot be reliably confirmed fixed later, at Verification
(`core/VVBM.md`, Stage 6) — reproduction is what makes that later confirmation
possible.

### 5. Root-Cause Analysis

Trace the problem to its underlying cause, not merely the symptom that was
reported. A fix that addresses a symptom without addressing its cause tends to
resurface, in the same or a different form.

### 6. Ranking Hypotheses

When more than one explanation is plausible, rank them by how well each fits the
gathered evidence and how simple each is — not by which is most interesting to
investigate. Test the most likely, simplest explanation first.

### 7. Selecting the Smallest Verified Change

Once a root cause is confirmed, prefer the smallest change that addresses it. A
smaller change is easier to verify completely and carries less risk (see
`core/GS99.999.md`, Risk Awareness) than a larger change that happens to also fix
the problem.

### 8. Verifying Outcomes

Confirm the change resolves the original reproduction case, and confirm it has not
broken previously verified behavior. Record this using
`templates/VERIFICATION_REPORT_TEMPLATE.md`, per `core/VVBM.md` Stage 6 — the
verification procedure itself is defined there, not here.

### 9. Knowing When to Stop

The investigation concludes once the root cause is identified and evidenced, and the
fix is verified. Continuing to explore beyond that point is scope expansion, not
diligence — see `ai_standard/AI_BEHAVIOR_STANDARD.md`'s Scope Control.

### 10. Escalating Only When Necessary

Escalate — to a human practitioner, or to a broader investigation — only after the
simplest plausible explanations have actually been tested and ruled out, not by
default and not at the first sign of difficulty.

### 11. Recognizing Repeated Failures and Changing Strategy

If the same class of fix fails more than once, stop repeating variations of it.
Return to Step 2 and reassess the underlying assumptions — the root cause identified
in Step 5 may itself have been wrong. Continuing to retry a failing approach without
reassessment is an instruction loop, not persistence.

## Relationship to Other Documents

- `core/VVBM.md` Stage 4 (Investigation) is when this workflow is applied; this
  document defines only what that stage requires, not when it occurs in the larger
  cycle.
- `ai_standard/AI_BEHAVIOR_STANDARD.md`'s Evidence Requirements define the Fact /
  Assumption / Inference / Recommendation / Unknown distinction used in Step 2, and
  its Failure Recovery section states the expected behavior — ask rather than guess
  — when Step 11's repeated-failure condition is met.
- `templates/INVESTIGATION_LOG_TEMPLATE.md` and `templates/VERIFICATION_REPORT_TEMPLATE.md`
  are where the outputs of this workflow are recorded.

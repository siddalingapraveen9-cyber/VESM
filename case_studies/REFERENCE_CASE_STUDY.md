# Reference Case Study — Standardizing Response Timestamp Formatting

**Format:** Follows `case_studies/CASE_STUDY_TEMPLATE.md`. Deliberately a different,
independent scenario from `examples/EXAMPLE_WALKTHROUGH.md`, so the two documents
demonstrate the methodology rather than the same story twice: the walkthrough shows
the *process* in narrative detail; this case study shows the *documentation format*
applied to a finished project.

## Project Summary

A small internal API returned response timestamps in two different formats
depending on which endpoint was called — some as ISO 8601 strings, some as Unix
epoch numbers — because each endpoint had been implemented separately over time,
without a shared formatting component. Client applications occasionally
mis-parsed one format expecting the other.

## Problem Statement

Timestamp formatting was inconsistent across endpoints, with no single point in the
system responsible for it, causing intermittent client-side parsing errors.

## Constraints

- Existing clients depended on the current per-endpoint formats; a hard breaking
  change was not acceptable.
- Engineering time allocated to this fix was limited — a full API redesign was not
  in scope.

## Mission Freeze

- **In scope:** Standardize all endpoints in the current API version on ISO 8601
  formatting, with a transition period for clients still expecting epoch format.
- **Out of scope:** Any change to response fields other than timestamp formatting;
  any change to API versions other than the current one.
- **Success criteria:** Every endpoint in the current version returns ISO 8601 by
  default, with epoch format available only via an explicit, documented opt-in
  during the transition period.
- **Frozen by:** API team lead.

## Architecture Decisions

A single shared response-formatting utility was introduced, used by every endpoint,
replacing each endpoint's independent formatting code.

- **Alternative considered:** Fixing each endpoint's formatting independently.
  Rejected — it would not prevent the same inconsistency from recurring as new
  endpoints were added, and violates `core/GS99.999.md`'s Consistency principle
  (the same standard should be enforced structurally, not endpoint by endpoint).

## Investigation Summary

This was not a single defect with one root cause, but structural drift: no shared
formatting component had ever existed, so each endpoint's author made an
independent, reasonable-seeming choice at the time it was written. An audit of every
endpoint's response-formatting code (a Fact-gathering step, not an assumption)
confirmed this — no endpoint was "wrong" in isolation; the absence of a shared
standard was the cause.

## Evidence

- A complete audit of all current-version endpoints' response formatting code,
  recording which format each used.
- Before-and-after sample responses from every endpoint, confirming consistent
  ISO 8601 output after the change.

## Verification

- **Claim:** Every current-version endpoint returns ISO 8601 timestamps by default.
- **Method:** Each endpoint was called directly and its response format checked.
- **Evidence:** Sample responses from all endpoints, confirming consistent format.
- **Additional check:** The epoch-format opt-in was tested to confirm existing
  clients using it were unaffected during the transition period.
- **Result:** Pass.

## Quality Review

| Dimension | Assessment |
|---|---|
| Correctness | All endpoints verified to return ISO 8601 by default. |
| Reliability | Confirmed under the opt-in path as well as the default path. |
| Performance | No measurable change — formatting cost is negligible relative to request handling. |
| Security | N/A — no security-relevant surface touched. |
| Maintainability | A single shared utility now governs formatting, reducing future drift. |
| Testing | Regression check added covering both default and opt-in formats. |
| Documentation | API documentation updated to describe the default format and the transition-period opt-in. |
| Release Readiness | All above assessed; transition-period messaging confirmed accurate. |

## Release Outcome

Released as a minor version. The changelog documented the new default format, the
opt-in mechanism for the transition period, and the date the opt-in would be
removed in a future major version, per `constitution/VERSION_POLICY.md`.

## Lessons Learned

- Structural drift — many individually reasonable decisions producing an
  inconsistent whole — is a distinct failure mode from a single defect, and was
  only visible once the endpoints were audited together rather than one at a time.
- The team proposed, for `constitution/CHANGE_POLICY.md` consideration, that
  Architecture First (`core/VVBM.md`, Stage 2) explicitly checks new endpoints
  against existing shared utilities before introducing new, independent
  implementations of shared concerns. This proposal was recorded for future
  evaluation, not adopted within this project's cycle, per
  `ai_standard/AI_BEHAVIOR_STANDARD.md`'s Scope Control.

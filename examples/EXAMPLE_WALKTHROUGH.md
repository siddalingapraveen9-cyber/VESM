# Example Walkthrough

**Purpose:** Demonstrate VESM applied to one complete, small project, start to
finish. This document introduces no new rules — every step below is an application
of an existing stage in `core/VVBM.md`, and each section names the stage it
corresponds to. The scenario is kept deliberately small and technology-neutral so
the focus stays on the workflow, not the implementation details of any particular
stack.

**Scenario:** A support team reports that a weekly summary report occasionally
shows duplicate line items for the same record.

---

## 1. Project Request

A support team member reports: "The weekly summary report sometimes lists the same
order twice, with the same total counted both times. It doesn't happen every week."
No further engineering work begins yet — this report is the input to Mission
Freeze, not a mission in itself (per `core/VVBM.md`, Stage 1).

## 2. Mission Freeze

*(`core/VVBM.md`, Stage 1 — recorded via `templates/MISSION_FREEZE_TEMPLATE.md`)*

- **Problem statement:** The weekly summary report occasionally duplicates a line
  item, inflating its counted total.
- **In scope:** The report generation logic that produces the weekly summary.
- **Out of scope:** Any broader redesign of the reporting system; other reports are
  not in scope unless the same root cause is confirmed to affect them.
- **Success criteria:** The reproduction case (see Investigation) no longer produces
  a duplicate line item, and a regression check confirms other report output is
  unaffected.
- **Frozen by:** Engineering lead, on the date this mission was agreed.

## 3. Architecture Review

*(`core/VVBM.md`, Stage 2 — recorded via `templates/ARCHITECTURE_TEMPLATE.md`)*

The report generator retrieves records in fixed-size pages from the data source and
appends each page's rows to the report. No redesign is needed for this fix; the
existing structure is documented as-is so the affected component (the paging logic)
is clearly identified before any change is made:

- **Components and responsibilities:** A query component fetches one page of
  records at a time; a formatting component appends each page's rows to the report
  output.
- **Alternatives considered:** Rewriting the report generator to fetch all records
  in a single query. Rejected for this cycle — it would exceed the frozen mission's
  scope and is unrelated to the reported symptom.

## 4. Investigation

*(`core/VVBM.md`, Stage 4, following `ai_standard/PROBLEM_SOLVING_STRATEGY.md`;
recorded via `templates/INVESTIGATION_LOG_TEMPLATE.md`)*

- **Reproduction:** The duplicate was reproduced by generating a report over a
  dataset whose record count is an exact multiple of the page size.
- **Facts vs. assumptions:** It was initially *assumed* the data source itself
  returned duplicate rows. Checking the raw query output (a Fact, not an assumption)
  showed no duplication at the source — the duplication was introduced after
  retrieval.
- **Root cause:** The paging logic used an inclusive boundary on both the start and
  end of each page, so the last row of one page was fetched again as the first row
  of the next page whenever a page boundary fell exactly on a record.
- **Simplest explanation tested first:** Before examining the formatting component,
  the simpler and more likely explanation — a boundary condition in paging — was
  tested first, per `ai_standard/PROBLEM_SOLVING_STRATEGY.md`, Step 6. It matched
  the evidence and was confirmed.

## 5. Implementation

*(`core/VVBM.md`, Stage 5)*

The smallest verified change was selected, per
`ai_standard/PROBLEM_SOLVING_STRATEGY.md`, Step 7: the page boundary was corrected
to be inclusive on the start and exclusive on the end, so each record is fetched by
exactly one page. No other part of the report generator was changed, consistent
with the frozen mission's scope.

## 6. Verification

*(`core/VVBM.md`, Stage 6 — recorded via `templates/VERIFICATION_REPORT_TEMPLATE.md`)*

- **Claim:** The reproduction case no longer produces a duplicate line item.
- **Method:** The exact dataset used in Investigation was re-run through the
  corrected report generator.
- **Evidence:** Output compared row-by-row against the expected record count; no
  duplicate rows present.
- **Additional check:** Reports over datasets *not* an exact multiple of the page
  size were also re-run, to confirm the fix did not drop the final partial page.
- **Result:** Pass.

## 7. Quality Assessment

*(`core/VVBM.md`, Stage 7, per `checklists/VQS_CHECKLIST.md`)*

| Dimension | Assessment |
|---|---|
| Correctness | Verified against the reproduction case and additional edge cases (partial final page). |
| Reliability | Confirmed across multiple dataset sizes, not only the original reproduction case. |
| Performance | Unaffected — the change alters a boundary condition, not the paging approach itself. |
| Security | N/A — no security-relevant surface touched. |
| Maintainability | Architecture document (Section 3, above) updated to note the corrected boundary rule. |
| Testing | A regression check covering the exact-multiple and partial-page cases was added. |
| Documentation | This walkthrough and the linked investigation log serve as the record. |
| Release Readiness | All above assessed; no open gaps. |

## 8. Release Preparation

*(`core/VVBM.md`, Stage 8, per `checklists/RELEASE_READINESS_CHECKLIST.md`)*

- Mission unchanged since freeze.
- `checklists/VQS_CHECKLIST.md` completed with no unresolved item.
- `checklists/GIT_SAFETY_CHECKLIST.md` completed: the fix is a single, self-contained
  commit that can be reverted independently if needed.
- `CHANGELOG.md` entry drafted.
- No new scope was accepted during this stage — a second, unrelated reporting
  question raised by the support team was noted for a future Mission Freeze rather
  than absorbed here.

## 9. Release Decision

*(`core/VVBM.md`, Stage 9, per `core/GIT_STANDARD.md`)*

The fix was released as a patch version, tagged, with the changelog entry
describing the corrected behavior. The release was confirmed reproducible from a
fresh checkout of the tagged commit before being published, per
`core/GIT_STANDARD.md`'s Repository Verification topic.

## 10. Lessons Learned

*(`core/VVBM.md`, Stage 10 — Post Release Review)*

- The duplicate no longer occurred in the following week's report generation,
  confirming the fix held under real data, not only the constructed reproduction
  case.
- The initial, incorrect assumption (that duplication originated at the data
  source) cost time before the Fact/Assumption distinction in
  `ai_standard/AI_BEHAVIOR_STANDARD.md` was applied to separate what had actually
  been checked from what had only been suspected.
- This recurring type of boundary-condition defect was noted as a candidate for a
  proposed Advanced Rule (per `constitution/CHANGE_POLICY.md`) recommending
  boundary-condition checks specifically during Architecture Review for any
  component that pages through data — a decision for a future cycle, not acted on
  within this one, per Continuous Improvement (`core/GS99.999.md`).

---

## What This Walkthrough Demonstrates

Every section above corresponds to an existing `core/VVBM.md` stage; no new stage,
rule, or principle was introduced to produce it. The templates and checklists
referenced throughout are the same ones defined in `templates/` and `checklists/`,
used exactly as specified there.

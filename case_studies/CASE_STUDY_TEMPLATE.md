# Case Study — Template

**Purpose:** A reusable format for documenting a real project carried out under
VESM, for reference by future practitioners. Distinct from `examples/EXAMPLE_WALKTHROUGH.md`
(a single illustrative walkthrough of the workflow itself) — this template is for
recording *actual* completed projects, of which there may be many over time.
**When to Use:** After a project reaches Post Release Review (`core/VVBM.md`,
Stage 10), to record it as a durable reference.
**Instructions:** Fill every Required Field using the project's actual artifacts
(its completed templates and checklists) as the source — do not reconstruct details
from memory. Link to those artifacts rather than re-describing them at length.

## Required Fields

- **Project summary:**
- **Problem statement:**
- **Constraints** (time, risk tolerance, compatibility, or other limits that shaped
  the decisions below):
- **Mission Freeze** (link to or summarize `templates/MISSION_FREEZE_TEMPLATE.md`
  output):
- **Architecture decisions** (link to or summarize `templates/ARCHITECTURE_TEMPLATE.md`
  output, including alternatives rejected and why):
- **Investigation summary** (link to or summarize `templates/INVESTIGATION_LOG_TEMPLATE.md`
  output, if the project involved diagnosing a defect):
- **Evidence** (what was checked, and how, to support the claims made in
  Verification and Quality Review below):
- **Verification** (link to or summarize `templates/VERIFICATION_REPORT_TEMPLATE.md`
  output):
- **Quality review** (summary of the `checklists/VQS_CHECKLIST.md` assessment):
- **Release outcome** (link to `templates/RELEASE_CHECKLIST_TEMPLATE.md` output;
  what shipped and when):
- **Lessons learned** (per `core/VVBM.md` Stage 10; anything proposed for
  `constitution/CHANGE_POLICY.md` or `ROADMAP.md` as a result):

## Optional Fields

- **Team size and roles:**
- **Duration:**
- **Related case studies:**

## Completion Criteria

- Every Required Field is filled, sourced from actual project artifacts.
- No detail is invented or reconstructed without an underlying record.
- Lessons Learned states, explicitly, whether anything from this project warrants a
  proposed change under `constitution/CHANGE_POLICY.md`.

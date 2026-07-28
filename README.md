# VESM — Verified Engineering System Methodology

**Version 1.0.0** — a complete, vendor-neutral engineering methodology.

## What VESM Is

VESM is a vendor-neutral engineering methodology for building software with maximum
engineering discipline. It is not a programming language, not an AI framework, and
not tied to any vendor, IDE, or cloud provider. It can be applied with any AI
assistant, any combination of tools, or with no AI at all.

## Why VESM Exists

VESM exists to reduce avoidable engineering failures by replacing guesswork with
disciplined execution — mission clarity, architecture-first design, evidence-driven
engineering, structured verification, high-quality releases, and low-risk version
control. See `constitution/ENGINEERING_PHILOSOPHY.md` for the full reasoning.

## The Four Core Standards

| Standard | Purpose | Location |
|---|---|---|
| **VVBM** — Vision Verified Build Mode | The ten-stage cycle every project executes | `core/VVBM.md` |
| **VQS** — Verification Quality Standard | Eight dimensions defining quality and release readiness | `core/VQS.md` |
| **GS99.999** — Gold Standard | Eight principles of engineering discipline and character | `core/GS99.999.md` |
| **Git Simplicity & Lowest-Risk Standard** | Ten vendor-neutral version-control principles | `core/GIT_STANDARD.md` |

Every requirement in the four Core Standards is a Core Rule in v1.0.0: mandatory,
regardless of project size or domain. (Optional, context-dependent Advanced Rules
are planned for a future release — see `ROADMAP.md`.)

## Repository Map

```
VESM/
├── README.md                  You are here
├── LICENSE                     CC BY 4.0
├── CHANGELOG.md                Dated log of changes, by release
├── CONTRIBUTING.md             How to propose changes to VESM
├── CODE_OF_CONDUCT.md
├── ROADMAP.md                  Planned future versions (not part of v1.0.0 scope)
├── VERSION.md                  Current version and versioning scheme
├── constitution/                What VESM is, why, and its permanent principles (8 docs)
├── core/                        The four mandatory Core Standards — the "how" (4 docs)
├── templates/                   Fill-in-the-blank documents used during a project (5 docs)
├── checklists/                  Objectively-verifiable readiness checklists (4 docs)
├── ai_standard/                 Behavioral requirements for any participating AI assistant (2 docs)
├── examples/                    A full worked walkthrough of the methodology (1 doc)
├── case_studies/                Case study format plus one filled reference case study (2 docs)
└── releases/                    Per-version release notes
```

## How to Use This Repository

1. Read the eight documents in `constitution/` — starting with
   `constitution/VESM_CONSTITUTION.md` and `constitution/VISION_AND_MISSION.md` —
   to understand what VESM is, why it exists, and its permanent principles.
2. Read the four documents in `core/` — these are mandatory for any project
   claiming VESM compliance.
3. Read `examples/EXAMPLE_WALKTHROUGH.md` to see the Core Standards applied
   end-to-end on a small, technology-neutral example.
4. Use `templates/` and `checklists/` as the working documents for your own
   project.
5. If an AI assistant is participating, have it read `ai_standard/` — its
   requirements apply in addition to, not instead of, the Core Standards.
6. When your project is complete, document it using
   `case_studies/CASE_STUDY_TEMPLATE.md` — see
   `case_studies/REFERENCE_CASE_STUDY.md` for a filled example.

## Status of This Release

v1.0.0 is a complete, production-ready public release: every document above is
finished, with no placeholders and no unresolved cross-references. See
`releases/v1.0.0.md` for the full release notes, including what was deliberately
left out of this release and why, and `CHANGELOG.md` for the detailed history.

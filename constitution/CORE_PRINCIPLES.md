# Core Principles

## Purpose of This Document

This document states the permanent principles of VESM. They are the standard against
which every Core Standard, Advanced Rule, template, and checklist in this repository
is checked for consistency, per `VESM_CONSTITUTION.md`'s statement of authority. They
are expected to almost never change; see `CHANGE_POLICY.md` for the process required
to alter one.

Each principle is stated as a preference between two things VESM values, because
engineering is a practice of tradeoffs — stating only the preferred side without its
alternative would misrepresent principles as absolutes rather than defaults.

## The Principles

### 1. Evidence over assumptions
Claims about what a system does, or why a problem occurred, must be supported by
observable evidence — reproduction steps, logs, test output — rather than asserted
from belief or precedent. An assumption may guide investigation; it may not stand in
for a conclusion.

### 2. Verification over confidence
Confidence that something works is not the same as having verified that it works.
VESM treats a fix or feature as incomplete until it has been verified, regardless of
how certain the person or AI assistant performing the work feels about it.

### 3. Architecture over implementation
The structure of a system is designed before it is built. Implementation without a
preceding architectural decision produces systems that are expensive to understand
and change, even when each individual piece of code is well written.

### 4. Correctness over speed
Where correctness and speed are in tension, correctness is chosen. Speed gained by
skipping verification is a debt that is typically repaid, with interest, later in
the project.

### 5. Simplicity over unnecessary complexity
The simplest approach that correctly meets the mission is preferred. Complexity is
added only when it is justified by a demonstrated need, never by default or for its
own sake — this is why VESM separates mandatory Core Rules from optional Advanced
Rules (see `GOVERNANCE.md`).

### 6. Reproducibility over convenience
A result — a build, a test outcome, a deployment — should be reproducible by someone
other than the person who first produced it, using the documented process. A
convenient shortcut that only the original author can repeat is not an acceptable
substitute.

### 7. Mission over feature creep
Work is evaluated against the frozen mission it was undertaken to serve. Additional
capability that does not serve that mission is deferred to a future version rather
than absorbed into the current one, regardless of how easy it would be to add.

### 8. Completion over endless expansion
A defined scope, finished and verified, is preferred to an ever-expanding scope that
never reaches a stable, releasable state. Finishing is treated as a deliverable, not
as an afterthought once "real" work is done.

### 9. Lowest-risk engineering decisions
Where multiple approaches would satisfy the mission, the approach with the lowest
risk of irreversible harm — to the system, its data, or its history — is preferred,
even where a higher-risk approach would be marginally faster or more convenient.

### 10. Vendor neutrality
No principle, Core Standard, or rule may depend on a specific vendor's product,
platform, or terminology in order to be followed. Guidance is written so it remains
valid as tools and vendors change.

### 11. Engineering integrity
Problems, limitations, and shortcuts are disclosed accurately, not concealed or
minimized. A methodology built on evidence is only as trustworthy as the honesty of
the evidence reported under it.

## How These Principles Are Applied

These principles are intentionally general; they are not, by themselves, checkable
process steps. They are made checkable by the Core Standards in `core/`, which
translate each principle into specific, mandatory practice (for example, Principle 2
becomes the Verification stage of `core/VVBM.md` and the criteria of
`core/VQS.md`). Where a Core Standard or Advanced Rule cannot be traced back to one
or more of these principles, it does not belong in VESM.

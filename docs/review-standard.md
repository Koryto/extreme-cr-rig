# Review Standard
<!-- VERSION: 1.0 | STATUS: initial release -->

## Purpose

Define the common review language used by all reviewer agents and the lead agent.

This is the normative review standard for `extreme-cr-rig`.

## Objective

Review the change as if it will become part of a long-lived production codebase.

The goal is not agreement or politeness.
The goal is to surface real risk early and express it in a format the lead agent can synthesize.

## Review Areas

### 1. Correctness and Regression Risk

- logic bugs
- broken invariants
- missing edge-case handling
- behavior drift from the intended change
- lifecycle, state-transition, concurrency, and partial-failure regressions

### 2. Scale

Scale is always a top-level concern.

- reject designs that do not scale to the expected workload
- look for repeated expensive scans, hot-path inefficiencies, chatty external calls, poor caching boundaries, and avoidable serialization/deserialization churn
- call out unclear scale assumptions explicitly

### 3. Industry Standards and Best Practices

- prefer established, defensible patterns over clever local shortcuts
- check alignment with the language, framework, and platform's normal production patterns
- if unsure, validate best-practice claims against primary sources or official documentation before asserting them

### 4. Extendability and Maintainability

- hidden coupling
- weak ownership boundaries
- poor abstractions
- ad hoc one-off logic
- missing documentation for non-trivial behavior
- over-documentation that obscures intent

### 5. Production-Grade Rigor

- do not waive low-severity debt just because the code "works"
- sloppy cleanup paths
- weak failure handling
- partial implementations disguised as complete
- convenience hacks that create future cost

### 6. Architecture and Ownership

- project invariant violations
- responsibilities in the wrong layer
- mixed authority
- duplicate ownership
- compatibility hacks that look permanent

### 7. Verification and Documentation Gaps

- weak or missing verification for risky paths
- unverified critical flows
- missing durable documentation updates when they are clearly needed

## Output Contract

The output must be findings-first.

### If Findings Exist

List findings ordered by severity.

Each finding should include:

- severity
- concise title
- why it matters
- evidence
- recommended fix direction

Use this shape:

```md
1. High - Description of the issue
   Why it matters: ...
   Evidence: ...
   Fix direction: ...
```

### If No Findings Exist

State explicitly:

`No findings.`

Then list any residual risks or verification gaps if they remain.

## Severity Guidance

- `High`: likely bug, regression, non-scalable design, broken invariant, or production risk that should be fixed before acceptance
- `Medium`: important weakness that should usually be fixed before acceptance unless consciously traded off
- `Low`: quality issue or debt that is not immediately blocking but should still be called out

## Between-Round Follow-Up

When reviewing a later round, each reviewer should also track the status of prior findings they raised:

- resolved
- still open
- deferred with acceptable reason
- deferred but unsatisfactory

Do not repeat previously rejected findings unless new evidence exists.

## Rules

Always:

- prioritize defects and architectural risks over summary
- be explicit when a point is inferred rather than directly evidenced
- call out scale risks even when the code is otherwise correct
- keep findings structured and synthesizable

Never:

- lead with praise
- bury findings under a long summary
- restate prior rejected findings without new evidence
- confuse review with verification


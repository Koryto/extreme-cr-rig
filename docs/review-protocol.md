# Review Protocol
<!-- VERSION: 1.1 | STATUS: hardened draft -->

## Purpose

Define the core review loop independently from any communication platform.

This protocol is the engine of `extreme-cr-rig`.

## Actors

- Human
- Lead agent
- Review agents

## Review Modes

### Standard Round

Standard rounds are the default.

Use them when the review still has meaningful finding volume or structural uncertainty.

### Quick Round

Quick rounds are allowed when the branch is already near merge and only low-signal follow-up remains.

Typical quick-round cases:

- no-findings confirmation
- doc-only cleanup
- one low-severity issue

Quick rounds should reduce ceremony, not remove rigor.

## Inputs

Each review round should start with:

- exact review scope
- exact reviewed state
- relevant project rules and constraints
- relevant design or system context
- expected reviewer roster
- human-owned merge criteria when relevant
- explicit out-of-scope items when relevant

Reviewers must verify the current file state before writing findings.

Diff-only review is not sufficient on its own.

## Required Round Artifacts

Every round must have:

- `00_round_context.md`
- `reviewers/`
- `60_round_verdict.md`

Every non-initial round must also have:

- `10_previous_round_feedback.md`

Standard rounds should produce:

- `lead/20_reviewer_feedback.md`
- `lead/30_round_results.md`

Quick rounds may skip `lead/20_reviewer_feedback.md` when there is no meaningful carry-forward value for another round.

Verification artifacts are expected whenever fix batches or manual validation occur.

## Round Phases

### 1. Round Start

The lead creates the round and populates required context with human guidance.

Reviewers should not begin until the round has:

- populated scope
- reviewed-state information
- reviewer roster
- non-initial carry-forward when applicable

### 2. Independent Review

Each review agent performs an independent review and emits findings using `review-standard.md`.

Before reviewing a new round, each reviewer should read the previous round carry-forward artifacts when they exist.

The reviewer is expected to:

- verify the live file state before writing findings
- check whether prior concerns were resolved
- avoid repeating rejected findings without new evidence
- explicitly track the status of earlier findings they raised
- remain in the rig even after reaching `No findings.`

When a reviewer has no more findings, that reviewer enters lightweight follow-up mode:

- validate prior concerns were fixed or deferred correctly
- watch for regressions introduced by fix batches
- avoid re-running a heavy cold review unless asked

### 3. Lead Pass

The lead agent ingests reviewer outputs and performs one internal synthesis pass.

Reviewer-facing classifications should use:

- `accepted`
- `duplicate`
- `stale`
- `rejected`
- `deferred`
- `non-actionable`

The lead should then produce:

- one reviewer-facing artifact
- one human-facing round-results artifact

### 4. Human Review

The human reviews the human-facing round-results artifact, not every internal lead substep.

The human interaction point here is:

- approve the round results and execution plan
- reject it and request another lead pass
- override any disputed lead judgment

### 5. Fix And Verification

Accepted work is implemented and verified.

Each batch should be small enough to:

- implement safely
- verify meaningfully
- isolate regressions when they appear

### 6. Re-Review

After all batches are complete, review is re-run on:

- changed areas
- impacted hotspots
- unresolved findings

Quick rounds may collapse this into a lighter closeout pass when only tiny follow-up work remains.

### 7. Human Verdict

Every finished round is closed.

The actual human decision is only:

- `merge`
- `another_round`

The verdict file should record:

- that the round is closed
- the human verdict
- remaining risks
- next action

## Review Standard

All reviewer agents and the lead agent must use `review-standard.md`.

## Protocol Rules

- the lead agent is the only synthesis authority
- review agents are signal producers, not coordinators
- the human owns disputed findings, merge criteria, and the final `merge` / `another_round` judgment
- fixes should be batched, not collapsed into one giant remediation pass
- reviewers must consume prior round feedback before starting another round
- repeated findings should be justified as still-open or newly evidenced, not restated blindly
- non-initial rounds should not start without carry-forward artifacts
- a missing reviewer submission must be made explicit by the lead before the round proceeds
- a round may proceed with partial reviewer submissions only if the lead records that fact and the human accepts it
- verification should be written into artifacts, not left only in chat

## Non-Goals

- enforcing one specific transport
- forcing one specific model vendor
- replacing human approval

## AND IT. IS. ON.

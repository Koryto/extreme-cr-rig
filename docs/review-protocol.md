# Review Protocol
<!-- VERSION: 1.0 | STATUS: initial release -->

## Purpose

Define the core review loop independently from any communication platform.

This protocol is the engine of `extreme-cr-rig`.

## Actors

- Human
- Lead agent
- Review agents

## Default Mode

Default mode is independent full review.

Review agents review the same change independently and emit findings using the same review standard.

Specialized reviewer assignments are optional and human-directed, not required by the protocol.

## Inputs

Each review round should start with:

- the change under review
- relevant project rules and constraints
- relevant design or system context
- merge criteria defined by the human
- reviewer count chosen by the human

## Round Phases

### 1. Round Start

The human starts a round and provides the required context.

### 2. Independent Review

Each review agent performs an independent review and emits findings in the shared format.

Before reviewing a new round, each reviewer should read the previous round's lead assessment, unified findings, and verdict when they exist.

The reviewer is expected to:

- check whether prior concerns were resolved
- avoid repeating rejected findings without new evidence
- explicitly track the status of earlier findings they raised

### 3. Lead Assessment

The lead agent ingests reviewer outputs and evaluates each finding as:

- `valid`
- `duplicate`
- `uncertain`
- `rejected`

### 4. Human Adjudication

The human reviews:

- the synthesized finding set
- any disputed or uncertain items

### 5. Unified Findings

The lead agent produces one unified finding list.

This is the authoritative review output for the round.

### 6. Fix Batching

The lead agent groups accepted findings into fix batches.

Each batch should be small enough to:

- implement safely
- verify meaningfully
- isolate regressions when they appear

### 7. Batch Verification

After each fix batch:

- changes are verified
- regressions are checked
- the next batch proceeds only after the current batch is accepted

### 8. Re-Review

After all batches are complete, review is re-run on:

- changed areas
- impacted hotspots
- unresolved findings

### 9. Human Verdict

The human decides whether:

- the loop is complete
- another round is required
- merge criteria have been met

## Review Standard

All reviewer agents must use a shared review standard so outputs are comparable.

At minimum the standard must cover:

- correctness and regressions
- scale
- industry standards and best practices
- extendability and maintainability
- production-grade rigor
- architecture and ownership
- verification and documentation gaps

## Protocol Rules

- the lead agent is the only synthesis authority
- review agents are signal producers, not coordinators
- the human owns disputed findings and final exit criteria
- one round should produce one unified finding list
- fixes should be batched, not collapsed into one giant remediation pass
- reviewers should consume prior round feedback before starting another round
- repeated findings should be justified as still-open or newly evidenced, not restated blindly

## Non-Goals

- enforcing one specific transport
- forcing one specific model vendor
- replacing human approval

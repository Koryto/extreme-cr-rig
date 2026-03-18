# Filesystem Reference Transport
<!-- VERSION: 1.0 | STATUS: initial release -->

## Purpose

Define the first supported transport for `extreme-cr-rig`.

This transport uses the local filesystem as the communication layer for review artifacts.

It is the reference implementation for the initial release.

## Why Filesystem First

The filesystem transport is:

- easy to inspect
- easy to debug
- easy to operate manually
- easy to adapt later into CLI, PR, chat, or API transports

## Round Workspace

Each review round should use a dedicated workspace directory.

Recommended structure:

```text
round_001/
|-- 00_round_context.md
|-- 10_previous_round_feedback.md
|-- reviewers/
|   |-- reviewer_alpha.md
|   |-- reviewer_beta.md
|   `-- reviewer_gamma.md
|-- lead/
|   |-- 20_assessment.md
|   |-- 30_unified_findings.md
|   `-- 40_fix_batches.md
|-- verification/
|   |-- batch_001.md
|   `-- batch_002.md
`-- 60_round_verdict.md
```

## Artifact Purpose

- `00_round_context.md`
  - round scope
  - change summary
  - relevant project rules
  - merge criteria
  - reviewer roster

- `10_previous_round_feedback.md`
  - summary of prior round outcomes relevant to this round
  - prior lead assessment references
  - prior unified finding references
  - prior verdict references

- `reviewers/reviewer_<name>.md`
  - one reviewer's findings in the shared format
  - includes follow-up on that reviewer's prior findings when applicable

- `lead/20_assessment.md`
  - lead classification of each reviewer finding

- `lead/30_unified_findings.md`
  - final accepted/disputed finding set for the round

- `lead/40_fix_batches.md`
  - fix plan broken into verification-sized batches

- `verification/batch_<n>.md`
  - verification results and regression notes for each fix batch

- `60_round_verdict.md`
  - round outcome
  - unresolved risks
  - whether another round is required

## Operating Flow

1. Lead creates the round context with human guidance.
2. Lead prepares previous-round feedback when applicable, with human guidance.
3. Reviewers read prior feedback and write findings files.
4. Lead writes assessment.
5. Human resolves disputed or uncertain items with the lead.
6. Lead writes the unified findings and fix batches.
7. Fixes are applied and verified batch by batch.
8. Lead writes the round verdict.
9. Human decides whether to stop or start another round.

## Transport Rules

- one reviewer file per reviewer
- no hidden state outside round artifacts
- the lead output becomes the authoritative round state
- verification must be written down, not assumed
- completed rounds should remain readable for later reference
- reviewers should have explicit access to prior round feedback before starting the next round

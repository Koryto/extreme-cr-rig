# Filesystem Reference Transport
<!-- VERSION: 1.1 | STATUS: hardened draft -->

## Purpose

Define the first supported transport for `extreme-cr-rig`.

This transport uses the local filesystem as the communication layer for review artifacts.

It is the reference implementation for the initial release.

## Why Filesystem First

The filesystem transport is:

- easy to inspect
- easy to debug
- easy to operate manually
- easy to adapt later into CLI, PR, chat, or API interfaces

## Round Workspace

Each review round should use a dedicated workspace directory.

Recommended structure:

```text
<repo>/.ecrr/<task_name>/round_001/
|-- 00_round_context.md
|-- 10_previous_round_feedback.md
|-- README.md
|-- reviewers/
|   |-- reviewer_alpha.md
|   |-- reviewer_beta.md
|   `-- reviewer_gamma.md
|-- lead/
|   |-- 20_reviewer_feedback.md
|   `-- 30_round_results.md
|-- verification/
|   |-- batch_001.md
|   `-- batch_002.md
`-- 60_round_verdict.md
```

## Artifact Purpose

- `00_round_context.md`
  - round scope
  - reviewed state / branch pair
  - change summary
  - relevant project rules
  - human-owned merge criteria when relevant
  - out-of-scope items
  - reviewer roster

- `10_previous_round_feedback.md`
  - summary of prior round outcomes relevant to this round
  - prior reviewer-facing carry-forward references
  - prior human-facing round-results references
  - prior verdict references

- `README.md`
  - small round-local operator guide
  - exact file flow for this round

- `reviewers/reviewer_<name>.md`
  - one reviewer's findings in the shared format
  - confirms review basis against current file state
  - includes follow-up on that reviewer's prior findings when applicable

- `lead/20_reviewer_feedback.md`
  - reviewer-facing carry-forward artifact
  - classification of reviewer findings
  - stale/rejected/deferred guidance for future rounds

- `lead/30_round_results.md`
  - human-facing round results
  - accepted findings
  - dropped / deferred notes as needed
  - execution plan / fix batches
  - approval request for the human
  - may be compact in quick rounds

- `verification/batch_<n>.md`
  - verification results and regression notes for each fix batch

- `60_round_verdict.md`
  - round closeout
  - human verdict: `merge` or `another_round`
  - unresolved risks
  - next action

## Operating Flow

1. Lead creates `<repo>/.ecrr/<task_name>/round_00X/`.
2. Lead copies the contents of `reference/filesystem/round_template/` into the new round.
3. Lead fills `00_round_context.md` with human guidance.
4. Lead fills `10_previous_round_feedback.md` before reviewers begin when the round is not the first round.
5. Reviewers read the populated round files and write findings files.
6. Lead produces reviewer-facing feedback and the human-facing round results.
7. Human approves the round results or requests another lead pass.
8. Fixes are applied and verified batch by batch.
9. Human decides `merge` or `another_round`, and the lead records that in `60_round_verdict.md`.

## Transport Rules

- one reviewer file per reviewer
- no hidden state outside round artifacts
- the round should not start until required files are populated
- reviewer-facing and human-facing lead outputs serve different audiences and should stay distinct
- verification must be written down, not assumed
- completed rounds should remain readable for later reference
- reviewers should have explicit access to prior round feedback before starting the next round

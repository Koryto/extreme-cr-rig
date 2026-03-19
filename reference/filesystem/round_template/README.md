# Round Template

This directory is copied into a live round workspace.

## Standard Flow

1. Lead populates `00_round_context.md`.
2. Lead populates `10_previous_round_feedback.md` before reviewers start when the round is not the first round.
3. Reviewers write findings under `reviewers/`.
4. Lead writes:
   - `lead/20_reviewer_feedback.md`
   - `lead/30_round_results.md`
5. Human approves the round results or asks for another lead pass.
6. Fixes and verification artifacts are written when needed.
7. Lead records `60_round_verdict.md` after the human decides:
   - `merge`
   - `another_round`

## Quick Round Flow

Use quick rounds when the branch is already near merge and only low-signal follow-up remains.

Quick rounds may skip `lead/20_reviewer_feedback.md` and use a compact `lead/30_round_results.md`.

## Required Files

- `00_round_context.md`
- `reviewers/`
- `60_round_verdict.md`

Required for non-initial rounds:

- `10_previous_round_feedback.md`

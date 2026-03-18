# Filesystem Reference Template

This directory contains the reference template for running `extreme-cr-rig` manually over the filesystem.

Use the template as the starting point for a review round.

## Layout

```text
reference/filesystem/
`-- round_template/
```

## How To Use

1. Start with [START_HERE.md](START_HERE.md).
2. Copy `round_template/` to a working round directory such as `round_001/`.
3. Fill `00_round_context.md`.
4. Fill `10_previous_round_feedback.md` when this is not the first round.
5. Have each reviewer create or rename a reviewer file under `reviewers/`.
6. Let the lead agent write assessment, unified findings, and fix batches.
7. Record verification results in `verification/`.
8. End the round with `60_round_verdict.md`.

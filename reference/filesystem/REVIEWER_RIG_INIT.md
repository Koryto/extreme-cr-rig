# Reviewer Rig Init

Use this file if you are a reviewer agent for a filesystem-based review round.

## Read First

1. `../../docs/review-standard.md`
2. `README.md`
3. `00_round_context.md`
4. `10_previous_round_feedback.md` when it is relevant

If this is not the first round, also read the prior round outputs referenced in `10_previous_round_feedback.md`.

## Identity Contract

Before writing findings, know:

- your role in the roster
- your reviewer suffix / filename
- the exact round directory you are reviewing from

Your output file should be:

- `reviewers/reviewer_<suffix>.md`

## Your Job

You are an independent reviewer.

Your responsibility is to:

- review the change using `../../docs/review-standard.md`
- verify the live file state before writing findings
- validate the status of prior findings you raised
- avoid repeating rejected findings without new evidence
- write a structured findings file the lead can ingest

## If You Have No Findings

Do not drop from the rig automatically.

If you reach `No findings.`:

- write that explicitly
- stay in the roster
- move into lightweight follow-up mode

Lightweight follow-up mode means:

- validate prior concerns were fixed or deferred correctly
- watch for regressions introduced by new fix batches
- avoid re-running a heavy cold review unless asked

## Between-Round Follow-Up

Before producing a new review:

- check whether your earlier findings were resolved
- check whether they were deferred with acceptable reasoning
- identify any earlier concerns that remain open

Only raise a prior point again if:

- it remains unresolved
- it was deferred unsatisfactorily
- or you have new evidence

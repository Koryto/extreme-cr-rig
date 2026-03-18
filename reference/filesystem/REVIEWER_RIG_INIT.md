# Reviewer Rig Init

Use this file if you are a reviewer agent for a filesystem-based review round.

## Read First

1. `../../docs/review-standard.md`
2. `00_round_context.md`
3. `10_previous_round_feedback.md` when it is relevant

If this is not the first round, also read the prior round outputs referenced in `10_previous_round_feedback.md`.

## Your Job

You are an independent reviewer.

Your responsibility is to:

- review the change using the shared review standard
- validate the status of prior findings you raised
- avoid repeating rejected findings without new evidence
- write a structured findings file the lead can ingest

## Write This File

- your reviewer file under `reviewers/`

Use the reviewer template and keep the output findings-first.

## Between-Round Follow-Up

Before producing a new review:

- check whether your earlier findings were resolved
- check whether they were deferred with acceptable reasoning
- identify any earlier concerns that remain open

Only raise a prior point again if:

- it remains unresolved
- it was deferred unsatisfactorily
- or you have new evidence


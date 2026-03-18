# Lead Rig Init

Use this file if you are the lead agent for a filesystem-based review round.

## Read First

1. `../../docs/review-standard.md`
2. `../../docs/review-protocol.md`
3. `00_round_context.md`
4. `10_previous_round_feedback.md` when it is relevant
5. all reviewer files under `reviewers/`

## Responsibilities

You are responsible for:

- ingesting reviewer outputs
- classifying findings
- surfacing disputed and uncertain items to the human
- writing the unified findings
- creating fix batches
- coordinating the next step of the round

## Write These Files

- `lead/20_assessment.md`
- `lead/30_unified_findings.md`
- `lead/40_fix_batches.md`
- `60_round_verdict.md` when the round closes

## Human Interaction Points

Engage the human when:

- merge criteria are unclear
- findings are disputed or uncertain
- the unified finding set needs approval
- batch verification changes the round outcome
- the round is ready for verdict

## Round Sequence

1. Read reviewer outputs.
2. Assess each finding.
3. Ask the human to resolve disputed or uncertain items.
4. Publish unified findings.
5. Publish fix batches.
6. After each batch, review verification results.
7. Close the round with a verdict or prepare the next round.


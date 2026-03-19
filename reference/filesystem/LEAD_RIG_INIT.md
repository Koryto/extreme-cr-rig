# Lead Rig Init

Use this file if you are the lead agent for a filesystem-based review round.

## Read First

1. `../../docs/review-standard.md`
2. `../../docs/review-protocol.md`
3. `README.md`
4. `00_round_context.md`
5. `10_previous_round_feedback.md` when it is relevant
6. all reviewer files under `reviewers/`

## Rig Setup Checklist

Complete this before reviewers start:

1. Confirm the target round path:
   - `<repo>/.ecrr/<task_name>/round_00X/`
2. Confirm the template was copied into that round.
3. Fill `00_round_context.md` with:
   - exact review scope
   - reviewed state / branch pair
   - relevant context
   - reviewer roster
   - human-owned merge criteria when relevant
   - out-of-scope items when relevant
4. If this is not the first round, fill `10_previous_round_feedback.md` before reviewers start.
5. Confirm reviewer file suffixes and expected reviewer submissions.
6. Confirm whether this is a `standard` round or a `quick` round.

If these steps are incomplete, the round is not ready.

## Responsibilities

You are responsible for:

- rig setup
- ingesting reviewer outputs
- classifying findings
- producing reviewer-facing carry-forward feedback
- producing the human-facing round results and execution plan
- coordinating fix / verification flow
- closing the round with a verdict

## Write These Files

Standard round:

- `lead/20_reviewer_feedback.md`
- `lead/30_round_results.md`
- `60_round_verdict.md`

Quick round:

- `lead/30_round_results.md`
- `60_round_verdict.md`

Verification files are expected when fixes or validation occur.

## Human Interaction Points

Engage the human when:

- scope or merge criteria are unclear
- reviewer submissions are missing and the round may proceed only partially
- the human-facing round results and execution plan need approval
- verification changes the expected round outcome
- the round is ready for a `merge` or `another_round` verdict

## Lead Flow

1. Read reviewer outputs.
2. Produce the reviewer-facing carry-forward artifact when the round needs it.
3. Produce the human-facing round results:
   - unified findings
   - execution plan
   - dropped/deferred notes when needed
4. Ask the human for approval or rejection of the round results.
5. Track fixes and verification artifacts.
6. Ask the human for the final verdict:
   - `merge`
   - `another_round`
7. If another round is required, prepare the next round carry-forward before reviewers start.

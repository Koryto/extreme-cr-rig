# Start Here

This file is the operational entrypoint for the initial release of `extreme-cr-rig`.

Use it when running the rig manually over the filesystem.

## Before You Start

You need:

- one human supervisor
- one lead agent
- one or more review agents
- the code change under review
- any relevant project rules, specs, or system context
- merge criteria defined by the human

## Launch The Rig

1. Copy `round_template/` into a new round workspace such as `round_001/`.
2. Fill `00_round_context.md`.
3. Assign:
   - one lead agent
   - one or more review agents
4. Give every participant the round context and the shared review standard.

## Reviewer Instructions

Before writing findings for a new round, each reviewer should read:

- `00_round_context.md`
- the previous round's lead assessment, if one exists
- the previous round's unified findings, if one exists
- the previous round's verdict, if one exists

Then the reviewer should:

1. validate whether their prior concerns were resolved, deferred properly, or remain open
2. write new findings only when they are genuinely new or still unresolved
3. submit a findings file under `reviewers/`

## Lead Instructions

The lead agent should:

1. read all reviewer files
2. classify each finding in `lead/20_assessment.md`
3. surface disputed or uncertain items to the human
4. write `lead/30_unified_findings.md`
5. write `lead/40_fix_batches.md`

## Human Control Points

The human should intervene at least at these points:

- round start
- disputed or uncertain findings
- approval of the unified findings and fix direction
- acceptance of verification after each batch when needed
- round verdict

## Batch Loop

For each batch:

1. apply the fixes
2. write verification results
3. confirm whether regressions were introduced
4. proceed to the next batch only after the current one is accepted

## Next Round

If another round is needed:

1. create the next round workspace
2. carry forward the prior round's assessment, unified findings, and verdict
3. require reviewers to read that feedback before producing another review

## End Condition

The rig round ends only when the human decides:

- merge criteria are met
- another round is not needed


# Start Here

Filesystem entrypoint for a live rig run.

## Role Split

- if you are the lead agent, read `LEAD_RIG_INIT.md`
- if you are a reviewer agent, read `REVIEWER_RIG_INIT.md`

## Lead Setup Checklist

The lead should perform these steps with human guidance before any reviewer starts:

1. Create the next round under the target repo:
   - `<repo>/.ecrr/<task_name>/round_00X/`
2. Copy every file and folder from:
   - `reference/filesystem/round_template/`
3. Fill:
   - `00_round_context.md`
4. If this is not the first round, fill:
   - `10_previous_round_feedback.md`
5. Confirm:
   - reviewer roster
   - reviewer file suffixes
   - round mode (`standard` or `quick`)
6. Tell reviewers which round directory they should use.

If those steps are not done, the round is not ready.

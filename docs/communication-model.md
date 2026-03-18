# Communication Model
<!-- VERSION: 1.0 | STATUS: initial release -->

## Purpose

Define how humans and agents interact during a review round without coupling the protocol to one specific platform.

## Principle

Communication is not the engine.

The purpose of the communication layer is to move review artifacts between actors while preserving:

- visibility
- control
- round state
- low-noise synthesis

## Communication Topology

### Human

The human can:

- instruct the lead agent
- provide context to the rig
- request another review round
- decide merge criteria and loop termination

### Lead Agent

The lead agent is the primary operational interface.

The lead agent should:

- ingest reviewer outputs
- communicate synthesized state to the human
- request clarification when disputed findings need human judgment
- produce fix batches and round outcomes

### Review Agents

Review agents should primarily communicate through structured outputs, not open-ended discussion.

Their main responsibility is to produce findings that the lead can ingest and normalize.

## Default Communication Rules

- reviewers review independently
- reviewers do not need to coordinate directly with one another
- the lead agent is the central synthesis point
- the human should mostly interact with the lead agent between major round steps
- direct reviewer-to-reviewer discussion should be minimized

## Required Communication Outcomes

The communication layer must allow:

- round start with shared context
- reviewer submission of findings
- lead publication of assessment and unified findings
- human approval or dispute of synthesized outcomes
- batch-by-batch fix and verification updates
- explicit round verdict

## Transport-Agnostic Boundary

The communication model should work across:

- files
- pull request comments
- chat systems
- HTTP services

Those are transport decisions, not protocol decisions.

The protocol only requires that artifacts can move between actors in a structured way.

## Initial Release Position

The initial release uses a file-system-based reference transport.

That transport is the first supported implementation of the communication model, not the model itself.


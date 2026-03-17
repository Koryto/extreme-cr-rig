# Extreme CR Rig Vision
<!-- VERSION: 0.1 | STATUS: draft -->

## Purpose

`extreme-cr-rig` is a lead-agent-centric orchestration system for reviewing large or high-risk code changes.

It is designed for cases where a single agent review plus one human reviewer is no longer enough to yield reliable results, especially on large pull requests or complex architectural changes.

The project exists to increase review depth without turning review into an unstructured multi-agent chat.

## Problem

Agent-assisted development increases implementation throughput.

That creates a new bottleneck:

- pull requests become larger
- changes span more systems
- human review bandwidth does not scale proportionally
- a single agent review may miss issues or fail to surface them in a reviewable way

The result is that teams can produce code faster than they can review it well.

`extreme-cr-rig` exists to solve that bottleneck.

## Core Idea

Use multiple review agents as independent signal producers and one strong lead agent as the synthesizer, planner, and human-facing coordinator.

The lead agent is the center of gravity.

Review agents are replaceable workers:

- they review
- they write findings in a shared format
- they do not need to coordinate deeply with one another

The human stays in control of:

- reviewer count
- merge criteria
- disputed findings
- review loop termination

## Product Shape

This is not a general project framework.

This is a review orchestration product or protocol with three primary actors:

1. Human
2. Lead agent
3. Review agents

It should remain transport-agnostic:

- markdown files
- pull request comments
- Discord messages
- HTTP endpoints
- other communication layers

The transport layer is secondary.
The orchestration protocol is primary.

## Default Review Model

1. Human starts a review round.
2. Human provides the lead agent with the change context:
   - diff or PR
   - relevant project rules
   - relevant specs and systems context
   - merge criteria
3. Human chooses reviewer count.
4. Review agents perform independent reviews using a shared code-review standard.
5. Review agents publish findings in a common format.
6. Lead agent ingests all findings.
7. Lead agent deduplicates, classifies, and evaluates:
   - valid
   - duplicate
   - uncertain
   - rejected
8. Human reviews the synthesized output and disputed items.
9. Lead agent produces fix batches.
10. Fixes are implemented and verified batch by batch.
11. Review is re-run on changed areas and unresolved hotspots.
12. Human decides whether another review round is needed.

## Roles

### Human

Owns:

- scope
- reviewer count
- merge criteria
- approval of disputed findings
- decision to continue or stop the loop

### Lead Agent

Owns:

- synthesis of reviewer outputs
- deduplication and classification
- communication with the human
- creation of fix batches
- tracking round state
- deciding what needs re-review

The lead agent should be the strongest reasoning/synthesis model available.

### Review Agents

Own:

- independent review
- structured finding output

They are not the center of the system.

They are intentionally simple and replaceable.

## Shared Review Standard

All review agents should use the same code review standard so their outputs are comparable.

That standard should include at minimum:

- correctness and regression risk
- scale
- industry standards and best practices
- extendability and maintainability
- production-grade rigor
- architecture and ownership
- verification and documentation gaps

## Design Principles

- lead-agent-centric, not group-chat-centric
- findings first, not discussion first
- human-controlled, not consensus theater
- protocol first, transport second
- support heterogeneous models to exploit different strengths
- optimize for reviewability, not just raw review volume
- fixes should happen in batches with verification between them

## Non-Goals

- replacing human merge authority
- fully autonomous review-to-merge pipelines
- forcing a specific communication platform
- solving every part of multi-agent software development
- becoming a general agent framework

## Why This Matters

Large PR review is currently weak across the industry.

Humans are bad at reviewing giant diffs without structure.
Single-agent review is useful but limited.
Multi-agent review without orchestration turns into noise.

`extreme-cr-rig` aims to create a structured review loop that combines:

- independent machine review depth
- strong synthesis
- human judgment

## Likely Early Implementation Direction

The first implementation should stay simple.

It should prove the protocol before optimizing transport or user experience.

Good early directions:

- file-based reviewer output
- a shared finding schema
- a lead-agent synthesis format
- a round-based workflow document

The first version does not need:

- rich UI
- live chat orchestration
- complex infrastructure
- full automation

## Future Potential

If the protocol proves strong, it could later expand into:

- better review transport layers
- formal role orchestration
- review dashboards
- integration with project frameworks
- eventually, broader multi-agent engineering orchestration

## Bottom Line

`extreme-cr-rig` is an attempt to solve the next bottleneck after agent-assisted implementation speed:

high-quality review at scales where one human and one agent are no longer enough.


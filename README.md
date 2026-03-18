# Extreme CR Rig

`extreme-cr-rig` is a lead-agent-centric orchestration system for reviewing large or high-risk code changes.

It is designed for the point where agent-assisted implementation has already increased delivery speed, but review quality has become the next bottleneck.

## What It Solves

Large pull requests and high-risk changes are difficult to review well with:

- one human reviewer
- one agent review pass
- one monolithic diff

The rig addresses that problem by combining:

- independent reviewer agents
- one lead agent as the synthesis center
- a human supervisor with final authority
- iterative review, fix, and verification loops

## Initial Release

The current release is the manual/reference rig over the filesystem.

It includes:

- a defined [review protocol](docs/review-protocol.md)
- a defined [review standard](docs/review-standard.md)
- a defined [communication model](docs/communication-model.md)
- a defined [filesystem reference transport](docs/filesystem-reference-transport.md)
- role-specific operator entrypoints for the filesystem transport
- a round template for running the rig manually

## Core Roles

- **Human**
  - chooses reviewer count
  - owns disputed findings
  - defines merge criteria
  - decides when the loop ends

- **Lead agent**
  - ingests reviewer outputs
  - evaluates and synthesizes findings
  - batches fixes
  - coordinates the next step

- **Review agents**
  - perform independent review
  - emit findings in the shared review format

## Design Principles

- lead-agent-centric, not group-chat-centric
- findings first, not discussion first
- protocol first, transport second
- human-controlled, not consensus theater
- support heterogeneous reviewer models
- optimize for reviewability, not just review volume

## How To Start

For the current release:

1. start with the [filesystem runbook](reference/filesystem/START_HERE.md)
2. choose your role-specific init file
3. run the round from the provided template

## Public Docs

- [Review Protocol](docs/review-protocol.md)
- [Review Standard](docs/review-standard.md)
- [Communication Model](docs/communication-model.md)
- [Filesystem Reference Transport](docs/filesystem-reference-transport.md)
- [Filesystem Directory Guide](reference/filesystem/README.md)
- [Filesystem Runbook](reference/filesystem/START_HERE.md)
- [Lead Rig Init](reference/filesystem/LEAD_RIG_INIT.md)
- [Reviewer Rig Init](reference/filesystem/REVIEWER_RIG_INIT.md)

## What This Is Not

- not a general agent framework
- not a freeform multi-agent group chat
- not an autonomous merge pipeline
- not a replacement for human review authority

## Next Direction

After the manual/reference rig is validated, the next intended step is a CLI-based transport/orchestration layer built on top of the same protocol.


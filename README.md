# Extreme CR Rig

`extreme-cr-rig` is a lead-agent-centric orchestration system for reviewing large or high-risk code changes.

It is built for the point where agent-assisted implementation has already accelerated delivery, but review quality has become the next bottleneck.

## What It Solves

Large pull requests and high-risk changes are difficult to review well with:

- one human reviewer
- one agent review pass
- one monolithic diff

The rig addresses that problem by combining:

- independent reviewer agents
- one strong lead agent
- a human supervisor with final authority
- iterative review, fix, and verification loops

## Initial Release

The initial release is intentionally simple.

It formalizes the already-proven manual operating model and ships with:

- a defined review protocol
- a defined communication model
- a file-system-based reference transport
- a reference round template for running the rig manually

This release is protocol-first, not tooling-first.

## Core Roles

- **Human**: chooses reviewer count, owns disputed findings, defines merge criteria, decides when the loop ends
- **Lead agent**: ingests reviewer outputs, evaluates them, synthesizes them, batches fixes, and coordinates the next step
- **Review agents**: perform independent review and emit findings in a shared format

## Design Principles

- lead-agent-centric, not group-chat-centric
- findings first, not discussion first
- protocol first, transport second
- human-controlled, not consensus theater
- support heterogeneous reviewer models
- optimize for reviewability, not just review volume

## Included Docs

- [Review Protocol](docs/review-protocol.md)
- [Communication Model](docs/communication-model.md)
- [Filesystem Reference Transport](docs/filesystem-reference-transport.md)
- [Filesystem Runbook](reference/filesystem/START_HERE.md)
- [Filesystem Reference Template](reference/filesystem/README.md)

## What This Is Not

- not a general agent framework
- not a freeform multi-agent group chat
- not an autonomous merge pipeline
- not a replacement for human review authority

## Current Release

The current release is the manual/reference rig over the filesystem.

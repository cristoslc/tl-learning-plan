---
title: "Program Maintainer Tech Lead"
artifact: PERSONA-001
track: standing
status: Active
author: Cristos L-C
created: 2026-04-01
last-updated: 2026-04-01
linked-artifacts:
  - VISION-001
  - INITIATIVE-001
  - EPIC-001
depends-on-artifacts: []
---

# Program Maintainer Tech Lead

## Archetype Label

Content Steward and Publisher

## Demographic Summary

Senior engineer or tech lead with strong system knowledge, moderate frontend comfort, and limited time for repetitive publishing tasks.

## Goals and Motivations

- Keep curriculum content fresh without touching fragile presentation code.
- Publish updates confidently with deterministic output.
- Avoid accidental visual regressions in a high-visibility capability map.

## Frustrations and Pain Points

- Manual HTML edits are error-prone and costly to review.
- Mermaid drift between files introduces confusion about what is current.
- Small content edits currently require high cognitive overhead.

## Behavioral Patterns

- Writes and curates content in markdown first.
- Prefers scripted generation and validation over hand-maintained duplication.
- Uses git history to audit and reason about changes.

## Context of Use

- Iterative updates during planning and coaching cycles.
- Quick content refreshes between meetings.
- Occasional structural updates requiring design-safe pipeline changes.

## Lifecycle

| Phase | Date | Commit | Notes |
|-------|------|--------|-------|
| Active | 2026-04-01 | 773bcc9 | Initial creation |

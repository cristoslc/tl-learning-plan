---
title: "Markdown Ingestion and Page Assembly"
artifact: SPEC-002
track: implementable
status: Ready
author: Cristos L-C
created: 2026-04-01
last-updated: 2026-04-01
priority-weight: high
type: enhancement
parent-epic: EPIC-001
parent-initiative: ""
linked-artifacts:
  - DESIGN-001
  - DESIGN-002
depends-on-artifacts:
  - SPEC-001
  - DESIGN-002
addresses: []
evidence-pool: ""
source-issue: ""
swain-do: required
---

# Markdown Ingestion and Page Assembly

## Problem Statement

Content currently exists across markdown files and hand-assembled HTML. We need deterministic markdown ingestion and assembly so content updates no longer require manual HTML edits.

## Desired Outcomes

Capability and summary markdown files become first-class content inputs to Astro page generation, with stable ordering and rendering behavior.

## External Behavior

- Inputs: `dist/_0 concept-map.md`, `dist/capability-*.md`, and `dist/summaries/*.md`.
- Output: generated capability map content sections and resource cards.
- Preconditions: Astro shell parity exists.
- Constraints: preserve current content hierarchy and navigation semantics.

## Acceptance Criteria

- Given markdown sources are unchanged, when build runs, then generated content sections preserve current headings and sequence.
- Given a capability markdown file is edited, when build runs, then corresponding page content updates without manual HTML edits.
- Given summaries are present, when page renders resources, then links and metadata remain consistent with source markdown.
- Given ordering rules are defined, when files are enumerated, then output order is deterministic across machines.

## Verification

| Criterion | Evidence | Result |
|-----------|----------|--------|

## Scope & Constraints

- Scope: content parsing, mapping, and page-model assembly.
- Constraint: no schema coupling that blocks future markdown additions.

## Implementation Approach

- Implement content loader utilities for capability and summary markdown files.
- Normalize parsed data into a stable page model.
- Render model through Astro components introduced in SPEC-001.

## Lifecycle

| Phase | Date | Commit | Notes |
|-------|------|--------|-------|
| Ready | 2026-04-01 | 773bcc9 | Initial creation |

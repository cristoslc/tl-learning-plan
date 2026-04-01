---
title: "Astro Shell and Page Parity"
artifact: SPEC-001
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
depends-on-artifacts:
  - DESIGN-001
addresses: []
evidence-pool: ""
source-issue: ""
swain-do: required
---

# Astro Shell and Page Parity

## Problem Statement

The current capability map layout and behavior live in hand-maintained HTML. We need an Astro page shell that reproduces this structure exactly so future content can be generated safely.

## Desired Outcomes

Astro emits a capability-map page that preserves current layout landmarks, theme toggle behavior, and interaction affordances.

## External Behavior

- Inputs: existing style/interaction contract from `dist/capability-map.html`.
- Output: generated HTML page with equivalent structure and behavior hooks.
- Preconditions: Astro project scaffold is initialized.
- Constraints: no design changes or UX model drift.

## Acceptance Criteria

- Given the Astro build runs, when `capability-map` page is generated, then top-level sections (header, content pane, map pane, footer) match the current structure.
- Given a user switches theme preference, when page reloads, then persisted theme behavior remains equivalent to current implementation.
- Given filters are interacted with, when resource visibility changes, then filter semantics match current behavior.
- Given the generated page is diffed against a baseline structure snapshot, then only approved dynamic regions may differ.

## Verification

| Criterion | Evidence | Result |
|-----------|----------|--------|

## Scope & Constraints

- Scope: Astro layout, shell markup, and interaction wiring parity.
- Constraint: do not alter content semantics or visual direction.

## Implementation Approach

- Bootstrap Astro project and create parity-oriented layout/component structure.
- Port page shell and interaction hooks with minimal structural deviation.
- Add structure-parity validation script/test.

## Lifecycle

| Phase | Date | Commit | Notes |
|-------|------|--------|-------|
| Ready | 2026-04-01 | 773bcc9 | Initial creation |

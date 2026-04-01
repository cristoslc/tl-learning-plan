---
title: "Mermaid Authority Sync and Validation"
artifact: SPEC-003
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
  - DESIGN-002
depends-on-artifacts:
  - SPEC-001
  - SPEC-002
  - DESIGN-002
addresses: []
evidence-pool: ""
source-issue: ""
swain-do: required
---

# Mermaid Authority Sync and Validation

## Problem Statement

Current state: the authoritative Mermaid graph is embedded in `dist/capability-map.html`.

Target state: `dist/capability-graph.mmd` becomes authoritative, and generated HTML must always derive its Mermaid block from that `.mmd` source.

## Desired Outcomes

We perform a controlled one-time authority flip (HTML -> `.mmd`) and then enforce a permanent pipeline rule that HTML graph output is generated from canonical `.mmd`.

## External Behavior

- Inputs: current authoritative Mermaid block in `dist/capability-map.html` and canonical target file `dist/capability-graph.mmd`.
- Output: validated canonical `.mmd` plus generated HTML Mermaid block sourced from it.
- Preconditions: Astro shell and content assembly paths are in place.
- Constraints: no future manual HTML Mermaid authorship.

## Acceptance Criteria

- Given the current authoritative Mermaid is in HTML, when migration runs once, then `dist/capability-graph.mmd` is updated to match that HTML graph exactly.
- Given migration is complete, when normal builds run, then Mermaid in generated HTML is produced from `dist/capability-graph.mmd` and not from embedded handwritten HTML.
- Given `.mmd` content changes, when build runs, then generated HTML Mermaid reflects the change deterministically.
- Given generated HTML Mermaid diverges from `.mmd` transformation output, when validation runs, then build fails with explicit drift diagnostics.

## Verification

| Criterion | Evidence | Result |
|-----------|----------|--------|

## Scope & Constraints

- Scope: authority migration, generation wiring, and drift validation.
- Constraint: preserve graph semantics and styling tokens while moving source authority.

## Implementation Approach

- Implement extraction utility to capture current HTML Mermaid and update `.mmd` once.
- Lock pipeline so generated HTML Mermaid is built from `.mmd`.
- Add validation step comparing generated Mermaid block against canonical transformation output.

## Lifecycle

| Phase | Date | Commit | Notes |
|-------|------|--------|-------|
| Ready | 2026-04-01 | 773bcc9 | Initial creation |

---
title: "Astro Static Site Generation Pipeline"
artifact: INITIATIVE-001
track: container
status: Active
author: Cristos L-C
created: 2026-04-01
last-updated: 2026-04-01
parent-vision:
  - VISION-001
priority-weight: high
success-criteria:
  - Generated `capability-map.html` preserves the existing structure, styling model, and interaction behavior.
  - Content updates flow from markdown inputs without manual HTML editing.
  - `dist/capability-graph.mmd` becomes and remains the Mermaid source of truth.
  - Build output is deterministic and validated in CI/local checks.
depends-on-artifacts:
  - VISION-001
addresses: []
evidence-pool: ""
---

# Astro Static Site Generation Pipeline

## Strategic Focus

Replace manual HTML maintenance with an Astro-based static pipeline while preserving the current UI and content structure exactly.

## Desired Outcomes

The maintainer can update markdown and Mermaid sources, run one build, and publish with confidence that generated HTML is accurate and stable.

## Progress

<!-- Auto-populated from session digests. See progress.md for full log. -->

## Scope Boundaries

In scope:
- Astro project scaffold for static generation.
- Content ingestion from existing markdown files.
- One-time Mermaid extraction from current HTML into `.mmd`.
- Future builds driven by `.mmd` into generated HTML.
- Parity checks for layout/structure safety.

Out of scope:
- Visual redesign.
- Content rewrite beyond pipeline needs.
- Runtime backend services.

## Tracks

- Parity Track: replicate current HTML structure and styling in Astro templates.
- Content Track: markdown-driven assembly of capabilities and summaries.
- Diagram Track: Mermaid authority migration and ongoing generation from `.mmd`.

## Child Epics

- [EPIC-001](../../../epic/Active/(EPIC-001)-Astro-Migration-with-Exact-HTML-Parity/(EPIC-001)-Astro-Migration-with-Exact-HTML-Parity.md)

## Small Work (Epic-less Specs)

None planned at creation.

## Key Dependencies

- Existing `dist/` markdown corpus remains stable as input.
- Existing HTML implementation remains reference baseline during parity work.

## Lifecycle

| Phase | Date | Commit | Notes |
|-------|------|--------|-------|
| Active | 2026-04-01 | 773bcc9 | Initial creation |

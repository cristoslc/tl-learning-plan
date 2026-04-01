---
title: "Astro Migration with Exact HTML Parity"
artifact: EPIC-001
track: container
status: Active
author: Cristos L-C
created: 2026-04-01
last-updated: 2026-04-01
parent-vision: VISION-001
parent-initiative: INITIATIVE-001
priority-weight: high
success-criteria:
  - Generated page preserves current DOM structure and major CSS token semantics used by the existing capability map.
  - Content and resource cards are assembled from markdown inputs.
  - Mermaid rendering path uses `.mmd` as the long-term canonical source.
  - Build and parity checks make drift detectable before publish.
depends-on-artifacts:
  - INITIATIVE-001
  - DESIGN-001
  - DESIGN-002
addresses: []
evidence-pool: ""
---

# Astro Migration with Exact HTML Parity

## Goal / Objective

Ship an Astro-based static generation pipeline that reproduces the current `dist/capability-map.html` experience without manual HTML maintenance.

## Desired Outcomes

The maintainer updates markdown and Mermaid artifacts, runs build, and gets publishable HTML with unchanged design and interaction behavior from the user perspective.

## Progress

<!-- Auto-populated from session digests. See progress.md for full log. -->

## Scope Boundaries

In scope:
- Astro migration, component structure, static build wiring.
- Markdown-to-page assembly.
- Mermaid canonical-source migration to `.mmd`.

Out of scope:
- Rewriting learning content intent.
- Design refresh or visual experiments.

## Child Specs

- [SPEC-001](../../../spec/Ready/(SPEC-001)-Astro-Shell-and-Page-Parity/(SPEC-001)-Astro-Shell-and-Page-Parity.md)
- [SPEC-002](../../../spec/Ready/(SPEC-002)-Markdown-Ingestion-and-Page-Assembly/(SPEC-002)-Markdown-Ingestion-and-Page-Assembly.md)
- [SPEC-003](../../../spec/Ready/(SPEC-003)-Mermaid-Authority-Sync-and-Validation/(SPEC-003)-Mermaid-Authority-Sync-and-Validation.md)

## Key Dependencies

- Existing `dist/capability-map.html` as baseline reference.
- Stable markdown file naming and ordering conventions.

## Lifecycle

| Phase | Date | Commit | Notes |
|-------|------|--------|-------|
| Active | 2026-04-01 | 773bcc9 | Initial creation |

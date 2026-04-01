---
title: "TL Learning Plan Publishing Pipeline"
artifact: VISION-001
track: standing
status: Active
product-type: personal
author: Cristos L-C
created: 2026-04-01
last-updated: 2026-04-01
priority-weight: high
depends-on-artifacts: []
evidence-pool: ""
---

# TL Learning Plan Publishing Pipeline

## Target Audience

Primary: the program maintainer who curates markdown curriculum content and publishes the capability-map site.

Secondary: engineering managers and tech leads consuming published content that must stay trustworthy and current.

## Value Proposition

Make content updates low-friction and reliable by replacing hand-edited HTML with a reproducible static-site pipeline that preserves the current presentation exactly while treating markdown and Mermaid as source inputs.

## Problem Statement

The current workflow requires manual HTML maintenance. This creates drift risk between markdown content, embedded diagrams, and published HTML behavior.

## Existing Landscape

Current assets are already strong:
- `dist/capability-map.html` contains the authoritative current UI/UX implementation.
- `dist/capability-*.md` and `dist/summaries/*.md` contain canonical learning content.
- `dist/capability-graph.mmd` exists but is not currently the canonical graph source.

The gap is the publishing pipeline, not the content or design quality.

## Build vs. Buy

Tier selected: build thin glue around existing content using Astro.

Reasoning:
- Off-the-shelf docs generators do not guarantee pixel-level parity with the existing handcrafted HTML structure.
- Astro gives static output, component composition, markdown ingestion, and predictable build control without forcing redesign.

## Maintenance Budget

Sustainability target:
- Ongoing maintenance should remain feasible for a single maintainer.
- Routine edits should be markdown-only unless structure changes are intentional.
- Regenerating HTML should be deterministic and scriptable.

## Success Metrics

- Content changes in markdown appear in generated HTML with no manual HTML edits.
- The generated capability-map page preserves current structure, theme behavior, and interaction semantics.
- `dist/capability-graph.mmd` becomes the long-term Mermaid source of truth and is rendered into generated HTML.
- A parity check catches unintended divergence between generated output and approved baseline structure.

## Non-Goals

- Redesigning visual identity, layout, typography, or interaction model.
- Expanding curriculum scope in this effort.
- Introducing runtime server dependencies for publishing.

## Lifecycle

| Phase | Date | Commit | Notes |
|-------|------|--------|-------|
| Active | 2026-04-01 | 773bcc9 | Initial creation |

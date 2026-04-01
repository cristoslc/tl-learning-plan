---
title: "Content and Mermaid Source of Truth"
artifact: DESIGN-002
track: standing
domain: data
status: Active
author: Cristos L-C
created: 2026-04-01
last-updated: 2026-04-01
superseded-by: ""
linked-artifacts:
  - EPIC-001
  - SPEC-002
  - SPEC-003
  - DESIGN-001
sourcecode-refs:
  - path: dist/capability-graph.mmd
    blob: cc7d0d0d40fd8ed087a12da6a0f8775660d67df4
    commit: 773bcc9
    verified: 2026-04-01
  - path: dist/capability-map.html
    blob: efad82b28b886ccc5cae078573fe726654e0d391
    commit: 773bcc9
    verified: 2026-04-01
depends-on-artifacts:
  - DESIGN-001
---

# Content and Mermaid Source of Truth

## Design Intent

**Context:** Current reality has Mermaid content embedded in HTML; future state requires `.mmd` as canonical input with generated HTML consuming that source.

### Goals
- Establish a one-way authority model where `dist/capability-graph.mmd` is canonical after migration.
- Normalize markdown content loading into a predictable page data model for Astro templates.
- Preserve deterministic generation order for capability sections and supporting summaries.

### Constraints
- One-time migration extracts Mermaid from current `dist/capability-map.html` into `dist/capability-graph.mmd`.
- After migration, manual Mermaid edits in HTML are prohibited by process and validation.
- Build must fail when generated Mermaid block diverges from canonical `.mmd` input transformation.

### Non-goals
- Changing graph semantics during authority migration.
- Introducing multiple Mermaid canonical files for the same map.
- Allowing bidirectional sync between HTML and `.mmd`.

## Data Surface

Static content source model for capability-map generation:
- Capability markdown files
- Summary markdown files
- Single canonical Mermaid `.mmd` file

## Entity Model

```mermaid
erDiagram
    CAPABILITY_FILE ||--o{ CAPABILITY_SECTION : "produces"
    SUMMARY_FILE ||--o{ RESOURCE_ENTRY : "produces"
    MERMAID_SOURCE ||--|| GRAPH_BLOCK : "renders"
    PAGE_MODEL ||--o{ CAPABILITY_SECTION : "contains"
    PAGE_MODEL ||--o{ RESOURCE_ENTRY : "contains"
    PAGE_MODEL ||--|| GRAPH_BLOCK : "contains"
```

## Data Flow

```mermaid
flowchart TD
    extract_once["One-time extract Mermaid from HTML"] --> write_mmd["Write dist/capability-graph.mmd"]
    write_mmd --> mark_canonical["Set .mmd as canonical source"]
    capability_md["Load capability markdown"] --> build_model["Build Astro page model"]
    summary_md["Load summary markdown"] --> build_model
    canonical_mmd["Load canonical Mermaid .mmd"] --> build_model
    build_model --> render_html["Render capability-map.html"]
    render_html --> parity_checks["Run parity and source-authority checks"]
```

## Schema Definitions

| Field | Type | Nullable | Constraints | Description |
|-------|------|----------|-------------|-------------|
| `capability_slug` | string | no | stable, unique | Deterministic capability key derived from filename/order |
| `capability_markdown` | string | no | non-empty | Renderable markdown body for capability section |
| `summary_refs` | array[string] | yes | path must exist when present | Linked summary documents used by resource cards |
| `mermaid_source_text` | string | no | loaded from `dist/capability-graph.mmd` | Canonical graph definition to inject/render |
| `rendered_graph_block` | string | no | must be generated from canonical source | HTML fragment for map pane graph container |

## Evolution Rules

- Markdown schema may grow with additive fields only.
- Mermaid canonical path remains single-file unless superseded by explicit design change.
- Any change in Mermaid transformation logic requires updating validation fixtures.

## Invariants

- Canonical Mermaid source path is `dist/capability-graph.mmd`.
- Build never treats embedded HTML Mermaid as authoritative after migration.
- Generated graph block is reproducible from canonical source and transformation logic.

## Edge Cases and Error States

- Missing `.mmd` file fails fast with explicit error.
- Invalid Mermaid syntax fails build with location/context diagnostics.
- Markdown parse errors isolate to the offending file and prevent publish.

## Design Decisions

- Use one-time extraction to respect current authoritative HTML state, then permanently flip authority to `.mmd`.
- Keep a single-page model pipeline to simplify parity validation and future maintenance.

## Assets

- `dist/capability-graph.mmd` (canonical post-migration)
- markdown input corpus under `dist/`
- Astro build scripts/components to implement transformation

## Lifecycle

| Phase | Date | Commit | Notes |
|-------|------|--------|-------|
| Active | 2026-04-01 | 773bcc9 | Initial creation |

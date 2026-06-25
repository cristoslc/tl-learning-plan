---
title: "Mermaid Node Jump to Capability"
artifact: SPEC-004
track: implementable
status: Complete
author: Codex
created: 2026-04-01
last-updated: 2026-04-01
type: enhancement
linked-artifacts:
depends-on-artifacts:
addresses:
evidence-pool:
source-issue:
swain-do: required
---

# Mermaid Node Jump to Capability

## Problem Statement

The capability map renders the Mermaid dependency diagram and the capability cards as two separate navigation surfaces. A reader can see that a box in the diagram corresponds to a capability, but clicking the box does nothing, so they still have to manually scan the page to find the matching card. That slows exploration and makes the diagram feel decorative instead of useful.

## Desired Outcomes

The diagram becomes a working navigation aid. A reader should be able to click a capability box in the Mermaid graph and land on the matching capability card in the list without losing context. This should reduce friction when moving between the overview and the detailed capability write-up, especially on smaller screens where the list and graph are farther apart.

## External Behavior

After the page loads and Mermaid finishes rendering the graph SVG, each capability box in the diagram should behave like an in-page jump target for its matching card in the capability list.

- Clicking a capability node scrolls the corresponding capability card into view.
- The destination card has a stable DOM target so the jump remains deterministic after re-renders.
- The jump behavior must tolerate Mermaid rendering timing; if the SVG is not ready yet, the page should not throw errors.
- Nodes that do not map to a capability card, if any exist in the future, should fail safely without breaking the page.
- Existing filters, theme toggles, progress tracking, and Mermaid styling remain intact.

## Acceptance Criteria

- Given the capability map page has finished loading, when a reader clicks a Mermaid node for a numbered capability, then the matching capability card scrolls into view in the main list.
- Given a reader clicks nodes for any currently rendered capability box, then the correct card is targeted for that box rather than the first matching title text on the page.
- Given the page is used after filters, theme changes, or progress toggles, when a reader clicks a Mermaid node, then the jump behavior still works and no existing controls regress.
- Given Mermaid has not yet produced the SVG or a node cannot be resolved, when the binding code runs, then the page fails safely without uncaught JavaScript errors.

## Verification

<!-- Populated when entering Testing phase. Maps each acceptance criterion
     to its evidence: test name, manual check, or demo scenario.
     Leave empty until Testing. -->

| Criterion | Evidence | Result |
|-----------|----------|--------|
| Mermaid node click jumps to matching capability card after load | Browser automation against `http://host.docker.internal:8765/dist/capability-map.html` clicked graph nodes for capabilities 1, 2, 8, 10, and 11 and confirmed each target card moved into view with the matching `#capability-<n>` hash. | Pass |
| Correct card is targeted for rendered capability boxes | Browser automation matched runtime Mermaid node ids containing `flowchart-C<n>-*` to article ids `capability-<n>` and verified the active element became the expected card for multiple capabilities. | Pass |
| Behavior survives filters, theme changes, and progress-related re-renders | Browser automation set filter `video`, switched theme to `night`, then triggered Enter-key navigation from the capability 3 graph node and confirmed the card still moved into view with no console errors. | Pass |
| Binding fails safely when SVG or target resolution is missing | Page-context check `jumpToCapability(999)` returned `false`, left the hash unchanged, and produced no thrown exception or console error. | Pass |

## Scope & Constraints

- Scope is limited to the existing static implementation in `dist/capability-map.html`.
- Do not introduce a build step, framework migration, or server-side behavior just to wire the jump interaction.
- Preserve Mermaid as the renderer for the graph; the enhancement should layer behavior onto the rendered output rather than replace the diagram implementation.
- Preserve static hosting compatibility for GitHub Pages.
- Keep the mapping logic maintainable if capability numbering or titles change later.

## Implementation Approach

Add a stable anchor or `id` per rendered capability card so the list has deterministic jump targets. After Mermaid renders the graph, query the generated SVG nodes, map each graph node identifier (for example `C1`, `C2`, ... `C11`) to the corresponding capability card, and attach click handlers that call `scrollIntoView` on the target card. Guard the binding so it can run safely after initial load and after any future Mermaid re-render without duplicating handlers or throwing when expected nodes are absent.

## Lifecycle

| Phase | Date | Commit | Notes |
|-------|------|--------|-------|
| Ready | 2026-04-01 | 773bcc9 | Initial creation |
| Complete | 2026-04-01 | 4d41a30 | Acceptance criteria verified and implementation finished |

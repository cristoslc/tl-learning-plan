---
id: tlp-n4jj
status: closed
deps: [tlp-hdgj]
links: []
created: 2026-04-01T16:43:56Z
type: task
priority: 1
assignee: cristos
parent: tlp-8zb4
tags: [spec:SPEC-004]
---
# Bind Mermaid nodes to capability cards

GREEN step for SPEC-004. Add stable targets for capability cards and wire Mermaid-rendered nodes to scroll to the matching card without breaking filters, theme toggles, or progress state.


## Notes

**2026-04-01T16:47:40Z**

Implemented SPEC-004 in dist/capability-map.html: capability cards now render with stable ids, Mermaid rendering is run explicitly after initialize, and rendered graph nodes matching flowchart-C<n>-* are bound as clickable/keyboard-accessible in-page links.

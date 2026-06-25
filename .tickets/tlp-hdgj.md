---
id: tlp-hdgj
status: closed
deps: []
links: []
created: 2026-04-01T16:43:56Z
type: task
priority: 1
assignee: cristos
parent: tlp-8zb4
tags: [spec:SPEC-004]
---
# Record failing navigation behavior

RED step for SPEC-004. Confirm the current Mermaid graph nodes do not navigate to their capability cards and capture the rendered node selector strategy for implementation.


## Notes

**2026-04-01T16:44:39Z**

Inspected current capability-map implementation and Mermaid SVG structure. Capability cards render without stable ids/anchors, and the graph SVG exposes node groups like flowchart-C1-0 / flowchart-C10-0 but no click binding exists in dist/capability-map.html. This is the failing baseline for SPEC-004.

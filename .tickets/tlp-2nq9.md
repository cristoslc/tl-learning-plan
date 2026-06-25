---
id: tlp-2nq9
status: closed
deps: [tlp-n4jj]
links: []
created: 2026-04-01T16:43:56Z
type: task
priority: 1
assignee: cristos
parent: tlp-8zb4
tags: [spec:SPEC-004]
---
# Verify jump behavior and document evidence

REFINE/verify step for SPEC-004. Re-run browser checks after implementation, confirm the correct card is targeted for multiple nodes, and capture evidence before closing the plan tasks.


## Notes

**2026-04-01T16:47:40Z**

Verification evidence: browser automation against http://host.docker.internal:8765/dist/capability-map.html confirmed graph nodes receive role=link/tabindex=0, click navigation moved capabilities 1/2/8/10/11 into view with matching #capability-<n> hashes, Enter-key navigation still worked after filter=video and theme=night, and jumpToCapability(999) returned false without throwing or logging console errors.

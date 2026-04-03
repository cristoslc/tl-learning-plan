---
title: "Retro: Video/Podcast Summary Linking"
artifact: RETRO-2026-04-02-summary-links
track: standing
status: Active
created: 2026-04-02
last-updated: 2026-04-02
scope: "Adding summaryUrl links to video/podcast resources in capability-map.html"
period: "2026-04-02"
linked-artifacts: []
---

# Retro: Video/Podcast Summary Linking

## Summary

Added `summaryUrl` fields to 14 video/podcast entries in capability-map.html. Discovered that ~15 summaries already existed in `dist/summaries/` — the work was simply connecting existing summaries to their media resources rather than creating new summaries.

## Reflection

### What went well

- **Reverse-engineering the pattern** from existing summary links (found at line ~790) enabled rapid identification of the exact changes needed.
- **Grep for media types** (`video|podcast`) quickly identified all candidates requiring summary links.

### What was surprising

- **Summaries already existed** — the "work" of creating summaries had already been done in a prior session; the gap was purely linking.
- **One entry legitimately lacks a summary** — "Developer to Architect — Lesson Series" (line 800) is a 200+ lesson series, not a single video, so no single summary applies.

### What would change

- **No changes needed** — this was a simple data-linking task. The process was efficient.

### Patterns observed

- No new patterns — this mirrors the prior retro's theme of "discover existing work and connect it" rather than creating net new content.

## Learnings captured

No new learnings — this was a straightforward linking task. The prior retro's guidance on systematic content audits remains relevant but wasn't needed for this task.
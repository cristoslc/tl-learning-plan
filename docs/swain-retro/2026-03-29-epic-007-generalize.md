---
title: "Retro: EPIC-007 Generalize for Public Sharing"
artifact: RETRO-2026-03-29-epic-007-generalize
track: standing
status: Active
created: 2026-03-29
last-updated: 2026-03-29
scope: "Generalization of TL learning plan for public sharing"
period: "2026-03-28 — 2026-03-29"
linked-artifacts:
  - EPIC-007
---

# Retro: EPIC-007 Generalize for Public Sharing

## Summary

Generalized a TL development curriculum for public sharing in a two-day session. Stripped identifying content from 50+ files, removed governance artifacts and infrastructure, wiped git history, fixed broken references, added a dark mode toggle, deployed to GitHub Pages, and cut v1.0.0.

## Reflection

### What went well

- **Crash recovery worked.** The session crashed mid-task but all work was recoverable from uncommitted files in the main worktree. The session bookmark accurately described what had been created, making recovery fast.
- **Parallel agent dispatch** for independent content-editing tasks cut wall-clock time. Independent tasks are good candidates for parallelization.
- **Screenshot-driven iteration** on the HTML design (dark mode palette, mobile layout, header structure, pane dividers) converged in ~5 rounds. Visual feedback is more efficient than spec-driven design for UI polish.
- **Scope reduction was the right call.** Redundant old content was cut decisively rather than generalized, saving significant work.

### What was surprising

- **Identifying term leaks persisted through multiple sweeps.** Short codes and abbreviations weren't caught by initial grep patterns targeting longer strings. Each leak required another history purge.
- **The capability-map.html was the hardest file.** At 1000+ lines with embedded JS data objects, it resisted both agent edits and simple sed replacements. Context-dependent rewrites needed manual intervention.
- **Worktree + git reinit don't compose.** Reinitializing `.git` inside a worktree creates a local repo that doesn't propagate back. Work done after reinit was lost when the worktree was removed.

### What would change

- **Do all content work first, audit comprehensively, then purge history exactly once.** Multiple history purges were needed as leaks were discovered incrementally. A single comprehensive audit before the first purge would have avoided this.
- **Grep for short codes separately.** Initial search patterns were long compound regexes. Short abbreviations need their own targeted scan because they hide in natural-seeming prose.
- **Don't reinit inside worktrees.** History wipes should happen on main as the final step.
- **Give agents explicit absolute paths** when working in worktrees. One agent reported success but edited files at the wrong path — its edits were silently lost.

### Patterns observed

- **Interactive aliases block automation.** Shell aliases with `-i` flags prompt for confirmation, breaking non-interactive commands. Workaround: use explicit paths or override with full binary paths.
- **GPG signing failures** from credential managers required workarounds on every commit. A session-level config would have been cleaner.

## Learnings captured

| Memory file | Type | Summary |
|------------|------|---------|
| feedback_retro_history_purge.md | feedback | Do all content work before purging history; purge exactly once |
| feedback_retro_short_codes.md | feedback | Grep for short internal codes separately from long identifying strings |
| feedback_retro_worktree_reinit.md | feedback | Never reinit git inside a worktree; do repo surgery on main |

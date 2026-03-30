---
title: "Retro: EPIC-007 Generalize for Public Sharing"
artifact: RETRO-2026-03-29-epic-007-generalize
track: standing
status: Active
created: 2026-03-29
last-updated: 2026-03-29
scope: "Full generalization of TL learning plan from company-internal to public-ready"
period: "2026-03-28 — 2026-03-29"
linked-artifacts:
  - EPIC-007
  - SPEC-002
  - SPEC-003
  - SPEC-004
  - SPEC-005
  - SPEC-006
  - SPEC-007
  - SPEC-008
---

# Retro: EPIC-007 Generalize for Public Sharing

## Summary

Took a company-internal TL development curriculum and generalized it for public sharing in a single two-day session. Stripped all identifying content from 50+ files, removed governance artifacts and infrastructure, wiped git history, fixed broken references, added a dark mode toggle, deployed to GitHub Pages, and cut v1.0.0.

## Artifacts

| Artifact | Title | Outcome |
|----------|-------|---------|
| EPIC-007 | Generalize for Public Sharing | Complete |
| SPEC-002 | Generalize Concept Map and Capabilities | Complete |
| SPEC-003 | Rewrite Track 01: Strategic Context | Complete |
| SPEC-004 | Generalize Tracks 02 and 03 | Complete |
| SPEC-005 | Remove Governance and Infrastructure | Complete |
| SPEC-006 | Wipe Git History | Complete |
| SPEC-007 | Fix Broken References | Complete |
| SPEC-008 | Dark Mode Toggle | Complete |

## Reflection

### What went well

- **Crash recovery worked.** The session crashed mid-SPEC-005 but all work was recoverable from uncommitted files in the main worktree. The session bookmark accurately described what had been created, making recovery fast.
- **Parallel agent dispatch** for SPEC-002/003 and SPEC-007/008 cut wall-clock time. Independent content-editing tasks are good candidates for parallelization.
- **Screenshot-driven iteration** on the HTML design (dark mode palette, mobile layout, header structure, pane dividers) converged in ~5 rounds. Visual feedback is more efficient than spec-driven design for UI polish.
- **Tracks deletion was the right call.** The operator recognized that tracks were redundant old content and cut them decisively rather than spending time generalizing them. Scope reduction late in the process saved significant work.

### What was surprising

- **Identifying term leaks persisted through multiple sweeps.** Short internal codes (AC1, AC2, FCA, ADA) weren't caught by the initial grep patterns which targeted longer strings (PlatformOne, Acme, etc.). Each leak required another history purge.
- **The capability-map.html was the hardest file.** At 1000+ lines with embedded JS data objects, it resisted both agent edits (agents edited wrong paths) and simple sed replacements (context-dependent rewrites needed). Required manual intervention multiple times.
- **Worktree + git reinit don't compose.** Reinitializing `.git` inside a worktree creates a local repo that doesn't propagate back. All work done after the reinit (dark mode, SPEC-007/008, file renames) was lost when the worktree was removed. Had to redo it on main.

### What would change

- **Do all content work first, audit comprehensively, then purge history exactly once.** We reinited the repo 4+ times as leaks were discovered incrementally. A single comprehensive audit pass before the first purge would have avoided this.
- **Grep for short codes separately.** The initial search patterns were long compound regexes. Short internal codes (AC1, AC2, FCA) need their own targeted scan because they hide in natural-seeming prose.
- **Don't reinit inside worktrees.** The history wipe should happen on main as the final step. Worktrees are for isolated development, not for repo surgery.
- **Give agents explicit absolute paths** when working in worktrees. The SPEC-008 agent reported success but edited files at the wrong path — its edits were silently lost.

### Patterns observed

- **Interactive `mv`/`cp` aliases block automation.** The shell has `-i` aliases that prompt for confirmation, breaking non-interactive commands. Workaround: use `cat > target` or explicit paths. This should be a standing feedback memory.
- **GPG signing failures** from 1Password required `git -c commit.gpgsign=false` on every commit. A session-level `git config` would have been cleaner.
- **The "remove docs, exclude .claude/.agents" decision** was made quickly during SPEC-006 but had downstream consequences — the spec docs themselves contained identifying terms as problem descriptions, and the swain skills/templates were lost. This was the right call for the public repo but meant losing the ability to run swain skills against this project.

## Learnings captured

| Memory file | Type | Summary |
|------------|------|---------|
| feedback_retro_history_purge.md | feedback | Do all content work before purging history; purge exactly once |
| feedback_retro_short_codes.md | feedback | Grep for short internal codes separately from long identifying strings |
| feedback_retro_worktree_reinit.md | feedback | Never reinit git inside a worktree; do repo surgery on main |

# Issue 4 — Incorporate "Patterns of Legacy Displacement"

Source: https://github.com/cristoslc/tl-learning-plan/issues/4
Article: https://martinfowler.com/articles/patterns-legacy-displacement/ (Cartwright, Horn & Lewis, Fowler.com, 2024)

## What the issue asks

Evaluate whether "Patterns of Legacy Displacement" should be worked into one or more capability modules — in whole or in parts. It is a candidate for at least Capability 2 (the issue anchors the "Decide How To Break The Problem Into Smaller Parts" section). Do not necessarily assign the entire reading; it could be a heavy Getting Started resource.

## What the article is

A hub article (plus 14 linked pattern pages) structuring legacy replacement around four activities:

1. **Understand the outcomes you want to achieve** — cost of change, business process improvement, retirement, disruption, "newer technology" (with the "Netflix Envy" and Feature Parity anti-patterns).
2. **Decide how to break the problem into smaller parts** — finding seams, mapping business capabilities, Event Storming / Wardley / capability mapping as discovery tools.
3. **Successfully deliver the parts** — Event Interception, Legacy Mimic, Divert the Flow, Transitional Architecture, canary/parallel run.
4. **Change the organization on an ongoing basis** — corporate antibodies, Inverse Conway Maneuver, protected pilots.

## Fit analysis per capability

| Capability | Fit | Rationale |
|---|---|---|
| 2 Scope the Problem | **Strong** | "Breaking the problem into smaller parts" is scoping: choose seams, extract thin slices, name what's deferred (vs Feature Parity big-bang). Pairs with existing scope-statement discipline. |
| 7 Read the Strategic Map | **Strong** | The treadmill narrative + outcomes section explains *why* a legacy replacement bet is made (or fails). Directly extends the existing Spolsky-rewrite / Caudill-counterpoint pair and Larson §3.6 Migrations row already in this capability. |
| 3 Find the Real Boundaries | **Good** | Seams in legacy = boundary discovery under real constraints; the Event Storming sidebar reinforces the existing Brandolini resource; "cross the legacy boundary, don't stop at it" sharpens the boundary-probing skill. |
| 8 Design from the Business | Moderate | "Identify Business Capabilities" pattern overlaps content already covered (Richardson, Tune, Azure domain analysis). Adding it would duplicate; skip. |
| 4, 5, 9, 10, 11, 1, 6 | Weak | Delivery mechanics (patterns for delivery) and org-change material are either too operational (4, 5) or already covered by stronger, more specific resources (9, 10). |
| 9 Lead the Conversation | Weak-moderate | The organizational-change cluster is interesting but the capability's focus is running sessions and explaining trade-offs; the article adds bulk without a distinct skill. Skip in this pass; can revisit. |

## Proposed changes (3 placements, all "Go Deeper" additions)

Content lives in `dist/capability-*.md`; the interactive page `dist/capability-map.html` embeds a JS data mirror of every resource row and must be hand-edited in the same change (SPEC-002's Astro ingestion pipeline is not built yet). A CHANGELOG entry documents the addition.

### 1. `dist/capability-02-scope-the-problem.md` — Go Deeper (add as second row, after Nick Tune)

| [Patterns of Legacy Displacement: Breaking the Problem into Smaller Parts](https://martinfowler.com/articles/patterns-legacy-displacement/#DecideHowToBreakTheProblemIntoSmallerParts) — Cartwright, Horn & Lewis | Article | 15 min | The section the issue cites: find seams, extract thin slices deliverable with minimal dependencies, and why the alternatives (Feature Parity, big bang) keep organizations on the replacement treadmill. Scoping for the special case of replacing a legacy system. |

Rationale: section-anchored URL, short, directly about deciding what to break off and deliver independently.

### 2. `dist/capability-07-strategic-map.md` — Go Deeper (add after Larson §3.6 Migrations row)

| [Patterns of Legacy Displacement](https://martinfowler.com/articles/patterns-legacy-displacement/) — Cartwright, Horn & Lewis | Article | ~45 min | Why legacy replacements fail (treadmill, BAU-vs-programme drift, Feature Parity) and how to sequence outcomes → seams → delivery → org change. The pattern-level companion to the rewrite-debate pair at the top of this capability. |

Rationale: the whole article belongs here as the "how to actually run the migration" text next to Larson's Migrations chapter; ~45 min is acceptable for a heavy Go Deeper row in this capability, which already carries the strategic-migration theme.

### 3. `dist/capability-03-find-boundaries.md` — Go Deeper (add after the Vernon SE Radio row, before Hard Parts Ch 5)

| [Patterns of Legacy Displacement: Getting Started](https://martinfowler.com/articles/patterns-legacy-displacement/#DecideHowToBreakTheProblemIntoSmallerParts) — Cartwright, Horn & Lewis | Article | 15 min | Seams in a legacy estate are boundary candidates: use Event Storming, Wardley mapping, and capability mapping to see how one big system serves many business needs, then find the first extraction seam. Warns against stopping discovery at the legacy boundary. |

Rationale: anchors the boundary-discovery-in-legacy angle and names the same discovery tools the capability already teaches (Event Storming via Brandolini).

### Mirrors and bookkeeping

- **`dist/capability-map.html`**: add the three matching entries to the JS data objects for capabilities 2, 7, 3 (format `article`, correct `time`, condensed `desc`, `summaryUrl` omitted — no summary exists and article rows in this repo never carry summaries). Keep placement order identical to the markdown tables.
- **`CHANGELOG.md`**: new bullet(s) under a "Research/Content" note or an `### Added` line in an unreleased section, matching the 1.1.0 style.
- No media summary needed: this is an article; summaries in this repo are for video/podcast/interview sources only. The two Thoughtworks podcast episodes on the article are optional future enrichment (out of scope unless asked).

## Order of work

1. Markdown edits: capability-02, capability-07, capability-03 (one commit).
2. capability-map.html JS data mirror (one commit) — then eyeball the rendered page locally for placement/filter sanity.
3. CHANGELOG entry (same commit as 2 or separate).
4. Verify: build/lint if configured (none found — plain static files), link-check the three URLs, confirm filter behavior (articles render in the article filter).

## What I'm unsure about

1. **Placement in Cap 3 vs Cap 8**: I chose Cap 3 (boundaries) over Cap 8 (business capabilities) because Cap 8 already has three near-identical capability-mapping resources. If the intent of the issue ("at least Module 9" — note the issue's module numbering may predate the current capability numbering) was Cap 9 "Lead the Conversation", my analysis says the article fits Cap 9 poorly; I'd flag that mismatch to you before proceeding.
2. **Section-anchored vs whole-article URLs**: I used the `#DecideHowToBreakTheProblemIntoSmallerParts` anchor for Caps 2 and 3 and the whole article for Cap 7. Anchors on martinfowler.com are stable heading ids; if you'd rather link the whole article everywhere and let the reader navigate, that's a one-line change each.
3. **Time estimates**: I set 15 min for the section excerpt and ~45 min for the whole article; adjust to taste.
4. **Whether "Getting Started" text in Cap 3 should instead be the Getting Started + Event Storming sidebar anchor** (`#EventStorming-TheSwissArmyKnifeOfModernProcessMapping`) — the sidebar is a tighter tie to the Brandolini summary already in Cap 3. Either works; I lean to the seams anchor with the Event Storming mention in the description.
5. **Duplicate-link concern**: the article would appear in three capabilities. Precedent exists (Architect Elevator appears in Cap 8 and Cap 9; FSA Ch 19 in Cap 2 and Cap 10), so this follows repo convention.

Nothing has been changed yet — awaiting your confirmation on the three placements (and the Cap 3 vs Cap 9 question) before implementing.
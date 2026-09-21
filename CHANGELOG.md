# Changelog

## 1.1.1 — 2026-09-21

### What shipped

#### "Patterns of Legacy Displacement" Worked Into Three Capabilities

Cartwright, Horn & Lewis's legacy-modernization article (martinfowler.com) is now placed in:

- **Capability 2 (Scope the Problem)** — the "Breaking the Problem into Smaller Parts" section: seams, thin slices, Feature Parity/big-bang as anti-patterns
- **Capability 7 (Read the Strategic Map)** — the full article: why legacy replacements fail (treadmill, BAU-vs-programme drift) and how to sequence outcomes → seams → delivery → org change
- **Capability 3 (Find the Real Boundaries)** — the same seams section as boundary discovery in legacy estates, alongside the existing Event Storming resource

Section-anchored URLs for Capabilities 2 and 3; whole article for Capability 7. No media summary — article resources are not summarized in this program. (Issue #4)

## 1.1.0 — 2026-04-10

### What shipped

#### Clickable Capability Map

Mermaid graph nodes are now interactive. Click any capability node to jump directly to its card with a smooth scroll and 3.2s glow highlight animation. Keyboard accessible — nodes support focus, Enter, and Space.

- Added summaryUrl links for video and podcast resources
- Added Will Larson engineering strategy summary and links
- Refined capability text and practice exercises for clarity
- Reordered resource lists in Capability 4 (Pressure-Test a Design)

### Research

- Assessment design trove — 7 sources collected on placement tests and self-assessment patterns


## 1.0.0 — 2026-03-29

Initial public release of the TL Capability Map — a capability-based development program for Tech Leads transitioning from application expertise to architectural thinking. Eleven capabilities, each with a situation description, curated resources, a practice exercise, and a readiness check. Designed to be adapted by any engineering manager for their team.

### What shipped

#### Interactive Capability Map

Single-page HTML application with 11 capability cards, collapsible resource sections (Start Here / Go Deeper / Practice This), format filters (video, article, podcast, book), localStorage-backed progress tracking, and a Mermaid-rendered dependency graph showing how capabilities connect.

#### Dark Mode with Day/Night/Auto Toggle

Three-state theme switcher in the page header. Auto follows system preference via prefers-color-scheme. FOUC prevention script in <head> applies the theme before first paint. Neutral dark-grey palette with WCAG AA contrast ratios. Smooth CSS transitions enabled after initial render.

- GitHub Pages deployment with redirect from index to capability map
- 19 structured media summaries linked from capability resource sections via GitHub-rendered blob URLs
- Responsive mobile layout — header, map, then capabilities in single-column flow on small screens



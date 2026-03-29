# Changelog

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



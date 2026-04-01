# Architecture Overview

This vision keeps the published site static while shifting authorship to source assets:

- Curriculum content from markdown in `dist/`
- Capability graph from `dist/capability-graph.mmd` (authoritative after one-time extraction)
- Presentation from Astro templates/components that preserve the current `capability-map.html` structure and styling

```mermaid
flowchart LR
    markdown_sources["Markdown Sources (dist/*.md)"] --> astro_build["Astro Build Pipeline"]
    mermaid_source["Mermaid Source (dist/capability-graph.mmd)"] --> astro_build
    astro_templates["Parity Templates (Astro components/layout)"] --> astro_build
    astro_build --> generated_html["Generated capability-map.html"]
    generated_html --> publish_target["Published Static Site"]
```

Key boundary: no runtime backend, no dynamic publishing service, no redesign layer.

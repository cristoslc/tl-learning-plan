# Architecture Overview

This initiative coordinates three layers:

1. Source layer: markdown files and canonical Mermaid `.mmd`
2. Generation layer: Astro templates/components and build scripts
3. Output layer: static HTML delivered with parity to the current capability map

```mermaid
flowchart TD
    source_markdown["Source Markdown Files"] --> parse_content["Astro Content Ingestion"]
    source_mermaid["Source Mermaid File (capability-graph.mmd)"] --> parse_mermaid["Mermaid Injection Step"]
    parse_content --> assemble_page["Page Assembly Pipeline"]
    parse_mermaid --> assemble_page
    parity_components["Parity Components and CSS Tokens"] --> assemble_page
    assemble_page --> build_output["Generated capability-map.html"]
    build_output --> parity_gate["Parity Validation Gate"]
```

Primary risk control: parity validation gate before publishing.

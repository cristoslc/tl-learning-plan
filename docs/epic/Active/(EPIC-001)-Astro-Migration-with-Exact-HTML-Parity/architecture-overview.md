# Architecture Overview

This epic introduces a static generation seam without changing the user-facing design contract.

```mermaid
flowchart LR
    input_md["Capability Markdown"] --> astro_content["Astro Content Loader"]
    input_mmd["capability-graph.mmd (canonical)"] --> mermaid_step["Mermaid Integration"]
    baseline_html["capability-map.html Baseline"] --> parity_spec["Parity Constraints"]
    astro_content --> page_model["Page View Model"]
    mermaid_step --> page_model
    parity_spec --> page_model
    page_model --> rendered_html["Generated capability-map.html"]
    rendered_html --> validation["Structure and behavior parity checks"]
```

Architectural intent: isolate content generation concerns while retaining the existing visual contract.

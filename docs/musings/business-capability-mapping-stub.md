# Musing: The "Identify Business Capabilities" stub and the missing end-to-end synthesis

Source: AI chat export `chat-export-1787594667879.json` — a research conversation about `capability-map.html#capability-8`.

## The problem

Capability 8 on the learning plan lists Martin Fowler's *"Identify Business Capabilities"* stub as a **START HERE** resource. It's a stub — there is no fully-fleshed-out version published by the same authors yet. Learners pointed at it get a dead end on the thing the plan calls "START HERE."

## Fully-fleshed-out substitutes found

Same authors (Cartwright, Horn, Lewis):
- **Thoughtworks "Patterns of Legacy Displacement" podcast Part 2** — Lewis verbally explains business capabilities in the legacy-displacement context; closest to the "why/what" of the stub. https://www.thoughtworks.com/insights/podcasts/technology-podcasts/patterns-legacy-displacement-pt1
- **GOTO Copenhagen 2022 talk** (Horn & Cartwright) — same pattern clusters incl. business capability identification.
- **Main "Patterns of Legacy Displacement" hub article** — fleshed out; covers capability mapping alongside Event Storming / Wardley Mapping / Domain Mapping; "find seams... considering how elements map to different business capabilities." https://martinfowler.com/articles/patterns-legacy-displacement/
- **"Create Town Plan" sibling stub** — more developed than the target stub: gives a working definition ("people, processes and tools that describe a stable boundary within a business"), core-banking examples, town-planning metaphor. https://martinfowler.com/articles/patterns-legacy-displacement/create-town-plan.html

Other authors:
- **Ian Cooper — "Capability Mapping" (NDC)** — full talk on identifying business capabilities for microservices.
- **Thoughtworks blog — "How to Keep Large Projects on Track with Business Capability Mapping"** — detailed 6-step process (independent research → validation sessions → visualization → workshop → facilitation → maintenance), red-flag catalog, "Goldilocks" principle. https://www.thoughtworks.com/en-us/insights/blog/legacy-modernization/keeping-large-projects-on-track-with-business-capability-mapping
- **Sriram Narayan — "Business Capability Centric" (martinfowler.com)** — cleanest definition with e-commerce/insurance/telecom examples; strategic vs. utility distinction. https://martinfowler.com/bliki/BusinessCapabilityCentric.html
- **Chris Richardson** — microservices.io "Decompose by Business Capability." https://microservices.io/patterns/decomposition/decompose-by-business-capability.html
- **Sam Newman — *Building Microservices*** (2nd ed).

## The concrete "what does a capability look like" angle (flow: capabilities → shared platform services → bounded contexts)

The deepest answer to the research conversation's follow-up:
- **Trond Hjorteland — "From Capabilities to Services Modelling" (SlideShare)** — best match for the capabilities → shared platform services flow, with real maps (Norwegian Labour & Welfare, ISP) and the Udi Dahan quote "a service is the technical authority for a specific business capability." https://www.slideshare.net/trondhr/from-capabilities-to-services-modelling-for-businessit-alignment-v2
- **Nick Tune — "Product-aligned vs Capability-aligned Organization Design"** — clearest concrete illustration (supermarket: physical store/online/mobile each re-implementing user management, loyalty, order management → capability-aligned shared services); includes trade-offs and failure modes (selfish silos, over-complex generic capabilities, empire building, adoption, funding). https://medium.com/nick-tune-tech-strategy-blog/product-aligned-vs-capability-aligned-organisation-design-99309596adde
- **Nick Tune — "Legacy Architecture Modernisation with Strategic DDD"** — the full flow: Business Model Canvas → Wardley → IT portfolio (Core Domain Charts) → EventStorming → Bounded Contexts → Platform Architecture. https://medium.com/nick-tune-tech-strategy-blog/legacy-architecture-modernisation-with-strategic-domain-driven-design-3e7c05bb383f

## Why no one has written the end-to-end synthesis

Three structural gaps, not because the approach is wrong:
1. **Two communities, two vocabularies** — enterprise architecture (capability maps; TOGAF/ArchiMate) vs. software architecture (bounded contexts; DDD). Few bridge both.
2. **The middle layer (shared platform services) is the least mature, most contested part** — hardest organizational problems live here.
3. **The approach IS adopted, just not written as a single pattern** — components are all canonical (capability map / Wardley / core-domain / platform engineering / bounded contexts).

Closest canonical candidates:
- **Susanne Kaiser — *Architecture for Flow*** (2024) — deliberate unified synthesis of Wardley Mapping + DDD + Team Topologies; canvas; but starts from Wardley, not capability map.
- **Nick Tune — *Architecture Modernization*** (Manning 2024) — full chapter path (Wardley, product taxonomy, Eventing, domains/subdomains, IT portfolio, Team Topologies, platform) — closest published walkthrough of the exact flow.

## Open question — what to do with the learning plan

Not whether the stub is a problem (it is) but which substitutes to fold into Capability 8's START HERE chain, and whether the plan should teach the *whole* capabilities → shared platform services → bounded-context pipeline as one thread, since no single resource covers it end-to-end. Candidate default chain: Narayan (define) → Tune supermarket (concrete, shared-services bridge) → Hjorteland slides (capability→service mapping) → Tune legacy-modernization article (connect to bounded contexts) → Thoughtworks blog (facilitation practice).

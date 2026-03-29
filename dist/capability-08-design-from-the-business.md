# 8. Design from the Business Down

[Back to Capability Map](concept-map)

**The situation:** You're in a room with an architect, a whiteboard, and a mandate to build a platform. The proposal has 30+ modules. You have domain expertise and a business capability map from a stakeholder workshop. But you don't have a method for going from "what the business does" to "what the platform builds" — and neither does the architect, because they don't know your business the way you do.

**What changes:** You learn to work in three layers: what the business does (capabilities), what the platform builds (services), and what the company sells (offerings). Capabilities are stable — they don't change when the technology changes. Platform services are what you design. The value chain is the organizing axis, not the module list. Where a capability produces data for others to consume, you apply data product thinking — treating that output as something subscribable, versioned, and owned by a domain, not just a table in a shared database. Wardley mapping adds the build-vs-buy dimension: which capabilities are commodity, which are differentiating, which are novel.

**You're ready when:** Given a business capability, you can identify the platform services it needs, explain why each service exists, and trace which service offerings depend on it. You can look at a proposal's module list and say "these three modules are actually one platform service under field data acquisition" or "this module doesn't map to any business capability we confirmed — what is it?"

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Identify Business Capabilities](https://martinfowler.com/articles/patterns-legacy-displacement/identify-business-capabilities.html) — Cartwright, Horn & Lewis | Article | 15 min | Practical guide to identifying business capabilities as the first step in architecture. Shows how to decompose an organization into stable capability units. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Business Capability Centric](https://martinfowler.com/bliki/BusinessCapabilityCentric.html) — Martin Fowler | Article | 5 min | What it means to organize teams and systems around capabilities rather than technical layers. Connects to Conway's Law. |
| [Platform Tech Strategy: The Three Layers](https://www.thoughtworks.com/insights/blog/platform-tech-strategy-three-layers) — ThoughtWorks | Article | 12 min | The three-layer model and how business capabilities map into platform services. Directly mirrors how platform investment maps are structured. |
| [Introduction to Value Chain Mapping](https://www.youtube.com/watch?v=NnFeIt-uaEc) — Simon Wardley ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/introduction-to-value-chain-mapping-simon-wardley.md)) | Video | 40 min | Wardley's foundational talk: why value chain position determines what to build, buy, or outsource. The evolution dimension the capability map doesn't give you. |
| [Wardley Maps (free book) — Ch 1-2](https://learnwardleymapping.com/book/) — Simon Wardley | Guide | ~60 min | Chapters 1 ("On Being Lost") and 2 ("Finding a Path"). The complete on-ramp to Wardley mapping. Free, CC-licensed. |
| [Use Domain Analysis to Model Microservices](https://learn.microsoft.com/en-us/azure/architecture/microservices/model/domain-analysis) — Azure Architecture Center | Article | 20 min | The full chain from capability identification to bounded context definition to service design. Uses a concrete example. Bridge between Capability 6 and Capability 2. |
| [Legacy Architecture Modernisation with Strategic DDD](https://medium.com/nick-tune-tech-strategy-blog/legacy-architecture-modernisation-with-strategic-domain-driven-design-3e7c05bb383f) — Nick Tune | Article | 15 min | Business capability analysis as the starting point for bounded contexts. Bridges capability mapping, EventStorming, and the Bounded Context Canvas. |
| [Core Domain Patterns](https://medium.com/nick-tune-tech-strategy-blog/core-domain-patterns-941f89446af5) — Nick Tune | Article | 10 min | Core Domain Charts: classify capabilities as core, supporting, or generic. Plot by complexity and differentiation. Directly informs build/buy/outsource decisions. |

### Practice This

Pick one business capability row from your team's capability map (e.g., "Data enhancement" or "Report generation"). List the platform services in that row. For each: why does this service exist? Which service offerings need it? Now compare to a recent architecture proposal's module list — which modules cover this same ground? Where do they split what should be together? Where do they combine what should be separate? Bring your mapping to a session.

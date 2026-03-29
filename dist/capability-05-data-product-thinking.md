# 5. Data Product Thinking

[Back to Capability Map](concept-map)

**The situation:** A domain in your system produces data that other domains, other teams, or external consumers need. Right now it's a database table someone queries directly, or a CSV export, or an API that returns whatever the producer decided to expose. When the schema changes, consumers break. When the data is wrong, nobody knows until a report looks funny.

**What changes:** You learn to treat data that crosses a boundary as a product — something with an owner, a contract, a quality guarantee, and a versioning strategy. Not every output needs this treatment, but when a capability produces data for others to consume, you apply a specific design discipline: who owns it, who can discover it, what freshness and accuracy guarantees does it carry, and how does it evolve without breaking consumers.

**You're ready when:** You can look at a data flow that crosses a domain boundary and say "this should be a data product because [multiple consumers / quality matters / schema will evolve]" or "this doesn't need product treatment because [single consumer / internal to the domain]." You can name the DAUTNIVS attributes and apply them to a real output.

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Data Mesh Principles and Logical Architecture](https://martinfowler.com/articles/data-mesh-principles.html) — Zhamak Dehghani | Article | 45 min | The four data mesh principles and DAUTNIVS — the 8 attributes that define a real data product. The canonical reference. |
| [Data Mesh Paradigm Shift](https://www.infoq.com/presentations/data-mesh-paradigm/) — Zhamak Dehghani ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/data-mesh-paradigm-shift-zhamak-dehghani.md)) | Video | 50 min | Dehghani's foundational talk — same principles with visuals showing domain-oriented data ownership in practice. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Dehghani Ch 3: Principle of Data as a Product](https://learning.oreilly.com/library/view/data-mesh/9781492092384/ch03.html) — Zhamak Dehghani | Book | ~45 min | Full DAUTNIVS treatment: what each attribute means, how to assess it, what "ownership" looks like. When someone says "data product," this is how you test whether they mean what Dehghani means. |
| [Dehghani Ch 11: Design a Data Product by Affordances](https://learning.oreilly.com/library/view/data-mesh/9781492092384/ch11.html) — Zhamak Dehghani | Book | ~45 min | The data product as architectural quantum — ownership, interfaces, contracts, quality guarantees. |
| [Dehghani Ch 9: The Logical Architecture](https://learning.oreilly.com/library/view/data-mesh/9781492092384/ch09.html) — Zhamak Dehghani | Book | ~40 min | How domains, data products, and platform planes interact as a system. Maps directly onto the three-layer model. |
| [Data Mesh Revisited](https://www.thoughtworks.com/insights/podcasts/technology-podcasts/data-mesh-revisited) — Dehghani, Parsons et al. ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/data-mesh-revisited-thoughtworks-podcast.md)) | Podcast | 50 min | Honest assessment three years later — what worked, what was hard, where data product thinking has matured. |
| [Hard Parts Ch 14: Managing Analytical Data](https://learning.oreilly.com/library/view/software-architecture-the/9781492086888/ch14.html) — Ford, Richards et al. | Book | ~40 min | Data mesh applied to the Sysops Squad case study. Compares data warehouse, data lake, and data mesh with concrete trade-offs. |

### Practice This

Pick a data flow in your team's platform that crosses a domain boundary — e.g., data flowing from one service into another team's reporting or processing pipeline. Apply the DAUTNIVS checklist: Is it Discoverable? Addressable? Understandable without calling the producer? Does it have Trustworthiness guarantees? Is it Natively accessible? Interoperable? Valuable on its own? Secure? Where does it fall short?

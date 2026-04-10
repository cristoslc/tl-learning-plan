# 4. Pressure-Test a Design

[Back to Capability Map](concept-map)

**The situation:** A proposed architecture looks clean on paper. Nobody's asking hard questions because it's early and everyone wants to move forward. But you've seen "clean on paper" before — the legacy system looked clean once too. You want to stress it, but you don't know where to push.

**What changes:** You learn that non-functional requirements are the pressure. Not vague ones ("it should be fast") — specific ones ("mobile users need to sync over unreliable connections with P95 under 200ms"). Each real NFR rules out some architectural options and constrains others. You stop evaluating designs by how they look and start evaluating them by what would break them. You also learn fitness functions — automated tests for architectural properties, so drift is caught by CI, not by a crisis.

**You're ready when:** Given a design, you can name the top 3 quality attributes that would stress it, explain which part of the design is most vulnerable to each, and sketch how you'd test for it.

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Lesson 73: Architecture Fitness Functions](https://developertoarchitect.com/lessons/lesson73.html) — Mark Richards ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/lesson-73-architecture-fitness-functions-mark-richards.md)) | Video | 10 min | Short, focused explanation of what fitness functions are and how they protect architectural characteristics. Best bang-for-the-buck intro. |
| [Lesson 37: Translating Quality Attributes to Business Concerns](https://developertoarchitect.com/lessons/lesson37.html) — Mark Richards ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/lesson-37-translating-quality-attributes-mark-richards.md)) | Video | 10 min | How to translate the "-ilities" into language that business stakeholders understand — critical for getting NFR investment prioritized. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Fitness Function-Driven Development](https://www.thoughtworks.com/en-us/insights/articles/fitness-function-driven-development) — ThoughtWorks | Article | 15 min | Making fitness functions a first-class part of the development cycle — architectural properties as testable, automatable constraints. |
| [Toward Agile Architecture: 15 Years of ATAM Data](https://www.infoq.com/articles/atam-quality-attributes/) — InfoQ | Article | 20 min | Empirical analysis of 31 architecture evaluations — reveals that modifiability, performance, availability, interoperability, and deployability are the quality attributes that actually drive trade-offs in practice. |
| [The Evolution of Evolutionary Architecture](https://www.infoq.com/podcasts/evolutionary-architecture-evolution/) — Rebecca Parsons ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/evolution-of-evolutionary-architecture-parsons-infoq.md)) | Podcast | 35 min | What changed between the first and second editions of BEA, how fitness functions have matured in practice. |
| [Building Evolutionary Architectures](https://gotopia.tech/episodes/232/building-evolutionary-architectures) — Rebecca Parsons, Neal Ford & James Lewis ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/building-evolutionary-architectures-parsons-ford-lewis.md)) | Video | 55 min | The three co-authors on evolutionary architecture principles and fitness functions as governance mechanisms — drawn from the 2nd edition of their book. |
| [Architecture as Code: Quantifying Architectural Trade-offs](https://youtu.be/r9cfeOEgHrM) — Neal Ford | Video | 55 min | Bridges the gap between architectural intuition and measurable proof — how to encode architectural decisions as runnable fitness functions so trade-offs become testable rather than debatable. |
| [Software Architecture: The Hard Parts](https://gotopia.tech/episodes/213/software-architecture-the-hard-parts) — Neal Ford & Mark Richards ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/software-architecture-the-hard-parts-ford-richards-goto.md)) | Video | 55 min | Trade-off analysis for distributed architectures: service granularity, workflow orchestration, distributed transactions. |
| [BEA Ch 2: Fitness Functions](https://learning.oreilly.com/library/view/building-evolutionary-architectures/9781492097532/ch02.html) — Ford, Parsons et al. | Book | ~45 min | Extends Richards' Lesson 73 with the full taxonomy: atomic vs holistic, triggered vs continual, static vs dynamic, automated vs manual. |
| [BEA Ch 4: Automating Architectural Governance](https://learning.oreilly.com/library/view/building-evolutionary-architectures/9781492097532/ch04.html) — Ford, Parsons et al. | Book | ~60 min | New material: code-level fitness functions with ArchUnit, coupling metrics, linters as governance. Case study of restructuring while deploying 60 times/day. |
| [BEA Ch 7: Building Evolvable Architectures](https://learning.oreilly.com/library/view/building-evolutionary-architectures/9781492097532/ch07.html) — Ford, Parsons et al. | Book | ~45 min | New material: anti-corruption layers, sacrificial architectures, last responsible moment, Postel's Law. Greenfield principles directly relevant to new platform builds. |

### Practice This

Pick one quality attribute that matters for your team's platform (offline sync? multi-tenancy? data freshness?). Write it as a specific, measurable scenario: "When [stimulus], the system [response] within [measure]." Then trace through a recent architecture proposal: which component would this break first? What would you change?

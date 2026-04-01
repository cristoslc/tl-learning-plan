# 3. Find the Real Boundaries

[Back to Capability Map](concept-map)

**The situation:** You're looking at a system design — maybe an architecture proposal, maybe a whiteboard sketch — and it has boxes with names. Modules, services, components. The question you can't answer: are these *real* boundaries (different domains with different rules and different data) or just a first-pass grouping to help the conversation move forward?

**What changes:** You learn to test boundaries with three questions: Does it own its data? Would a different team draw the same line? How much does it need to talk across the boundary to do its job? Boundaries that are still provisional usually raise questions on at least one of these. You also learn that the number of boxes is not a quality signal — 30 modules isn't better or worse than 7 until you know why each boundary exists.

**You're ready when:** You can look at a system diagram and point to a specific boundary and say "this one is real because [data ownership / independent change / minimal cross-talk]" or "this one is worth probing further because [shared database / high coupling / org-chart-driven]."

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Bounded Context](https://martinfowler.com/bliki/BoundedContext.html) — Martin Fowler | Article | 10 min | Concise definition with examples of how the same concept ("product," "customer") means different things in different contexts. Read this first. |
| [DDD & Microservices: At Last, Some Boundaries!](https://www.youtube.com/watch?v=yPvef9R3k-M) — Eric Evans ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/ddd-microservices-at-last-some-boundaries-eric-evans.md)) | Video | 50 min | The person who invented bounded contexts explains how they give services real isolation — and how, without them, complexity tends to move from the codebase into service interactions. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [50,000 Orange Stickies Later](https://youtu.be/1i6QYvYhlYQ) — Alberto Brandolini ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/50000-orange-stickies-later-alberto-brandolini.md)) | Video | 50 min | EventStorming — a workshop technique where domain boundaries emerge naturally from mapping business events. Useful when you need to discover boundaries rather than just evaluate proposed ones. |
| [Practical DDD: Bounded Contexts + Events => Microservices](https://www.infoq.com/presentations/microservices-ddd-bounded-contexts/) — Indu Alagarsamy ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/practical-ddd-bounded-contexts-events-microservices-indu-alagarsamy.md)) | Video | 50 min | Worked example through e-commerce showing how "product" means different things in different contexts, then uses events to achieve autonomous services. |
| [Bounded Context Canvas V3](https://medium.com/nick-tune-tech-strategy-blog/bounded-context-canvas-v2-simplifications-and-additions-229ed35f825f) — Nick Tune | Article | 15 min | A practical workshop tool for mapping what a bounded context owns, its communication, and its business alignment. Something you can actually use in a session. |
| [Identify Microservice Boundaries](https://learn.microsoft.com/en-us/azure/architecture/microservices/model/microservice-boundaries) — Microsoft Azure Architecture Center | Article | 20 min | Step-by-step guidance on using domain analysis to identify bounded contexts. Prescriptive and concrete. |
| [Vaughn Vernon on Strategic Monoliths and Microservices](https://se-radio.net/2022/01/episode-495-vaughn-vernon-on-strategic-monoliths-and-microservices/) — SE Radio ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/vaughn-vernon-strategic-monoliths-microservices-se-radio.md)) | Podcast | 60 min | How bounded contexts inform whether you need microservices at all, and how to derive models that inform architectural boundaries. |
| [Hard Parts Ch 5: Component-Based Decomposition Patterns](https://learning.oreilly.com/library/view/software-architecture-the/9781492086888/ch05.html) — Ford, Richards et al. | Book | ~90 min | Six-step process for extracting services from a monolith. The most detailed decomposition guide available. |
| [Hard Parts Ch 7: Service Granularity](https://learning.oreilly.com/library/view/software-architecture-the/9781492086888/ch07.html) — Ford, Richards et al. | Book | ~45 min | The disintegrators/integrators framework — structured reasons to split vs keep together. Directly applicable to evaluating a proposal's module decomposition. |
| [FSA Ch 7: Scope of Architecture Characteristics](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch07.html) — Richards & Ford | Book | ~30 min | Introduces the "architecture quantum" — the independently deployable unit with high functional cohesion. Changes how you think about where characteristics apply. |

### Practice This

Take 3 modules from a recent architecture proposal at your company. For each: does it own its data? Would a team coming fresh to the problem still draw this boundary? What cross-boundary communication does it need? Write up your assessment — agreement, uncertainty, or "I'd need to know more about X."

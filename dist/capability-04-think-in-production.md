# 4. Think in Production

[Back to Capability Map](concept-map)

**The situation:** The architecture looks good on the whiteboard. The design review passed. Then it ships, and you discover there's no way to tell if offline sync is silently dropping records, no runbook for when the data pipeline stalls, and the only person who knows how the reconciliation service works is on vacation.

**What changes:** You learn to design for day 2, not just day 1. Every service needs answers to: how do I know it's healthy? How do I know it's broken? What does the operator do when it breaks? How do I deploy a fix without downtime? You stop treating observability and operability as things you add after launch and start treating them as constraints that shape the design.

**You're ready when:** Given a proposed service, you can sketch its health signals (what to monitor), its failure modes (what breaks and how you'd know), and its recovery path (what the operator does). You push back on designs that can't answer these questions.

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Lesson 37: Translating Quality Attributes](https://developertoarchitect.com/lessons/lesson37.html) — Mark Richards ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/lesson-37-translating-quality-attributes-mark-richards.md)) | Video | 10 min | Translating the "-ilities" into operational concerns. Bridges design intent to production reality. |
| [Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/) — Google SRE Book (Ch 6) | Article | 20 min | The four golden signals and why monitoring should answer "what's broken, and why?" Free chapter. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Implementing Service Level Objectives](https://sre.google/sre-book/service-level-objectives/) — Google SRE Book (Ch 4) | Article | 25 min | How to define SLIs, SLOs, and SLAs for objective service health measurement. |
| [Building Evolutionary Architectures](https://gotopia.tech/episodes/232/building-evolutionary-architectures) — Parsons, Ford & Lewis ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/building-evolutionary-architectures-parsons-ford-lewis.md)) | Video | 55 min | Fitness functions as automated operational governance — catching drift in CI, not in production. |
| [BEA Ch 4: Automating Architectural Governance](https://learning.oreilly.com/library/view/building-evolutionary-architectures/9781492097532/ch04.html) — Ford, Parsons et al. | Book | ~60 min | Code-level fitness functions, coupling metrics, linters as governance. Making architectural properties testable in the pipeline. |
| [DDIA 2e Ch 9: The Trouble with Distributed Systems](https://learning.oreilly.com/library/view/designing-data-intensive-applications/9781098119058/ch09.html) — Kleppmann & Riccomini | Book | ~60 min | Everything that can go wrong: unreliable networks, clocks, process pauses. Why distributed systems fail differently than monoliths. |

### Practice This

Pick one service from your team's platform (e.g., offline sync, data processing, report generation). Answer: What are its health signals? How would an operator know it's silently failing? What's the recovery procedure? What happens to upstream/downstream services when it's down? If you can't answer these, that's the gap.

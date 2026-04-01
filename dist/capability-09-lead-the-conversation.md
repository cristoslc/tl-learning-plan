# 9. Lead the Conversation

[Back to Capability Map](concept-map)

**The situation:** You have the analysis — boundaries, pressure tests, data product design, strategic context, a capability-to-platform mapping. Now you need to do something with it. Someone is proposing an architecture. Leadership wants to know if it's right. Your team needs to understand why decisions are being made.

**What changes:** The vocabulary stops being foreign — not because you memorized definitions, but because you've used the concepts to do real work. You can explain a trade-off to a design partner, justify a scope decision to a director, and walk a developer through why a boundary exists. You can sit in a co-design session and say "our capability map shows X, the proposal's module list shows Y — let's reconcile them together" rather than just reacting to a proposal.

**You're ready when:** You can run a working session — not just attend one. You can present your domain map in a cross-functional session and defend your boundary choices. You can explain to leadership why "data mesh ready" doesn't mean building a data mesh. You can teach a teammate what a bounded context is by pointing at a real one in your system.

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Starbucks Does Not Use Two-Phase Commit](https://www.enterpriseintegrationpatterns.com/ramblings/18_starbucks.html) — Gregor Hohpe | Article | 15 min | The best non-academic intro to async messaging and eventual consistency. A model for how to explain complex concepts simply. |
| [The Architect Elevator — Visiting the Upper Floors](https://martinfowler.com/articles/architect-elevator.html) — Gregor Hohpe | Article | 15 min | How architects translate between business strategy and technical execution — the skill of communicating across organizational levels. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Data Consistency Using Sagas](https://www.infoq.com/presentations/saga-microservices/) — Chris Richardson ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/data-consistency-using-sagas-chris-richardson.md)) | Video | 50 min | Practical walkthrough of the saga pattern — orchestration vs choreography. After this, "saga" becomes a concrete design tool rather than a vague term. |
| [When to Use Microservices (And When Not To)](https://gotopia.tech/episodes/20/moving-to-microservices-with-sam-newman-and-martin-fowler) — Sam Newman & Martin Fowler ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/when-to-use-microservices-newman-fowler.md)) | Video | 35 min | When microservices are and aren't the best fit. A balanced position you can take into a room. |
| [Consumer-Driven Contracts](https://martinfowler.com/articles/consumerDrivenContracts.html) — Ian Robinson | Article | 25 min | How consumers express expectations that providers must satisfy. |
| [Turning the Database Inside Out](https://www.youtube.com/watch?v=fU9hR3kiOK0) — Martin Kleppmann ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/turning-the-database-inside-out-martin-kleppmann.md)) | Video | 45 min | Reframes databases as streams of immutable facts. Changes how you think about event sourcing. |
| [Hard Parts Ch 12: Transactional Sagas](https://learning.oreilly.com/library/view/software-architecture-the/9781492086888/ch12.html) — Ford, Richards et al. | Book | ~50 min | 8 named saga patterns across three dimensions. After this you can name the exact pattern a workflow needs. |
| [Hard Parts Ch 13: Contracts](https://learning.oreilly.com/library/view/software-architecture-the/9781492086888/ch13.html) — Ford, Richards et al. | Book | ~35 min | Strict vs loose contracts, stamp coupling, the "need-to-know" principle. |
| [DDIA 2e Ch 5: Encoding and Evolution](https://learning.oreilly.com/library/view/designing-data-intensive-applications/9781098119058/ch05.html) — Kleppmann & Riccomini | Book | ~60 min | Comprehensive schema evolution treatment: JSON, Thrift, Protobuf, Avro. |
| [DDIA 2e Ch 8: Transactions](https://learning.oreilly.com/library/view/designing-data-intensive-applications/9781098119058/ch08.html) — Kleppmann & Riccomini | Book | ~75 min | ACID, isolation levels, write conflicts. Essential when someone says "we need transactions across services." |
| [Chris Richardson on Microservice Patterns](https://se-radio.net/2019/06/episode-370-chris-richardson-on-microservice-patterns/) — SE Radio ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/chris-richardson-microservice-patterns-se-radio.md)) | Podcast | 55 min | Broad vocabulary survey: sagas, API gateways, event sourcing, CQRS. |
| [Schema Evolution in Avro, Protobuf and Thrift](https://martin.kleppmann.com/2012/12/05/schema-evolution-in-avro-protocol-buffers-thrift.html) — Martin Kleppmann | Article | 20 min | Concrete backward/forward compatibility comparison. |

### Practice This

Pick one and do it for real: (1) Write a 5-minute presentation of your team's business capability map for a non-technical stakeholder. (2) Prepare a co-design agenda for a 90-minute architecture session: what you'll present, what you'll ask, what you need to leave with. (3) Teach a teammate one concept from this map using a real example from your platform, not a definition.

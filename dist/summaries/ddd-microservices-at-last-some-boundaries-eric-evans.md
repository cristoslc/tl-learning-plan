---
podcast_url: https://www.youtube.com/watch?v=yPvef9R3k-M
transcript_url:
updated: 2026-03-28
---

# DDD & Microservices: At Last, Some Boundaries! — Eric Evans

- **Speaker:** Eric Evans, creator of Domain-Driven Design
- **Event:** GOTO Conference
- **Format:** Conference talk + Q&A
- **Duration:** ~50 minutes

## Key Takeaways

Microservices finally give DDD practitioners the physical boundaries they've been trying (and failing) to create through logical means for decades.

> 1. **Bounded contexts need real walls, not dotted lines** — logical boundaries have historically failed because it's too easy to pierce them. Microservices make isolation the natural default.
> 2. **The context map shows power relationships, not data flow** — arrows point toward the team that controls the language, not the direction messages travel.
> 3. **Conformist vs. anti-corruption layer is a strategic choice** — conforming is cheap but means you inherit upstream mess; an ACL protects your model but costs translation effort.
> 4. **Not all of a large system will be well-designed** — say this three times in the mirror every morning. Overreaching for perfection leads to fixing everything and achieving nothing.
> 5. **Interchange contexts emerge; don't plan them upfront** — when one service's language becomes the de facto lingua franca, consider extracting a deliberate interchange language.
> 6. **Duplication can be cheaper than dependency** — if a capability isn't complex, duplicating it beats creating a dependency on another team's success (the DRY principle can be overvalued across service boundaries).

## Speaker Background

Eric Evans literally wrote the book on Domain-Driven Design (2003), introducing concepts like bounded contexts, ubiquitous language, aggregates, and context maps that are now foundational to how the industry thinks about software modeling. This talk captures Evans reflecting on microservices through the lens of decades spent trying to achieve proper isolation in software systems — and finding that microservices finally deliver the concrete boundaries DDD always needed.

## Core Thesis

The value of microservices for DDD isn't primarily about runtime concerns (scaling, failover, independent deployment). It's about what the deployment philosophy does to the **development phase**: it creates physical isolation that makes it unnatural to violate boundaries. Logical boundaries have been tried for decades and consistently fail because they don't survive the "rough and tumble" of enterprise development. Microservices provide the wall — not just the dotted line on the grass — that lets teams build precise, high-clarity models without external corruption.

## Major Topics Discussed

### [[00:01:05]](https://youtu.be/yPvef9R3k-M?t=65) Why Microservices Excited Evans

Evans was inspired by Netflix's approach — specifically the creation of **truly isolated spaces for autonomous teams**. He'd long advocated that teams doing complex modeling should have their own data stores rather than sharing a "mishmash" database. Microservices made this isolation the default rather than the exception. He also admired the "boldness" of concepts like cattle-not-pets and the Simian Army (Chaos Monkey), noting that this runtime philosophy unexpectedly changed how people approach development and design.

### [[00:04:57]](https://youtu.be/yPvef9R3k-M?t=297) The Rough and Tumble of Enterprise Development

Evans criticizes idealistic views of software development: "I am more than tired of sort of idealistic views of software development." Sophisticated domain models are "fragile like snowflakes" — they need protection to exist within the chaos of large organizations. If you value good design, you must value ways of **isolating that design from the outer world**, with a philosophy that fully acknowledges reality.

### [[00:07:54]](https://youtu.be/yPvef9R3k-M?t=474) Bounded Contexts and the Language of Services

Understanding messages between services requires context — this is just how language works. Evans builds up the concept of bounded contexts through a running example with services A through F:
- **Within a bounded context**, words have precise, agreed-upon meanings
- **Between contexts**, translation is necessary
- A service's messages are in that service's "language"
- Understanding requires knowing which language you're receiving

### [[00:10:32]](https://youtu.be/yPvef9R3k-M?t=632) Context Map Patterns: Partnership, Conformist, Anti-Corruption Layer

Evans walks through relationship patterns using his A-F service example:
- **Partnership (A-B):** Two teams actively collaborate; both invest in maintaining a shared translation. Symmetrical relationship.
- **Conformist (C to A):** C adopts A's language wholesale to make consumption easy. Cheap but risky — if A's design degrades, C inherits the mess.
- **Anti-corruption layer (D to A):** D builds a translation wall, transforming A's messages into D's own language. More work but protects model integrity. Like a car engine's air filter — high-precision parts need protection from a dirty environment.
- **Upstream conformist (E to A):** E provides data to A but in A's language, not its own. The arrow on the context map points toward power (A), not data flow direction.

### [[00:19:23]](https://youtu.be/yPvef9R3k-M?t=1163) When Contexts Go Wrong — Corruption Propagation

When F makes poor design choices, C (which conformed to F) immediately inherits the mess: "If I conform to a mess, then what does that make me?" When E fails to maintain quality conformance to A, both A and D risk corruption. The ideal world pushes E to fix things; the real world requires A and D to introduce anti-corruption layers as protection. **The context map must reflect reality, not aspirations** — if E isn't actually conforming, update the map.

### [[00:22:49]](https://youtu.be/yPvef9R3k-M?t=1369) Not All of a Large System Will Be Well-Designed

Evans considers this the most important mindset for anyone who cares about good design: "Say it three times to yourself in the mirror every morning." Without this acceptance, you'll overreach — trying to fix everything and fixing nothing, spreading work too thin. The question isn't "how do we make everything good?" but "given that some parts will be messy, how do we protect the parts that need precision?"

### [[00:25:43]](https://youtu.be/yPvef9R3k-M?t=1543) The Interchange Context

When one service's language becomes the de facto communication standard across many services, consider extracting a dedicated **interchange context** — a language designed specifically for inter-service communication rather than internal logic. This context has no physical form (no service backs it); it's purely a shared vocabulary. Evans advises letting this need emerge rather than planning it upfront: "I like to kind of let the need for it come upon us."

### [[00:29:16]](https://youtu.be/yPvef9R3k-M?t=1756) Why Physical Boundaries Beat Logical Ones

Critics argue that bounded contexts are "just logical boundaries" that don't need microservice machinery. Evans concedes they're right in principle but counters with decades of evidence: "We've been trying to do that for decades now... it's just too subtle. It doesn't survive the rough and tumble." Microservices make it **unnatural** to violate boundaries — "Sometimes you need a wall." His first client experiment with this approach produced decoupling that logical boundaries never achieved, even though the client didn't need the scaling benefits.

### [[00:37:30]](https://youtu.be/yPvef9R3k-M?t=2250) Q&A Highlights

- **Teams and contexts:** One team can own multiple contexts, but one context should never have multiple owners — that leads to "tragedy of the commons."
- **DRY across boundaries:** Evans would rather see duplication than a dependency on another team: "If you've created a dependency on a whole other team and their success just to have this function they've already built, maybe it's better to do some duplicating."
- **Monolith first?** Evans leans toward starting broken up but acknowledges others have had good results with monolith-first. He doesn't hold a strong opinion.
- **Nano-services warning:** When services shrink to 20 lines of code, "Boy, that sounds like an object" — the same problems that plagued fine-grained object systems will recur.

## Books, Tools & Resources Mentioned

- **Domain-Driven Design** (2003) — Eric Evans (the foundational text introducing bounded contexts, ubiquitous language, context maps)
- **Big Ball of Mud** paper (1997) — Brian Foote & Joseph Yoder (describes systems that grow into tangled messes, with an admiringly pragmatic tone)
- **Netflix microservices architecture** — cited as the original inspiration
- **Simian Army / Chaos Monkey** — Netflix's resilience testing tools, cited for their "boldness"
- **Context mapping** — DDD technique for visualizing relationships between bounded contexts

---

*Source: [DDD & Microservices: At Last, Some Boundaries! — Eric Evans](https://www.youtube.com/watch?v=yPvef9R3k-M)*

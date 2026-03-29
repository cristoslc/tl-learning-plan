---
podcast_url: https://www.youtube.com/watch?v=OJEZmb6Fw8w
transcript_url:
updated: 2026-03-28
---

# Vaughn Vernon on Strategic Monoliths and Microservices — SE Radio Episode 495

- **Guest:** Vaughn Vernon, entrepreneur, developer, and software architect; leading expert on Domain-Driven Design, reactive programming, and event-driven architecture
- **Hosts:** Akshay Manchale
- **Podcast:** Software Engineering Radio
- **Published:** January 19, 2022

## Key Takeaways

The fundamental problem in modern software organisations is not a technical one — it is the broken relationship between business and technology. Purposeful architecture emerges from fixing that relationship first, then letting architectural decisions follow from clear domain understanding rather than from tool enthusiasm.

> 1. **Monolith vs. microservices is a false binary.** Most companies should default to a well-modularised monolith; the decision to extract microservices should be driven by rate of change within a bounded context, not by hype.
> 2. **Bounded contexts, not line counts, define a microservice.** A microservice is the right size when it fully expresses the ubiquitous language of one bounded context — 100, 1,000 or 10,000 lines are all fine.
> 3. **Start with a modularised monolith even when you plan microservices.** Eliminating the network during early development lets you validate the domain model cheaply. Extract services later, once clean seams are proven.
> 4. **Conway's Law is a design force, not just an observation.** Teams must communicate well for their architecture to be good; reorganise teams to improve communication before expecting architectural improvement.
> 5. **DRY is about knowledge, not code.** Duplicating data attributes across bounded contexts is acceptable; duplicating business rules (knowledge) is the violation to avoid.
> 6. **Resistance to change is the silent killer.** Architects who protect their fiefdoms when modernisation is needed put their organisations — and ultimately their own careers — at greater risk than the change itself.
> 7. **Technology choices should follow domain understanding, not precede it.** Introduce Kubernetes, Kafka, or NoSQL only after you know they solve a specific, proven need; default to the simplest thing that works (e.g. Postgres at 10,000 TPS covers 95 % of projects).
> 8. **Innovators, not inventors.** Software developers are well suited to improving existing capabilities rather than inventing from nothing — engaging deeply with business problems is how that potential is unlocked.

## Guest Background

Vaughn Vernon is an entrepreneur, developer, and software architect with more than 35 years of experience. He is a leading international authority on Domain-Driven Design (DDD), reactive programming, and event-driven architecture, and consults and trains organisations worldwide. He is the author of several books in the DDD space, including *Implementing Domain-Driven Design* and, most recently, *Strategic Monoliths and Microservices: Driving Innovation Using Purposeful Architecture* (co-authored with Tomasz Jaskula). He previously appeared on SE Radio in Episode 49 to discuss reactive programming with the actor model.

## Core Thesis

The monolith-vs-microservices debate is a distraction from the real challenge: building software that genuinely serves business strategy. Vernon argues that most architectural problems are downstream of a communication failure — between business and technology, between teams, and within teams themselves. His prescription is to ground every architectural decision in Domain-Driven Design's bounded context concept, begin with a well-modularised monolith to keep options open, and only promote bounded contexts to network-deployed microservices when the rate of change or team-autonomy economics justify the additional complexity.

## Major Topics Discussed

### [[00:01:13]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=73) Motivation and the Business–Technology Gap

Vernon opens by describing a pattern he has observed across decades of consulting: the teams that deliver the most value are those where engineering and executive leadership actively collaborate. In contrast, many engineering teams have developed a "survival instinct" of avoiding business engagement — paradoxically even in DDD workshops where Vernon himself plays the domain expert and offers to answer questions. Meanwhile, business leaders grow frustrated with technologists who use jargon and condescend rather than find common ground.

- The book is deliberately addressed to **both** C-level executives and individual engineers simultaneously, a structural choice Vernon calls unique.
- The gap is not malice on either side; it is a learned behaviour that festers when neither side knows how to bridge the divide.

### [[00:07:39]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=459) Mud Systems and Barriers to Change

Vernon introduces the term "mud system" (big ball of mud) — the state a system reaches after years of expedient changes, where any original purposeful architecture has dissolved into tangled coupling. Two organisational barriers compound this:

- **Fiefdom resistance:** Senior architects and chief architects protect their domains because acknowledging problems feels like admitting failure, even though resisting change is itself the career-threatening path.
- **Unrealistic timelines:** Once an organisation accepts it must change, leadership often expects transformation in months, ignoring that decades of accumulation cannot be reversed quickly.

### [[00:10:53]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=653) Are Monoliths Bad? Are Microservices Good?

Vernon rehabilitates the word "monolith." The bad reputation comes from conflating monolith with *big ball of mud monolith* — an architecture that decayed, not one that was wrong from the start. His positions:

- **Monoliths are not inherently bad.** Most companies would be better served by a well-designed monolith than by microservices.
- **Microservices are not inherently good.** Introducing the network adds failure surfaces (partitions, indeterminism) and reduces raw performance. It is only worth paying that cost when the benefits (independent deployment, isolated scalability) are genuinely needed.
- **Size metrics are meaningless.** The "100-line microservice" rule and its variants are language-dependent and arbitrary. The right size is determined by the ubiquitous language of the bounded context, not a line count.
- **Tool ≠ solution:** Kafka, Kubernetes, and microservices are tools. Introducing them does not solve systemic communication or design problems; it often amplifies them.

### [[00:18:13]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=1093) Conway's Law and Team Communication

Conway's Law: any system a team builds will reflect that team's communication structure. Vernon dismisses the naive reading ("three teams → three subsystems") and focuses on the actionable insight:

- Teams must communicate well *first* for system design to be good. You cannot engineer good architecture around poor collaboration.
- Conway himself prescribed **reorganising teams** to improve communication when a design is not working — a prescription Vernon notes is essentially what modern "inverse Conway maneuver" advocates rediscovered fifty years later.
- DDD is fundamentally about communication and rapid learning, which is why Conway's Law and DDD are natural allies.

### [[00:22:05]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=1325) Bounded Contexts and the Sphere of Knowledge

A bounded context is a **sphere of knowledge**: a linguistic and conceptual boundary within which a team's ubiquitous language has precise, agreed-upon meaning.

- The word "policy" means something different in an insurance underwriting context than in a claims context, even though both use the same term and share some data fields. DDD says: don't force global agreement — bound each meaning in its own context.
- The **fence-and-yard metaphor:** neighbours all have grass, but the grass means something different in each yard (playground vs. manicured lawn). The context defines the meaning, not the surface similarity.
- In large legacy enterprises, business capabilities often span multiple legacy systems. You can still reason about them as a single logical bounded context — doing so may reveal an integration service worth building.

### [[00:30:43]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=1843) Building Monoliths Correctly (Greenfield)

Vernon's recommended approach for new software:

1. **Default to a modularised monolith.** Use separate in-process modules for each bounded context, with as much logical separation as if they were deployed independently — but without introducing the network.
2. **Treat inter-context communication as if it crossed a service boundary.** Use lightweight messaging or REST-style interfaces *within process* (method calls with loose coupling, possibly multithreaded) to prevent cross-context coupling from hardening.
3. **Resist early infrastructure decisions.** Use in-memory databases initially; introduce NoSQL, CQRS, or event sourcing only once the domain model is validated and the need is proven.
4. **Rationale:** Getting the domain model right is much cheaper without network complexity. The seams you create now become the extraction points for microservices later if you need them.

### [[00:39:54]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=2394) Migrating Existing Monoliths and Legacy Systems

For entangled legacy systems ("big ball of mud"):

- **Well-modularised monolith:** Extracting a bounded context into a microservice is "pretty straightforward" — you already have the ports-and-adapters seams; you just swap the technology beneath the adapter from in-process calls to network calls.
- **Tangled legacy (Java, .NET, Ruby on Rails):** Identify cohesive classes, write unit tests first, then consolidate related objects into candidate modules incrementally. Opportunistically clean areas whenever a bug fix or feature change brings you into that code.
- **True legacy (COBOL on mainframes):** Full replacement is usually required, but first **mine the business rules**. One client found 75–80 % of business rules dating from the mid-1970s were completely obsolete — migrating them would have been wasted effort.

### [[00:45:11]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=2711) Greenfield Microservices and the Right Granularity

When microservices are the deliberate starting point:

- Use bounded contexts as the decomposition unit, not technical tiers or entity types.
- **Danger zone:** Separate microservices for "create entity" and "update entity" of the same type is too granular; it destroys cohesion and multiplies deployment complexity with no architectural benefit.
- If a part of a bounded context changes faster than the rest, it may make sense to deploy that aggregate separately — but it stays **logically** within the same bounded context and team sphere of knowledge.
- Chapter 11 of the book maps the specific path from well-modularised monolith to microservices deployment.

### [[00:49:07]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=2947) DRY, Siloing, and Context Mapping

DRY (Don't Repeat Yourself) is about **knowledge**, not code:

- Duplicating a `policyId` attribute across bounded contexts is fine — it is data, not knowledge.
- Duplicating business rules (how to calculate risk, how to price a premium) across contexts violates DRY and causes dangerous knowledge drift.
- **Separate Ways** (a DDD context-mapping pattern): sometimes the integration cost exceeds the benefit; consciously going separate ways is legitimate, provided the team does not inadvertently silo *knowledge*.

### [[00:54:46]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=3286) Technology Choices and Language Diversity

When to make technology stack decisions and how heterogeneous to go:

- Defer stack decisions until the domain model is proven; use the simplest possible infrastructure first.
- Language diversity in microservices is a cultural and risk decision, not a technical one. For a 70-person startup, five or six different languages across services creates unsustainable key-person dependency risk.
- **Use the right tool for the job** — Python for machine learning is justified by its ecosystem even though it is a costly runtime. But justify it rationally, not by fashion.
- Bus-factor risk is the practical constraint: ensure enough engineers are fluent in each language in use.

### [[00:57:53]](https://www.youtube.com/watch?v=OJEZmb6Fw8w?t=3473) Closing Advice: Shift to Innovation

Vernon's parting message for engineers at all levels:

> *"Just completely shift gears to innovation — software as a strategy, software for delivering innovation. When your mind shifts to that, and you're having fun solving difficult business problems, then you don't need Kubernetes … to be that feather in your cap, because you're just having too much fun doing heavy lifting for the business."*

The architecture that fits will emerge naturally from that orientation. Vernon distinguishes **inventor** (creates something from nothing) from **innovator** (takes what exists and makes it much better) — and argues most software developers are well-positioned to be exceptional innovators when engaged with real business challenges.

## Books, Tools & Resources Mentioned

- **Strategic Monoliths and Microservices: Driving Innovation Using Purposeful Architecture** — Vaughn Vernon & Tomasz Jaskula (Addison-Wesley, 2022); the primary subject of the episode
- **Implementing Domain-Driven Design** — Vaughn Vernon (earlier book, referenced contextually)
- **Domain-Driven Design** — Eric Evans (implied throughout as foundational DDD text)
- **Event Storming** — collaborative modelling technique for mapping domains across subsystems (mentioned as a starting point for bounded-context discovery)
- **Conway's Law** — Mel Conway's 1968 paper on how organisational communication structure shapes system design
- **Ports and Adapters / Hexagonal Architecture** — referenced as the enabling pattern for clean monolith-to-microservice extraction
- **CQRS (Command Query Responsibility Segregation)** — mentioned as a pattern to evaluate only after simpler query approaches prove insufficient
- **Kafka, Kubernetes, PostgreSQL** — named as examples of tools to introduce only when the specific need is demonstrated; Postgres at 10,000 TPS cited as sufficient for ~95 % of projects
- **SE Radio Episode 49** — Vaughn Vernon's earlier appearance on the podcast discussing reactive programming with the actor model

---

*Source: [Episode 495: Vaughn Vernon on Strategic Monoliths and Microservices](https://www.youtube.com/watch?v=OJEZmb6Fw8w)*

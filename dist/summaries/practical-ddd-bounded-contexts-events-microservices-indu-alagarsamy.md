---
podcast_url: https://www.youtube.com/watch?v=Ab5-ebHja3o
transcript_url:
updated: 2026-03-28
---

# Practical DDD: Bounded Contexts + Events => Microservices — Indu Alagarsamy

- **Speaker:** Indu Alagarsamy, Solution Architect at Particular Software (NServiceBus)
- **Event:** QCon
- **Format:** Conference talk
- **Duration:** ~51 minutes

## Key Takeaways

Domain-Driven Design's bounded contexts give you clarity and freedom in modeling; event-driven architecture gives you the communication mechanism between those contexts. Together, they naturally produce autonomous microservices.

> 1. **Unified models are the enemy of clarity** — "Product" means different things to sales (marketable thing), inventory (thing you have or don't), and shipping (thing that goes in a box). One model to rule them all creates contradictions, bloated schemas, and lost domain language.
> 2. **Bounded contexts are safe spaces for models** — inside a context, models can evolve freely using the domain's natural language. Outside, other teams are completely independent.
> 3. **Use events between contexts, commands within them** — events convey "something significant happened" (published to many). Commands convey intent (sent to one) and can fail. Between bounded contexts, communication should be through events to maintain autonomy.
> 4. **Naming matters more than you think** — "PDF document was generated" is a technical artifact; "certified mail was sent" is a domain event. "Rebook flight" vs. "rebooking was proposed" — listen to the domain experts' language and refactor your code to match.
> 5. **Temporal coupling is the autonomy killer** — if your booking context must call the loyalty context synchronously to make a decision, you're stuck when loyalty is down. Instead, subscribe to loyalty events and cache the status locally. Ask domain experts how much staleness is acceptable.
> 6. **EventStorming surfaces the real behavior** — sticky notes are cheap; code is expensive. Putting domain experts and developers in the same room to map events on a timeline catches misunderstandings before they become bugs.

## Speaker Background

Indu Alagarsamy is a Solution Architect at Particular Software, the makers of NServiceBus (a .NET messaging platform for event-driven architecture). Her journey into architecture started in 2010 when she worked at a company sending regulatory mortgage notices during the real estate crisis — the software couldn't handle the load, which led her to event-driven architecture and DDD. She speaks from hands-on experience building systems where messaging and bounded contexts solve real scaling and reliability problems.

## Core Thesis

The intersection of DDD (as a modeling discipline) and event-driven architecture (as a technology) naturally produces microservices that are autonomous, reliable, and scalable. The key is: use bounded contexts to keep models clean and domain-aligned, use events to communicate between contexts without temporal coupling, and continuously refactor your models and naming to match what domain experts actually say.

## Major Topics Discussed

### [[00:02:51]](https://youtu.be/Ab5-ebHja3o?t=171) The "Product" Problem — Why Unified Models Fail

Using an e-commerce example: "product" in the sales context means a marketable item with descriptions and images. In inventory, it's something you have or don't. In shipping, it's something with physical dimensions and weight. A unified model with one "weight" field creates contradictions (display weight vs. shipping weight) and loses the natural language each team uses. Composite field names like "display_weight" and "shipping_weight" just bloat the model and introduce translations nobody uses in conversation.

### [[00:07:02]](https://youtu.be/Ab5-ebHja3o?t=422) Bounded Contexts as Safe Spaces

A bounded context gives a team a space where models can evolve freely using the domain's natural language. Each context has its own "product" with its own "weight" — no contradiction, no duplication. Teams inside one context are completely independent of models in other contexts. Finding context boundaries: ask whether two fields ever need transactional consistency together (if not, different context), look at natural team/department boundaries, and refine through ongoing conversations with domain experts.

### [[00:15:02]](https://youtu.be/Ab5-ebHja3o?t=902) Events vs. Commands

Two types of messages for inter-context communication:
- **Events** — "something significant happened in the business." Published to multiple subscribers. Past tense. Can't fail (it already happened).
- **Commands** — convey intent, sent to one specific service. Can fail (the Sparta/Xerxes analogy: "bend your knee" didn't go so well).

Use events between bounded contexts; use commands within a context for internal orchestration.

### [[00:24:15]](https://youtu.be/Ab5-ebHja3o?t=1455) EventStorming in Practice

A collaborative technique from Alberto Brandolini: put events on a timeline on a wall with domain experts. Then add commands (what triggers each event), then identify failure modes (what if the command fails?). The key conversation: business people discovering that the software behaves differently from what they expect — "well, it shouldn't behave like that!" These conversations are gold; having them over sticky notes is infinitely cheaper than discovering them in code.

### [[00:21:50]](https://youtu.be/Ab5-ebHja3o?t=1310) The Saga Pattern for Long-Running Processes

When multiple messages participate in one business process (rebooking involves checking, proposing, waiting for customer response, cancellation grace period), you need state management across messages. The saga pattern: process one message, store state, when next message arrives, rehydrate state and decide next action. Enables compensating actions when things don't go as planned. "Friends don't let friends do distributed transactions."

### [[00:31:32]](https://youtu.be/Ab5-ebHja3o?t=1892) Naming as Domain Alignment

Stop naming handlers after events (AircraftTypeWasChangedHandler) — call them what they do (ProposeNewRebooking). Stop using CRUD verbs for events — "customer was deleted" makes no domain sense; "customer was deactivated" does. The requirement said "new booking proposal" but the code said "rebook flight" — refactor to match the domain language. This obsession with language is what makes DDD code readable, communicable, and maintainable.

### [[00:38:38]](https://youtu.be/Ab5-ebHja3o?t=2318) Eliminating Temporal Coupling with Events

Scenario: booking context needs loyalty status to decide who gets rebooking notifications. Synchronous call to loyalty service = temporal coupling (if loyalty is down, booking is stuck). Solution: loyalty publishes "customer promoted to gold" events; booking subscribes and stores status locally. Now booking can make decisions independently. Staleness question: "Is it okay if the status is a day old?" — ask the domain expert, not the programmer.

### [[00:43:10]](https://youtu.be/Ab5-ebHja3o?t=2590) Deployment and Reliability Patterns

With event-driven design, deployments become safer: bring up v1.1 alongside v1.0, let messages flow to both, evaluate, then stop the old version. Failed messages go to an error queue (poison messages), not lost forever — debug, fix, replay. Monitoring becomes critical: queue length, message processing time, SLA compliance. "One good thing about a monolith is you know immediately when things fail."

## Books, Tools & Resources Mentioned

- **Domain-Driven Design** — Eric Evans ("the blue book"; start with Part 4: Strategic Design)
- **NServiceBus** — .NET messaging platform from Particular Software
- **EventStorming** — Alberto Brandolini's collaborative modeling technique
- **"All models are wrong, but some are useful"** — George Box (cited for the iterative nature of modeling)
- **DDD: The First 15 Years** — free ebook on leanpub.com/ddd15first15years
- **Explore DDD** (Denver) and **DDD Europe** (Amsterdam) — recommended conferences
- **Udi Dahan's Advanced Distributed Design course** — referenced for deeper boundary-finding techniques

---

*Source: [Practical DDD: Bounded Contexts + Events => Microservices — Indu Alagarsamy (QCon)](https://www.youtube.com/watch?v=Ab5-ebHja3o)*

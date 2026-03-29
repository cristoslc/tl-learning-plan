---
podcast_url: https://www.youtube.com/watch?v=PzEox3szeRc
transcript_url: https://www.youtube.com/watch?v=PzEox3szeRc
updated: 2026-03-27
---

# "Good Enough" Architecture — Stefan Tilkov — GOTO 2019

- **Speaker:** Stefan Tilkov, Co-founder & Principal Consultant at INNOQ
- **Event:** GOTO Conference 2019
- **Published:** 2019

## Key Takeaways

There is no universally "good" architecture — only architectures that are good enough for a specific context. The best architects balance simplicity with evolvability, enforce a small number of strict rules while granting teams maximum autonomy, and continuously manage system evolution rather than treating architecture as a one-time upfront activity.

> - Architecture quality can only be assessed relative to the quality attributes you actually care about (performance, security, maintainability, etc.)
> - Trying to design a one-size-fits-all customizable solution satisfies no one — build specific solutions for specific needs
> - Microservices are not inherently good; splitting too fine leads to cross-team dependency nightmares and the "entity service" anti-pattern
> - Autonomous teams need strict macro-architecture rules to stay loosely coupled — loose coupling requires strict enforcement
> - Successful systems are most at risk of architectural rot because nobody invests in architecture while things are working
> - Smart endpoints, dumb pipes: never put business logic in infrastructure or integration middleware
> - Architecture must evolve continuously — YAGNI doesn't mean "never think ahead," it means make conscious trade-off decisions

## Speaker Background

Stefan Tilkov is co-founder of INNOQ, a technology consultancy specializing in software architecture. He draws on decades of consulting experience reviewing and improving architectures at companies ranging from e-commerce platforms and insurance firms to banks and financial service providers. He's known for his pragmatic, anti-dogmatic stance on architecture.

## Core Thesis

### [[00:00:15]](https://youtu.be/PzEox3szeRc?t=15) The Problem with "Good" Architecture

Architecture is "whatever hurts if you get it wrong" (Grady Booch). There is no good architecture in the abstract — only architecture that fits your specific quality attributes, scale requirements, and organizational context. Asking "what's a good architecture?" is like asking "what's a good car?" without knowing whether you need a race car or a minivan.

## Major Topics Discussed

### [[00:01:06]](https://youtu.be/PzEox3szeRc?t=66) Defining Architecture

Tilkov walks through definitions from ISO standards (elements, relationships, design principles) to Grady Booch's pragmatic version ("whatever hurts if you get it wrong"). The real-world definition: architecture is whatever the people in charge consider important enough to merit their attention — which means important things often get overlooked while trivial details get over-specified. Architecture is a **property of the system**, not a document. Every system has one, whether intentional or accidental.

### [[00:06:01]](https://youtu.be/PzEox3szeRc?t=361) Scaling Dimensions: Logic vs. Load

A key framework: systems vary along two axes — **business logic complexity** (from a simple CMS to German tax law) and **load** (from a dozen users to half the planet). Twitter is high-load but relatively simple logic; Amazon is both high-load and high-complexity; insurance systems are high-complexity but low-load. Your architecture must match where you sit on these axes.

### [[00:07:44]](https://youtu.be/PzEox3szeRc?t=464) Anti-Pattern 1: Non-Extensible Extensibility

A global e-commerce platform tried to serve all customers (from long-tail small shops to strategic enterprise clients) with a single ultra-configurable solution, complete with its own Eclipse-based IDE. **Result:** too complex for small customers, too limited for large ones — satisfying nobody. **Fix:** build specific solutions for specific customer segments. The large clients pay enough to justify custom development; the small clients need something dead simple.

### [[00:11:02]](https://youtu.be/PzEox3szeRc?t=662) Anti-Pattern 2: Perilously Fine-Grained Services

A large multinational split a system into ~40 microservices for 30 developers (roughly one service per person). When the team grew to 300+, services overlapped across team boundaries, creating constant ownership conflicts. The **entity service anti-pattern** emerged — an "order service" that every other service depended on, becoming a bottleneck containing concerns from fulfillment, support, billing, and more. **Fix:** reorganize services around team boundaries, giving each team ownership of the entities relevant to their domain. Refactoring within team boundaries became easy again.

- **[[00:14:10]](https://youtu.be/PzEox3szeRc?t=850) The Netflix trap** — Almost nobody is Netflix, yet almost everybody copies their architecture. Unless you're building a scalable video platform for hundreds of millions of users in 150 countries, their architecture is probably wrong for you.

### [[00:20:34]](https://youtu.be/PzEox3szeRc?t=1234) Anti-Pattern 3: Freestyle Architecture (No Rules)

A large European online retailer with 120 developers adopted self-contained autonomous teams — a fundamentally sound approach. But they **exaggerated autonomy** by refusing to standardize anything: ad-hoc UI integration (poor performance), wildly different API styles (collection+JSON, HAL, Siren simultaneously), and a centralized front-end team that became a bottleneck. Avoiding the word "architecture" didn't prevent an architecture from forming — it just meant they got one they didn't want.

- **[[00:26:40]](https://youtu.be/PzEox3szeRc?t=1600) Diversity vs. Chaos** — There's a fine line between valuable diversity (teams picking best-of-breed tools) and pointless chaos (incompatible API formats for no reason).
- **[[00:27:19]](https://youtu.be/PzEox3szeRc?t=1639) Strict rules enable loose coupling** — Paradoxically, the looser the coupling you want, the stricter your macro-architecture rules must be: no direct DB connections across boundaries, no shared libraries, standardized communication patterns. Few rules, but strictly enforced.

### [[00:28:39]](https://youtu.be/PzEox3szeRc?t=1719) Anti-Pattern 4: Cancer as Growth

A successful financial services company grew organically over 20+ years: Oracle Forms to Java/JavaScript web app (business logic still in Oracle DB), then added C# web services, then acquired a company and **copied the entire system** rather than migrating, merging data models into a superset. They accumulated 8+ databases, and — the crown jewel — a **custom C++ encryption implementation** (of a standard algorithm) that contained a bug. By the time they discovered the bug, they'd encrypted too much data to switch, so they're permanently stuck with broken encryption running in a Borland C++ Windows VM.

- **[[00:32:42]](https://youtu.be/PzEox3szeRc?t=1962)** Successful systems often end up with the worst architecture because nobody invests in it while things are working. Start managing evolution before the burning platform moment.

### [[00:33:46]](https://youtu.be/PzEox3szeRc?t=2026) Positive Example: Smart Endpoints, Dumb Pipes

A bank replaced a bloated proprietary message broker (with its own IDE, XML mapping, and business logic in configuration) with a **simple pub/sub messaging solution** plus small **adapter programs** deployed as Docker containers near each system. Instead of configuring a magic platform, developers wrote actual programs (~10 minutes vs. 3 hours in the GUI). Used the strangler pattern to gradually migrate. Blueprint architectures showed teams *how* to build adapters without mandating a single tool for everyone.

### [[00:39:10]](https://youtu.be/PzEox3szeRc?t=2350) Final Takeaways

- **Don't be afraid of architecture** — pragmatic, lightweight governance is not the same as ivory-tower bureaucracy
- **Choose the simplest thing that works** — but also design for evolvability, because your architecture *will* need to change
- **Manage evolution continuously** — architecture done upfront will suck; that's fine, as long as you keep improving it
- **YAGNI ≠ "never think ahead"** — make conscious trade-offs between building for today vs. investing in tomorrow
- **Add value, remove roadblocks** — if you're an architect, enable teams rather than imposing personal preferences

## Books, Tools & Resources Mentioned

- **ISO 42010** — International standard for architecture description
- **Grady Booch** — "Architecture is whatever hurts if you get it wrong"
- **Netflix architecture** — cited as commonly (and inappropriately) copied
- **Self-Contained Systems (SCS)** — architectural pattern for team autonomy
- **Apache Camel** — integration framework used in the bank adapter example
- **Docker Swarm** — used for adapter deployment in the positive example
- **Strangler Pattern** — incremental migration strategy for replacing legacy systems
- **Rational Rose** — legacy CASE tool, referenced as cautionary example
- **Oracle Forms** — legacy 4GL tool

---

*Source: ["Good Enough" Architecture — Stefan Tilkov — GOTO 2019](https://www.youtube.com/watch?v=PzEox3szeRc)*

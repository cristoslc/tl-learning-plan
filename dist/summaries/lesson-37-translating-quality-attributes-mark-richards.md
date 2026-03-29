---
podcast_url: https://developertoarchitect.com/lessons/lesson37.html
transcript_url: https://www.youtube.com/watch?v=oP9Q9dpTomA
updated: 2026-03-27
---

# Lesson 37: Translating Quality Attributes to Business Concerns — Mark Richards

- **Guest:** Mark Richards, Hands-on Software Architect and Founder of developertoarchitect.com
- **Host:** Mark Richards (solo lesson)
- **Series:** Software Architecture Monday
- **Published:** October 15, 2018

## Key Takeaways

A single architectural "-ility" does not achieve a business goal — only a **cluster of complementary quality attributes together** satisfies a business concern. Architects must learn to present these clusters in the language of business stakeholders, not in technical jargon.

> - Individual quality attributes (agility, testability, deployability) **cannot be mapped one-to-one** to business outcomes — context collapses the value.
> - **Time-to-market** is achieved by the combination of agility + testability + deployability, not by any one alone.
> - **User satisfaction** is supported by performance + availability + fault tolerance + testability + deployability + agility working together.
> - **Mergers and acquisitions readiness** maps to agility + scalability + learnability + interoperability + adaptability.
> - **Competitive advantage** requires agility + testability + deployability + scalability + availability + fault tolerance + adaptability.
> - The architect's job is to **translate bidirectionally**: from business concern to "-ilities" when designing, and from "-ilities" back to business language when communicating.
> - **Learnability** is an underappreciated "-ility" that encompasses both simplicity of design and quality of documentation — essential for M&A scenarios.

## Guest Background

Mark Richards is a practising, hands-on software architect based in Boston. He is the founder of [developertoarchitect.com](https://developertoarchitect.com) and has spent decades designing and implementing large-scale distributed systems. He is best known as co-author of *Fundamentals of Software Architecture* (with Neal Ford, O'Reilly) and as the creator of the Software Architecture Monday video series. He regularly teaches multi-day software architecture training courses and speaks at conferences and user groups worldwide. This lesson originated from a question raised by a student (credited as "May N.") during one of his three-day architecture training classes.

## Core Thesis

There is a persistent **translation gap** between the language architects use (non-functional quality attributes, or "-ilities") and the language business stakeholders use (time-to-market, user satisfaction, competitive advantage, mergers and acquisitions). Bridging this gap is not just a communication nicety — it is essential for building architectures that actually serve business goals. The critical insight Richards delivers is that the mapping is **not one-to-one**: no single "-ility" can be meaningfully equated to a business concern. Business outcomes emerge only when the right *combination* of quality attributes is identified, prioritised, and communicated as a coherent cluster.

## Major Topics Discussed

### [[00:00:00]](https://www.youtube.com/watch?v=oP9Q9dpTomA?t=0) Introduction — The Lost-in-Translation Problem

Richards opens by framing the central challenge: architects speak fluently about fault tolerance, testability, and deployability, while business stakeholders speak about user satisfaction, time-to-market, and competitive advantage. When these two vocabularies collide without a translation layer, architectural decisions become disconnected from business goals. The lesson was prompted by a student's question in a recent three-day training.

### [[00:02:26]](https://www.youtube.com/watch?v=oP9Q9dpTomA?t=146) Mapping Business Concern #1: Time-to-Market

- **Business language:** "We need faster time-to-market."
- **Architectural translation:**
  - **Agility** — the ability to respond quickly to change.
  - **Testability** — both the *ease* of testing and the *completeness* of test coverage; poor testability means bugs slow down releases.
  - **Deployability** — not just ease of deployment but *frequency* of deployment and *risk reduction* per deployment. High deployability = deploying daily or hourly with low ceremony and low breakage risk.
- Together, these three "-ilities" form the architectural foundation for time-to-market. Richards emphasises that architects can present this cluster back to a business stakeholder as: *"We are supporting faster time-to-market through these three architectural characteristics."*

### [[00:03:30]](https://www.youtube.com/watch?v=oP9Q9dpTomA?t=210) Mapping Business Concern #2: User Satisfaction

- **Business language:** "We need better user satisfaction."
- **Architectural translation:**
  - **Performance** — faster applications produce happier users, internal and external.
  - **Availability** — frequent downtime directly causes user frustration.
  - **Fault tolerance** — when failures occur, only portions of the system fail so some users remain operational.
  - **Testability** — reduces bugs that users encounter.
  - **Deployability** — enables faster delivery of fixes and features users need.
  - **Agility** — the ability to respond quickly to user-reported bugs and new feature requests.
- Richards notes that performance alone can boost satisfaction somewhat, but only the full cluster reliably delivers high user satisfaction.

### [[00:04:58]](https://www.youtube.com/watch?v=oP9Q9dpTomA?t=298) Mapping Business Concern #3: Mergers and Acquisitions Readiness

- **Business language:** "We must be ready for upcoming mergers and acquisitions."
- **Architectural translation:**
  - **Agility** — ability to absorb rapid change that M&A brings.
  - **Scalability** — growing customer base and data volumes from acquired entities requires systems that can scale.
  - **Learnability** — a less commonly discussed "-ility" that Richards defines as encompassing both *simplicity of design* and *quality of documentation*. New teams inheriting systems after an acquisition need to understand them quickly. Poorly learnable systems become M&A liabilities.
  - **Interoperability** — integrating with acquired company systems requires standards-based interfaces, open APIs, and extensible API layers.
  - **Adaptability** — systems must be able to adapt to the operational and technical context of merged entities.

### [[00:06:18]](https://www.youtube.com/watch?v=oP9Q9dpTomA?t=378) Mapping Business Concern #4: Competitive Advantage

- **Business language:** "We must maintain competitive advantage."
- **Architectural translation:**
  - **Agility** — respond faster than competitors to market changes.
  - **Testability + Deployability** — ship higher quality, more frequently.
  - **Scalability** — more customers as you outcompete; systems must handle growth.
  - **Availability** — systems must be up when customers need them.
  - **Fault tolerance** — partial failures should not become total outages that damage reputation.
  - **Adaptability** — adapt to shifts in market conditions and competitor moves.

### [[00:07:04]](https://www.youtube.com/watch?v=oP9Q9dpTomA?t=424) The Critical Insight — No One-to-One Mapping Exists

Richards attempts the reverse mapping — starting from individual "-ilities" and asking what business concern each maps to — and immediately runs into the core problem: **agility alone does not equal time-to-market**. It maps to all four business concerns simultaneously, which means it maps to none specifically. The same is true of testability, deployability, and every other "-ility".

The lesson learned: **the mapping only works at the cluster level**. Architects who tell business stakeholders "we're supporting agility" have said nothing meaningful. Architects who say "we're supporting agility + testability + deployability to achieve faster time-to-market" have made a concrete, actionable statement.

Richards acknowledges one nuance: a single "-ility" like performance can move the needle on user satisfaction in isolation — but even then, full satisfaction requires the complete cluster.

## Books, Tools & Resources Mentioned

- **developertoarchitect.com** — Richards' website and home of the Software Architecture Monday video series.
- **Software Architecture Monday** (free bi-weekly video series) — the series in which this lesson appears; covers architecture tips, techniques, and patterns.
- No specific books are cited in this lesson; for core reading, Richards' *Fundamentals of Software Architecture* (O'Reilly, with Neal Ford) is the natural companion text for this topic.

---

*Source: [Lesson 37: Translating Quality Attributes to Business Concerns — Mark Richards](https://www.youtube.com/watch?v=oP9Q9dpTomA)*

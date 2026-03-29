---
podcast_url: https://www.youtube.com/watch?v=GBTdnfD6s5Q
transcript_url:
updated: 2026-03-28
---

# When To Use Microservices (And When Not To!) — Sam Newman & Martin Fowler • GOTO 2020

- **Guests:** Sam Newman, Author of *Building Microservices* & *Monolith to Microservices*; Martin Fowler, Chief Scientist at ThoughtWorks
- **Hosts:** GOTO Book Club / GOTO Conferences
- **Series:** GOTO Book Club
- **Published:** 2020

## Key Takeaways

The core message of this talk is disarmingly simple: microservices are a cost you pay in exchange for specific organisational and operational benefits — and you should only pay that cost if you know exactly what you are buying. Default to a monolith; migrate selectively and incrementally.

> 1. Our industry focuses on tech tools instead of outcomes — use microservices only as a deliberate means to a desired end, not because they are fashionable.
> 2. Microservices should not be the default. Start with the simplest deployment topology (a single-process monolith) and only reach for distribution when you have a concrete reason.
> 3. The three most valid reasons to adopt microservices are: (a) zero-downtime independent deployability, (b) isolation of data and processing (e.g. GDPR / PII separation), and (c) enabling organisational autonomy across many teams.
> 4. Avoid the **distributed monolith** anti-pattern by actually deploying services independently from day one — if you bundle them "for convenience" you will never go back.
> 5. As team size grows, coordination overhead increases exponentially; microservices force the information-hiding boundaries that make parallel work sustainable.
> 6. Monolithic module boundaries are easy to violate; promoting a module to a service makes violation painful — useful, but sad that we need that friction.
> 7. Data is the hardest part of any decomposition. Breaking relational schemas means giving up joins, ACID transactions, and referential integrity — be deliberate about this trade-off.
> 8. Organisational change must accompany architectural change. Microservices in a command-and-control culture deliver the pain without the benefit.

## Speaker Background

**Sam Newman** is a consultant and author whose career has centred on distributed systems and continuous delivery. He wrote *Building Microservices* (O'Reilly, 2015) — which originated as a book about architecting for CD and accidentally became the canonical microservices reference — and *Monolith to Microservices* (O'Reilly, 2019), which grew out of a single chapter that expanded to 25,000 words when he attempted to update the first book. His practice gives him deep hands-on exposure across healthcare, financial services, and SaaS organisations.

**Martin Fowler** is Chief Scientist at ThoughtWorks, the most-viewed speaker in GOTO Conferences history, and author or co-author of more than fifteen books including *Refactoring*, *Patterns of Enterprise Application Architecture*, and the influential martinfowler.com blog where the microservices pattern was first formally described. His value in this conversation is the synthesis role: he has observed microservices adoption across hundreds of engagements and is willing to challenge even the arguments he originally championed.

## Core Thesis

Microservices are not a default architecture — they are an **option you purchase** (the James Lewis framing: "microservices buy you options"). Like any option, the purchase price is real and upfront: complexity, operational overhead, the loss of relational database guarantees, and the organisational investment needed to realise the benefits. The question to ask before adopting microservices is not "should we?" but "what outcome are we trying to achieve, and is microservices the most cost-effective path to that outcome?"

## Major Topics Discussed

### [[00:01:16]](https://youtu.be/GBTdnfD6s5Q?t=76) Why a Second Microservices Book?

Sam explains that *Monolith to Microservices* began as a single chapter of the *Building Microservices* second edition, covering how to decompose a monolith. Two months and 25,000 words later, it was clearly its own book. The origin story reflects a broader point: the problem of **decomposition** deserves first-class treatment, not a chapter buried in a broader architectural reference.

### [[00:04:09]](https://youtu.be/GBTdnfD6s5Q?t=249) When Should You Use Microservices?

Martin notes that he has only ever heard Sam complain of people adopting microservices unnecessarily — never the reverse. Sam's answer: use them when you have **a really good reason**, meaning a specific outcome you believe this architecture delivers. He names three top reasons:

- **Zero-downtime independent deployability** — deploy one service without coordinating or redeploying the rest; essential for SaaS businesses that cannot tolerate downtime.
- **Data and processing isolation** — useful for regulatory contexts (GDPR, healthcare PII) where you need auditable separation of which services touch sensitive data.
- **Organisational autonomy** — distribute decision-making and deployment authority across teams, reducing cross-team coordination.

He adds: technology heterogeneity and differential scaling are secondary benefits but rarely justify the cost on their own.

### [[00:06:18]](https://youtu.be/GBTdnfD6s5Q?t=378) The Default Should Be a Monolith

Sam's recommended starting point is a **single-process monolith with good internal module boundaries**. He reframes the landscape: even a monolith talking to a separate database is already a distributed system — the increment from "simple monolith + database" to "a few services" is smaller than the industry's all-or-nothing framing implies. His advice is to try extracting **one service**, experience the operational and design costs, and let the architecture evolve from there rather than building a microservices platform before writing a line of business code.

### [[00:11:00]](https://youtu.be/GBTdnfD6s5Q?t=660) Avoiding the Distributed Monolith

The **distributed monolith** anti-pattern — services that must be deployed in lockstep — is identified as the most common microservices failure mode. Two practices to avoid it:

1. **Actually deploy independently from the start.** Teams that bundle deployments "for convenience" find months later that they cannot disaggregate them; the habit becomes structural.
2. **Track co-change patterns.** Link Jira tickets to commits; if services A, B, and C always change together, consider merging them back or reslicing the boundaries.

The underlying design principle is **information hiding** (Parnas): the smaller the interface a service exposes to the world, the easier it is to change its internals without breaking consumers. The tragedy, both speakers agree, is that most languages and frameworks make it trivially easy to violate module boundaries, which is exactly why a network process boundary — despite its costs — can enforce the discipline that code-level modules cannot.

### [[00:18:02]](https://youtu.be/GBTdnfD6s5Q?t=1082) Organisational Scale as the Real Argument

Fowler finds the "limit blast radius per deployment" argument only moderately convincing — you can achieve frequent safe deployments with a well-disciplined monolith (Flickr and Etsy being the classic examples). The argument he finds **much more compelling** is organisational: coordination overhead grows roughly exponentially with team count. When you have 10–20 teams working on one codebase, the overhead of synchronising a monolith deployment becomes genuinely prohibitive. Microservices force the team-level ownership boundaries that make parallel work sustainable.

### [[00:23:52]](https://youtu.be/GBTdnfD6s5Q?t=1432) Data Decomposition — The Hard Part

Both speakers agree this is the most technically treacherous domain. Key observations:

- **Relational databases communicate intent.** A schema often makes domain relationships clearer than the code does; start here when mapping decomposition candidates.
- **Most teams extract code before data**, which is pragmatic (you get early benefit) but dangerous if the data extraction never follows. Running a new microservice against the old shared database creates a hidden coupling.
- **Separate schemas on one database node** is a legitimate and cost-effective intermediate step; it enforces logical isolation without requiring separate infrastructure.
- Giving up microservices means giving up **joins, ACID transactions, and enforced referential integrity**. Eventual consistency is not a free upgrade — it is a different, harder programming model.
- Sam's *Monolith to Microservices* has its longest chapter on databases precisely because the pattern space is large and under-documented in the industry.

### [[00:31:29]](https://youtu.be/GBTdnfD6s5Q?t=1889) People and Organisational Change

The Jerry Weinberg aphorism applies: *it's always a people problem.* Sam describes two failure modes in large organisations:

- **Nothing changes**: the organisation adopts microservices architecturally but retains centralised command-and-control decision-making. Result: all the cost, none of the benefit.
- **Everything changes overnight**: developers are told on a Monday that they now own production. 5% are energised; 95% start looking for another job.

The antidote is **incremental organisational change in parallel with incremental architectural change** — the same "turn the dial a little" metaphor Sam uses for the technical migration. Governance-through-tooling (e.g., mandating a single internal platform like OpenShift) is a common dysfunctional pattern that preserves the illusion of team autonomy while centralising all meaningful decisions. The honest first step is asking: "What kind of organisation do we want to be, and how much power do we actually want to distribute to teams?"

## Books, Tools & Resources Mentioned

- **Sam Newman — *Monolith to Microservices*** (O'Reilly, 2019) — the primary subject of the interview; the chapter on databases is the longest in the book.
- **Sam Newman — *Building Microservices*** (O'Reilly, 2015; 2nd ed. in progress at time of recording) — the canonical microservices reference that spawned this book.
- **James Lewis** — coined the phrase "microservices buy you options."
- **David Parnas** — information hiding theory; Fred Brooks's eventual acknowledgement that Parnas was right (20th anniversary edition of *The Mythical Man Month*).
- **Praful Todkar** — wrote a piece on martinfowler.com about breaking up a microservice with focus on the data layer.
- **John Allspaw** — release engineering lead at Flickr, then Etsy CTO; discussed the limits of rapid monolith deployments (database migrations still required weekend windows).
- **Jerry Weinberg** — "it's always a people problem."
- **gotopia.tech/bookclub** — full transcript of this interview.

---

*Source: [When To Use Microservices (And When Not To!) • Sam Newman & Martin Fowler • GOTO 2020](https://www.youtube.com/watch?v=GBTdnfD6s5Q)*

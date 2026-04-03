---
podcast_url: https://www.youtube.com/watch?v=vkfzpQ10eI4
transcript_url: https://gist.github.com/cristoslc/e2a8962f7422f1769450186b9e6ef51c
updated: 2026-04-02
---

# Solving the Engineering Strategy Crisis — Will Larson

- **Speaker:** Will Larson, CTO at Carta
- **Event:** QCon SF 2023 (recorded version)
- **Format:** Solo talk (~49 minutes)
- **Published:** October 2023

## Key Takeaways

The engineering strategy crisis is largely self-inflicted: most companies already have an implicit strategy — it just isn't written down. Writing it down is both the fastest and most underrated intervention available to any engineer at any level.

> 1. Engineering strategy is simply an **honest diagnosis** of your situation plus a **practical approach** to address it — not grand vision statements or exciting blog-post ideas.
> 2. **Every company already has an engineering strategy** — it's just rarely written down. Writing it down immediately solves half the crisis.
> 3. Written strategy beats implicit strategy in every dimension: discoverability, updateability, accountability, and onboarding clarity.
> 4. Good strategy requires **explicit trade-offs**. If an approach acknowledges no trade-offs, it isn't a real practical approach.
> 5. Context is everything — what worked at Google is almost certainly impractical at a 150-person startup, and even between similar-sized companies.
> 6. The most powerful property of strategy is that it enables things only achievable through **universal adoption** (consolidated tooling investment, conflict reduction, predictable onboarding).
> 7. To advance strategy **top-down**, write the strategy the CTO wants — not the one you want. Debug their feedback; don't fight it.
> 8. To advance strategy **bottom-up** without mandate, use the "**write five, synthesize**" method: five design docs → one narrow strategy, repeated five times → one broad engineering strategy, no permission required.
> 9. Building buy-in is the hard work, not writing the document. Don't write and hand off; do the buy-in work yourself.
> 10. Frame strategy proposals as **low-risk experiments** ("let's try this for 3 months") to reduce organizational friction.

## Speaker Background

**Will Larson** is the CTO of Carta and a widely-read engineering leadership author and blogger (Irrational Exuberance, lethain.com). Before Carta he led engineering at **Calm** (as CTO), **Stripe** (Foundation Engineering), and **Uber**, among other roles. He is the author of *An Elegant Puzzle: Systems of Engineering Management*, *Staff Engineer*, and *The Engineering Executive's Primer* (published shortly after this talk). He is also the author of *Crafting Engineering Strategy*, which directly extends the ideas in this talk. His writing on engineering management and strategy is widely cited across the industry.

## Core Thesis

The "engineering strategy crisis" — the pervasive feeling that companies lack engineering strategy — is mostly a **documentation problem, not a strategy problem**. Implicit strategy exists everywhere; it just lives in people's heads, in unwritten norms, and in past decisions. The solution is straightforward but unglamorous: write the strategy down. Once documented, strategy becomes improvable. The talk then provides two concrete mechanisms any engineer can use to advance strategy, regardless of whether they have organizational authority to mandate it.

## Major Topics Discussed

### [[00:01:47]](https://youtu.be/vkfzpQ10eI4?t=107) What Engineering Strategy Actually Is

Larson anchors on Richard Rumelt's framework from *Good Strategy, Bad Strategy*: strategy has three components — **diagnosis** (honest assessment of the situation), **guiding policy** (how you'll approach the problem), and **coherent actions** (concrete steps that prove the policy isn't empty words). Larson simplifies this to two for engineering: honest diagnosis + practical approach. He deliberately de-emphasizes "coherent actions" because engineering strategy is primarily about shaping future decisions (how to implement incoming requests) rather than mandating a single current action.

### [[00:06:28]](https://youtu.be/vkfzpQ10eI4?t=388) The Widget & Hammer Company — Illustrating Honest Diagnosis

A hypothetical company running a Python monolith launches a new product as a service and declares a services migration. Two years later, the original product is still in the monolith. Larson uses this to distinguish **dishonest diagnosis** ("we can migrate in 3 months," "we've de-risked the approach") from **honest diagnosis** (acknowledging reality: the migration isn't happening because tooling doesn't exist and no one is willing to slow product velocity to build it). The key insight: nothing is universally true — what is honest for one company is dishonest for another. Senior leaders fail when they import their previous company's diagnosis without checking whether it matches the new reality.

### [[00:10:52]](https://youtu.be/vkfzpQ10eI4?t=652) What Makes an Approach Practical

Practical approaches **acknowledge trade-offs**. Larson's examples of genuinely practical (if unexciting) approaches: "We delay the migration until we have tooling" and "We don't adopt new programming languages because we don't have capacity to support them." Neither of these would make a compelling conference talk — but both work. If an approach contains no trade-off acknowledgment, it isn't real.

### [[00:14:46]](https://youtu.be/vkfzpQ10eI4?t=886) Real-World Strategy Examples: Stripe, Calm, Uber

Three detailed case studies showing strategy working in practice:

- **[[00:14:46]](https://youtu.be/vkfzpQ10eI4?t=886) Stripe — "We run a Ruby monolith."** Diagnosis: Stripe's business involves constant external change (regulators, banks, card networks, thousands of financial institutions). That external change consumes the company's entire risk budget; there's nothing left for technology risk. Approach: reduce technology risk by running a single Ruby monolith, invest heavily in tooling for that stack. Impact: Stripe avoided the microservices detour many peers took (and later reversed), concentrated investment made projects like Sorbet (static typing for Ruby) possible, and almost all innovation budget went to product rather than infrastructure.

- **[[00:18:22]](https://youtu.be/vkfzpQ10eI4?t=1102) Calm — "We're a product engineering company."** Diagnosis (circa early 2020): engineers were arguing constantly about adopting new technologies to learn them; a year into a services migration with nothing of substance migrated; a tiny infra team split across monolith and services. Approach: new technologies adopted only to create valuable product capabilities; everything else written in the Node.js monolith; all exceptions in writing, granted by CTO only. Impact: ended technology conflict debates, consolidated tooling onto a TypeScript monolith, redirected innovation budget to product. A few engineers who wanted technology exploration for its own sake left — Larson frames this as acceptable and expected; good strategy clarifies who belongs, not how to please everyone.

- **[[00:22:59]](https://youtu.be/vkfzpQ10eI4?t=1379) Uber — "We run our own hardware."** Diagnosis (~2014): rapidly expanding geographically into regions with no meaningful cloud presence; operating at tens of thousands of servers (where self-hosting yields 20–30% cost reduction); willing to forgo cloud vendor capabilities in exchange for geographic flexibility. Approach: own hardware in dedicated colo space; no data or compute in the cloud; cloud used only as points of presence. Impact: Uber spun up data centers in China in ~6 months without co-locating US/EU data — something cloud-dependent competitors couldn't do. Trade-off acknowledged: significant "not invented here" cost rebuilding common cloud tooling; Lyft (cloud-heavy) had better developer capabilities in domestic markets but couldn't expand internationally as easily.

### [[00:27:02]](https://youtu.be/vkfzpQ10eI4?t=1622) Why These Strategies Worked — The Power of Universal Adoption

Many of strategy's most valuable properties only emerge through universal adoption. Uber's hardware strategy only enables geographic flexibility if *all* data and compute stay on-prem. Stripe's investment in Ruby tooling only makes Sorbet viable if *almost everything* runs in Ruby. Strategy also concentrates tooling investment, reduces ongoing conflict (rules become clear rather than contested), and makes onboarding dramatically easier for new hires — especially senior hires who arrive with strong priors about technology.

### [[00:30:49]](https://youtu.be/vkfzpQ10eI4?t=1849) Counter-Examples: Strategy Failures

- **Digg v4**: Good diagnosis (legacy PHP/MySQL setup was hard to work in), impractical approach (simultaneously adopting Cassandra + Python + PHP service-oriented architecture). Three-plus years in before it worked — arguably never did, as Digg shut down after launch.
- **Stripe + Java**: Diagnosis not grounded in reality (motivated reasoning; the real problems were system design issues, not Ruby's limitations). Massive effort, minimal accomplishment.
- **Uber dual routing**: Two reasonable routing technologies built on two conflicting diagnoses that were never resolved. Both teams doing reasonable work, unable to find which diagnosis was accurate.

### [[00:33:03]](https://youtu.be/vkfzpQ10eI4?t=1983) Strategy Is Everywhere — Just Not Written Down

Every company Larson has worked at had an engineering strategy. None of them had a *written* one when he joined (Carta, partially, was the exception). The implication: you don't need to create strategy from scratch. You need to write down what already exists. Written strategy is more discoverable, more improvable, easier to update, easier to hold people accountable to, and easier to explain the rationale behind.

### [[00:36:01]](https://youtu.be/vkfzpQ10eI4?t=2161) Advancing Strategy Top-Down — Borrowing CTO Authority

When you can access leadership authority, the method is simple: write a diagnosis, validate with the CTO and key stakeholders; draft approaches, validate again; share as a draft to collect input; rely on the CTO to enforce. The critical insight most people miss: **to borrow the CTO's authority, you must write the strategy the CTO wants, not the one you want.** This requires:
- Debugging feedback rather than fighting it (ask "why" rather than advocate your position)
- Being reliably curious — the CTO will only delegate authority to someone who will faithfully represent all stakeholders
- Being pragmatic rather than dogmatic — strong personal technology preferences disqualify you from representing the organization's perspective
- **Building buy-in as part of the work, not as a hand-off** — writing the document is the easy part; getting alignment is the real work
- Framing as low-risk experiments ("let's try this for 3 months")

### [[00:44:28]](https://youtu.be/vkfzpQ10eI4?t=2668) Advancing Strategy Bottom-Up — Write Five, Synthesize

When top-down authority isn't available (CTO is managing active team conflict, not the right moment, etc.), any engineer can advance strategy through bottom-up documentation. Larson's method: **Write Five, Synthesize**.

1. Write **five design documents** on a given topic area (e.g., data engineering projects in a half-year). Capture decisions made, challenges, trade-offs chosen.
2. **Synthesize** those five docs into one narrow strategy document for that area.
3. Repeat for **five different areas** (front-end, mobile, platform, data, etc.).
4. **Synthesize** those five narrow strategies into a broad engineering strategy.

No mandate required. The document is valid strategy because it accurately describes how decisions are actually made — not how they should be made. It's inarguable because it's descriptive, not prescriptive. From there, specific areas that aren't working can be raised as concrete points of improvement with leadership.

## Books, Tools & Resources Mentioned

- **[Good Strategy, Bad Strategy](https://www.goodreads.com/book/show/11721966-good-strategy-bad-strategy)** — Richard Rumelt. Foundation text for the diagnosis/guiding-policy/coherent-actions framework. Larson recommends at minimum the first two chapters (~1–2 hours).
- **[An Elegant Puzzle: Systems of Engineering Management](https://lethain.com/elegant-puzzle/)** — Will Larson's first book on engineering management systems.
- **[Staff Engineer](https://staffeng.com/book)** — Will Larson's guide to operating as a staff-plus engineer.
- **[The Engineering Executive's Primer](https://lethain.com/eng-exec-primer/)** — Will Larson's third book (referenced as "coming early next year" at time of this talk, now published).
- **[Crafting Engineering Strategy](https://lethain.com/crafting-engineering-strategy/)** — Will Larson's fourth book, the direct full-length treatment of the ideas in this talk.
- **[Sorbet](https://sorbet.org/)** — Stripe's static typing solution for Ruby, cited as an example of investment only possible through concentrated monolith strategy.
- **[lethain.com/solving-the-engineering-strategy-crisis/](https://lethain.com/solving-the-engineering-strategy-crisis/)** — Written version of this talk (speaking notes + slides).

---

*Source: [Solving the Engineering Strategy Crisis — Will Larson](https://www.youtube.com/watch?v=vkfzpQ10eI4)*

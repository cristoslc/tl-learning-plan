# 6. Read the Strategic Map

[Back to Capability Map](concept-map)

**The situation:** Leadership makes a decision — standardize on C#, pursue MDM, invest in data products. You hear about it, maybe in a town hall, maybe secondhand. You can repeat the decision but you can't explain *why* it was made, which means you can't use it to inform your own technical choices or help your team understand what it means for their work.

**What changes:** You build a mental model of your organization's strategic bets: why a new platform exists (not a rewrite — a different architectural bet), why data products matter (raw outputs are feedstock, not finished goods), why master data management is being pursued at the organizational level, why language standardization has a business rationale beyond preference. You can connect a technical decision in your domain to the strategic context that motivates it.

**You're ready when:** Someone asks "why are we building a new platform instead of improving the legacy system?" or "what does 'data mesh ready' actually mean for us?" and you can give a clear, accurate, 2-minute answer without checking notes.

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Engineering strategy](https://lethain.com/engineering-strategy/) — Will Larson | Article | 15 min | How strategy actually forms: accumulated design decisions synthesized into direction. Not top-down visionary planning — bottom-up sense-making. This is the skill. |
| [Things You Should Never Do, Part I](https://www.joelonsoftware.com/2000/04/06/things-you-should-never-do-part-i/) — Joel Spolsky | Article | 10 min | The classic argument against rewrites. Read this first, then the counterpoint next — together they frame the "build alongside, don't throw away" approach. |
| [Lessons from 6 Software Rewrite Stories](https://medium.com/@herbcaudill/lessons-from-6-software-rewrite-stories-635e4c8f7c22) — Herb Caudill | Article | 25 min | The counterpoint: six real rewrites (Basecamp, VS Code, Gmail/Inbox, etc.) show that building new alongside old often works. The "new platform alongside legacy" approach fits this pattern. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Is High Quality Software Worth the Cost?](https://martinfowler.com/articles/is-quality-worth-cost.html) — Martin Fowler | Article | 15 min | Why internal quality reduces cost over time. The best single article for explaining platform investment to non-technical stakeholders. |
| [Technical Debt Quadrant](https://martinfowler.com/bliki/TechnicalDebtQuadrant.html) — Martin Fowler | Article | 5 min | The 2x2 matrix (reckless/prudent vs deliberate/inadvertent) gives you vocabulary for explaining which kind of debt you're dealing with and why it matters. |
| [Presenting to executives](https://lethain.com/presenting-to-executives/) — Will Larson | Article | 10 min | Business value (1-2 sentences) → historical narrative (2-4 sentences) → explicit ask (1-2 sentences). The simplest framework for presenting technical decisions to leadership. |
| [Building an effective technical strategy](https://leaddev.com/leadingeng-london-2023/video/building-effective-technical-strategy) — Sarah Wells ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/building-an-effective-technical-strategy-sarah-wells.md)) | Video | 30 min | How to decide what to prioritize, document your strategy, and communicate it so people can actually use it to make decisions. |
| [ThoughtWorks Technology Radar](https://www.thoughtworks.com/radar) — ThoughtWorks | Guide | 20 min | The Adopt/Trial/Assess/Hold framework for evaluating and standardizing on technologies. Study the methodology, not just the results. |
| [The Platform and Program Split at Uber](https://newsletter.pragmaticengineer.com/p/program-platform-split-uber) — Gergely Orosz | Article | 30 min | How Uber structured platform teams (building blocks) vs program teams (business outcomes). A case study of standardization through platform ownership. |
| [Agile Master Data Management](https://agiledata.org/essays/masterdatamanagement.html) — Scott Ambler | Article | 20 min | What MDM is, why enterprises pursue it, and why traditional approaches fail. Practical and vendor-neutral — explains why organizations care about shared definitions of core entities. |
| [Bottleneck #01: Tech Debt](https://martinfowler.com/articles/bottlenecks-of-scaleups/01-tech-debt.html) — Martin Fowler et al. | Article | 25 min | Organizational patterns for managing tech debt as a strategic concern: auditing, ownership, tiger teams. Not just code cleanup — the business of debt management. |
| [Data Monolith to Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html) — Zhamak Dehghani | Article | 30 min | The original data mesh article — included here for the strategic "why" of domain-oriented data ownership, not the technical "how" (which is in Cap 5). |
| [Hohpe Ch 9: Architecture Is Selling Options](https://learning.oreilly.com/library/view/the-software-architect/9781492077534/ch09.html) — Gregor Hohpe | Book | ~20 min | Every technology decision is buying an option. The question isn't "is C# good?" but "what options does C# preserve and what does it foreclose?" The framework for evaluating any strategic technology commitment — language, platform, vendor, stack. |
| [Hohpe Ch 6: Making Decisions](https://learning.oreilly.com/library/view/the-software-architect/9781492077534/ch06.html) — Gregor Hohpe | Book | ~20 min | How architects frame decisions in complex environments. Pairs with Ch 9 — one is the framing, the other is the evaluation method. |
| [Hohpe Ch 15: A4 Paper Doesn't Stifle Creativity](https://learning.oreilly.com/library/view/the-software-architect/9781492077534/ch15.html) — Gregor Hohpe | Book | ~15 min | Standards (like language standardization) enable rather than restrict. The constructive framing for explaining why organizations standardize on specific languages. |
| [Hohpe Ch 26: Reverse Engineering Organizations](https://learning.oreilly.com/library/view/the-software-architect/9781492077534/ch26.html) — Gregor Hohpe | Book | ~20 min | Applying architectural analysis to understand why an organization makes the decisions it does. The diagnostic skill behind "read the strategic map." |
| [Larson §3.3: Visions and strategies](https://learning.oreilly.com/library/view/an-elegant-puzzle/9781492077930/ch03.html#visions_and_strategies) — Will Larson | Book | ~20 min | How to write and use strategy and vision documents. The structural companion to Larson's blog posts on engineering strategy. |
| [Larson §3.6: Migrations](https://learning.oreilly.com/library/view/an-elegant-puzzle/9781492077930/ch03.html#migrations_the_sole_scalable_fix_to_tech) — Will Larson | Book | ~25 min | Migrations as the sole scalable fix to tech debt. Directly relevant to legacy-to-new-platform migrations — how to run a migration that actually completes. |

### Practice This

Pick one of your organization's strategic bets (language standardization, master data management, data products, the new platform itself). Write a 2-minute explanation of *why* — not what the decision is, but what problem it solves and what would happen if the organization didn't make this bet. Test it on a colleague who isn't in this program.

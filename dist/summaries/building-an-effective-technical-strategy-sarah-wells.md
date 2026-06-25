---
podcast_url: https://leaddev.com/leadingeng-london-2023/video/building-effective-technical-strategy
transcript_url:
updated: 2026-03-28
---

# Building an Effective Technical Strategy — Sarah Wells — LeadingEng London 2023

- **Speaker:** Sarah Wells, Independent Consultant & Author (formerly Technical Director, Financial Times)
- **Event:** LeadingEng London 2023
- **Format:** Conference talk (~30 min)
- **Published:** March 2, 2023
- **Slides:** [Publicly available PDF](https://leaddev.com/wp-content/uploads/2023/03/BuildingAnEffectiveTechnicalStrategy-FINAL-2.pdf)

## Key Takeaways

A technical strategy only exists if it is written down, communicated relentlessly, and tracked — undocumented strategy leads to divergent local decisions that silently undermine the whole organisation.

> 1. **Strategy as diagnosis + guiding policies + coherent actions** — a good strategy has all three elements (the kernel from "Good Strategy, Bad Strategy"). Diagnosis names the challenge. Policies set the direction. Actions are feasible and mutually reinforcing.
> 2. **Boring is good** — Will Larson's insight holds: good engineering strategy is deliberately unglamorous. Resist including your best ideas. Write five design docs first, then synthesise what keeps coming up. That's your strategy.
> 3. **Avoid the "Air Sandwich"** — the gap between executive vision and day-to-day execution (from Nilofer Merchant's *The New How*). Fill it with an explicit, documented strategy that connects business goals to engineering decisions.
> 4. **Communication is not a one-shot** — the model is Transmitted → Received → Understood → Agreed → Converted to useful action. If your team isn't complaining that you're over-communicating, you haven't communicated enough.
> 5. **Alignment AND surfacing conflict both have value** — good strategy helps teams make consistent decisions autonomously, but it also surfaces where strategies from different parts of the organisation clash. Resolve conflicts explicitly rather than leaving them to fester.
> 6. **Tracking matters** — a strategy that isn't measured will drift. Use OKRs (or equivalent) tied to strategy milestones, and revisit the strategy itself as context changes. Adapting is not failure.

## Speaker Background

Sarah Wells spent over a decade at the Financial Times, rising to Technical Director for Engineering Enablement and Operations — the span of her tenure covered the FT's transformation from 12 releases a year to more than 20,000, encompassing the shift to microservices, containers, DevOps, and platform engineering. She left the FT and now works as an independent consultant specialising in engineering effectiveness, technical strategy, incident management, and platform engineering. She is the author of **Enabling Microservice Success** (O'Reilly), a practitioner-level book covering the technical, organisational, and cultural challenges of microservice adoption. She is a regular conference speaker at LeadDev, QCon, YOW!, and GOTO, and has chaired QCon London.

Wells was invited for this talk because the "Building an Effective Technical Strategy" theme had become a recurring pain point surfaced in the LeadingEng community: many engineering leaders know *why* strategy matters but struggle with the practical mechanics of creating one that actually guides decisions.

## Core Thesis

Most engineering organisations have a technical strategy — it exists implicitly in the choices they keep making. The problem is that **an undocumented strategy cannot be shared, challenged, or acted on consistently across teams**. Wells argues that writing the strategy down is only the beginning: you also need to communicate it so that people can use it as a decision-making tool, and track it so you can tell whether it is working and adapt when the context changes.

The talk is structured around the full lifecycle of a technical strategy: **coming up with it → documenting it → implementing/communicating it → tracking progress and adapting**.

## Major Topics Discussed

### What Makes a Good Strategy

Wells grounds the talk in Richard Rumelt's "kernel of a strategy" from **Good Strategy, Bad Strategy**:

- **1. A diagnosis** — a clear-eyed description of the challenge being faced. "What is going on here?" Bad strategies skip this; they start with solutions.
- **2. Guiding policies** — principles or approaches that define how you will tackle the challenge. Real FT examples from the slides: *Cloud-only 2020* (no new on-premise infrastructure), *No Next-Next* (stop releasing big-bang future versions of products), *Get off the monolith* (decompose the legacy monolith into independently deployable services).
- **3. Coherent and feasible actions** — things you will actually do, grounded in the policies. The three elements together can be summarised as **What, Why, and How**.

### Coming Up with Your Strategy

- **You need a strategy for your part of the organisation** — don't wait for a strategy to come from above. Own the level you lead.
- **Avoid the Air Sandwich** (Nilofer Merchant, *The New How*): the dangerous gap between high-level vision and day-to-day execution, filled with misunderstandings and misalignment. Document your strategy explicitly to close this gap.
- **Look at the context and what's changing** — strategy should be a response to your actual situation: technical debt landscape, team capability, competitive pressure, regulatory environment.
- **Don't be afraid of being boring** (Will Larson) — resist the temptation to make your strategy visionary and exciting. Practical, specific guidance that helps people make daily decisions is more valuable than inspiring prose that no one acts on.
- **Start from design docs** — Wells endorses Larson's bottom-up method: write five design documents, look for the decisions and trade-offs that keep coming up across them, then synthesise those into strategy. Design docs have the specificity that abstract strategy lacks. "Write five, then synthesise."
- **Write it down in different ways** — the FT published their [Tech Principles publicly](https://www.ft.com/tech-principles). Presenting the same strategy as principles, as a narrative, as a roadmap, etc. increases the surface area for it to land with different audiences.

### Implementing (Communication)

- The key insight here is that after spending weeks writing the strategy, **to most people this is new**. The author's freshness means they over-estimate how much others already understand.
- **Talk about it. In lots of different ways. In lots of different ways.** (The repetition in the slide is intentional — Wells uses it to make the point viscerally.)
- The communication ladder (attributed via Jason Yip to Alia Rose Connor): **Transmitted → Received → Understood → Agreed → Converted to useful action**. Most communication effort stops at "transmitted." You need to reach "converted to useful action."
- Key quote: *"If they're not complaining that you're communicating too much, you probably haven't communicated it enough."* (Jason Yip)
- **Using OKRs (or equivalent)** to connect strategy to team-level work. Strategy without OKRs stays abstract; OKRs without strategy are disconnected activity.
- **Find the places where strategies conflict** — surfacing conflicts is a feature, not a failure. When two teams' strategies pull in opposite directions, making that visible enables resolution rather than silent drift.

### Tracking Progress and Adapting

- A strategy must answer: **how will you know if it is successful?** The FT's *Cloud-only 2020* strategy is a good example — it had an explicit end-state with a date, making progress measurable.
- **Adapting to change** is expected and healthy. Strategy is not a commitment to ignore new information; it is a lens for evaluating new information. "Nailing the switch" — knowing when to update or replace a strategy — requires tracking whether the original diagnosis is still accurate.
- The final key point from the closing summary: *"There is value in alignment AND in surfacing conflict."* Both are legitimate outcomes of a living strategy.

## Books, Tools & Resources Mentioned

- **Good Strategy, Bad Strategy** — Richard Rumelt. The foundational framework for the "kernel" of strategy (diagnosis, guiding policies, coherent action). Core to Wells' mental model throughout.
- **The New How: Creating Business Solutions through Collaborative Strategy** — Nilofer Merchant. Source of the "Air Sandwich" concept — the dangerous void between vision and execution.
- **Will Larson** — ["Good engineering strategy is boring"](https://lethain.com/good-engineering-strategy-is-boring/) and ["Engineering Strategy"](https://lethain.com/eng-strategies/) (staffeng.com). Practical guidance on writing strategy from design docs and on why boring is a virtue.
- **Anna Shipman** — ["No Next Next"](https://medium.com/ft-product-technology/no-next-next-42c71541ebcc) (FT blog post) and ["Tech Strategy Process"](https://www.annashipman.co.uk/jfdi/tech-strategy-process.html). Real examples from the FT's strategy history.
- **Mark Barnes** — ["Making the Case for Cloud-Only"](https://medium.com/ft-product-technology/making-the-case-for-cloud-only-92f382ff8dd9) (FT blog post). The FT's cloud-only strategy case study.
- **Jason Yip** — ["Why Aligned Autonomy is an Ongoing Struggle"](https://jchyip.medium.com/why-aligned-autonomy-is-an-ongoing-struggle-efa62e272d5d). Source of the communication ladder and the "over-communicating" quote.
- **FT Tech Principles** — [ft.com/tech-principles](https://www.ft.com/tech-principles). A real-world example of publishing strategy externally.
- **What Matters** — [whatmatters.com](https://www.whatmatters.com/faqs/okr-meaning-definition-example). OKR reference for connecting strategy to execution.

---

*Source: [Building an Effective Technical Strategy — Sarah Wells — LeadingEng London 2023](https://leaddev.com/leadingeng-london-2023/video/building-effective-technical-strategy) (video requires LeadDev ticket; slides publicly available at the link above)*

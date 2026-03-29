---
podcast_url: https://www.youtube.com/watch?v=1i6QYvYhlYQ
transcript_url:
updated: 2026-03-28
---

# 50,000 Orange Stickies Later — Alberto Brandolini

- **Speaker:** Alberto Brandolini, creator of EventStorming
- **Event:** Explore DDD 2017
- **Format:** Conference talk + Q&A
- **Duration:** ~54 minutes

## Key Takeaways

EventStorming is a collaborative modeling technique that uses sticky notes on a timeline to make entire business processes visible — and its real power is surfacing the conflicts, ambiguities, and organizational dysfunction that no requirements document will ever capture.

> 1. **EventStorming is like pizza — multiple recipes** — Big Picture for discovery (up to 35 people), Process Modeling for detailed flow analysis, and Software Design for implementation-ready models. Same building blocks, different zoom levels.
> 2. **"Gossip does not compile"** — you can't turn organizational politics, siloed knowledge, and unspoken conflicts into requirements. But put everyone in a room with sticky notes and a timeline, and inconsistencies become impossible to hide.
> 3. **Domain events are the best lingua franca** — events (past tense, business-relevant) work better than entities or data models as a shared language because business people naturally think in terms of "what happened," not database schemas.
> 4. **Fuzzy definitions are deliberate** — strict notation excludes people from the conversation. Incremental, loose notation invites cross-functional participation and lets precision emerge through discussion.
> 5. **Focus on behavior, not data** — aggregates emerge last in EventStorming, discovered through commands and events. Postpone naming entities; the aggregate is "the yellow thing between the blue and the orange."
> 6. **Not every problem needs this depth** — EventStorming's deep design mode is for the core domain where experiments pay off, not for supporting subdomains like logging or security.

## Speaker Background

Alberto Brandolini is an Italian software consultant who invented EventStorming, a workshop-based modeling technique that has become one of the most widely adopted DDD practices. He runs Avanscoperta (his consultancy) and has been writing the EventStorming book for years (a running joke in the community). The technique originated almost by accident at an Italian DDD meetup where Brandolini modeled a business process with an IKEA paper roll and orange sticky notes — and realized he'd stumbled onto something powerful.

## Core Thesis

The fundamental lie in software development is that "we just need to understand the business and translate it into code." In reality, business knowledge is fragmented across silos, riddled with conflicts, and shaped by organizational politics. EventStorming bypasses the broken telephone of requirements gathering by putting all stakeholders in one room to collaboratively build a visible, timeline-based narrative of their business. The resulting model isn't just a technical artifact — it's the first time many organizations see their own business process end-to-end.

## Major Topics Discussed

### [[00:03:27]](https://youtu.be/1i6QYvYhlYQ?t=207) The Big Picture Format

The most famous EventStorming recipe. Invite the right people (business, IT, UX — 20-35 participants), provide unlimited modeling space (long paper roll), and have them place orange sticky notes (domain events, past tense) on a timeline. The first 2-5 minutes feel awkward and chaotic, then it starts working. Structure emerges naturally as people see separations between concerns, departments, and goals. **Hot spots** (purple stickies) mark conflicts and ambiguities. The outcome: the whole business flow is visible, the key bottleneck is identified, and participants vote on the most important area to tackle.

### [[00:06:06]](https://youtu.be/1i6QYvYhlYQ?t=366) Why Requirements Gathering Fails

Business experts know their own portion well but live in silos. Organizational culture creates unhealthy competition where every department wants to be "the second worst." Knowledge is distributed unevenly with diverging opinions, mysterious undocumented processes, and departed employees who took critical knowledge with them. You can't translate this into requirements — but you can make it visible by having everyone build one consistent narrative together.

### [[00:09:00]](https://youtu.be/1i6QYvYhlYQ?t=540) Making Conflicts Visible

When different departments place their locally-ordered event sequences on the same timeline, gaps and conflicts surface immediately. "The moment you put the two timelines in the same place, you realize you've got to talk." Purple hot-spot stickies annotate where things are going wrong. This is the learning notepad — visible, shared, impossible to ignore.

### [[00:12:12]](https://youtu.be/1i6QYvYhlYQ?t=732) Incremental Notation

EventStorming deliberately avoids UML, BPMN, or any strict notation that would exclude non-technical participants. The notation is defined on the fly with "professional touch" — just enough structure to enable conversation without creating gatekeeping. Sticky figures for users/actors, orange for events, blue for commands, yellow for aggregates, lilac for policies. "Choosing a strict notation is excluding people from the conversation."

### [[00:14:24]](https://youtu.be/1i6QYvYhlYQ?t=864) Finding the Core Domain

After the Big Picture exploration, participants autonomously vote on what they think is the most important area. In established companies, the core problem is usually genuinely hard (if it were easy, smart people would have already solved it). Brandolini's approach: "Try hard till you find the solution" — no estimates, no sprint-fitting. Like Dr. House diagnosing rare conditions, not treating the common flu.

### [[00:21:18]](https://youtu.be/1i6QYvYhlYQ?t=1278) Process Modeling

The second recipe — scoped to a specific feature set or epic. More structured than Big Picture with explicit building blocks: **read models** (data users need to make decisions), **commands** (user actions), **aggregates** (processing), **domain events** (outcomes), and **policies** (reactive rules: "whenever X happens, then do Y"). Policies define company behavior and span the full spectrum from implicit human habits to fully automated sagas.

### [[00:26:27]](https://youtu.be/1i6QYvYhlYQ?t=1587) Challenging Value at Every Step

Every step in the flow can create or destroy value for users. Value isn't just money — it includes anxiety reduction, reputation, personal satisfaction. By mapping emotional value alongside functional flow, teams discover opportunities to make people happy along the journey. This naturally converges with customer journey mapping without requiring a UX specialist in the room.

### [[00:30:49]](https://youtu.be/1i6QYvYhlYQ?t=1849) Software Design Level

The third recipe adds aggregates explicitly. Key insight: **arrive at the aggregate last**, after discovering all commands and events. The aggregate is the "local decision-making" component — it accepts or rejects commands based on internal state. **Postpone naming** to avoid data-first thinking ("this is clearly an Order with a customer and total amount..."). Focus on behavior: which bits of information trigger a given behavior? The best indicator of a successful modeling session is **how much trash you're producing** (discarded sticky notes).

### [[00:33:14]](https://youtu.be/1i6QYvYhlYQ?t=1994) Ubiquitous Language — Multiple, Not One

At the Big Picture level, it's obvious you won't have one ubiquitous language. Departments have their own consistent internal conversations — trying to force a single enterprise-wide vocabulary creates composite names ("purchase order" vs "order history") that nobody actually uses. Instead, accept multiple bounded languages and use domain events as the lingua franca at boundaries. Events have "some hope of becoming lingua franca over all the organization."

### [[00:38:43]](https://youtu.be/1i6QYvYhlYQ?t=2323) Read Models as Decision-Making Tools

Read models are not "just data" — they are **the data needed for a user to take a given decision**. Example: filling a timesheet three weeks late. Your read model isn't the timesheet form — it's your Google Calendar, GitHub commits, phone records, and sent emails for that day. If you can aggregate those into one screen, the problem becomes trivial. "Read models are not exposing data; they are decision-making tools."

### [[00:44:22]](https://youtu.be/1i6QYvYhlYQ?t=2662) Takeaways and Zoom Levels

EventStorming works at every zoom level — from C-suite vision conversations to IDE-ready implementation — using the same building blocks (events, commands, policies, aggregates). You can zoom in and out: discover that the big-picture vision was inconsistent, or that the detailed process isn't viable, and move up and down freely. It's also a platform for team self-organization: when the system is clear and understandable, people naturally organize around the work.

## Books, Tools & Resources Mentioned

- **EventStorming** (book, in progress) — Alberto Brandolini (eventstorming.com)
- **Avanscoperta** — Brandolini's consultancy
- **IKEA paper rolls** — the original modeling surface
- **3M orange sticky notes** — the core building block (Brandolini jokes that 3M saw a spike in consumption)
- **Vaughn Vernon's IDDD Tour** — where EventStorming gained early traction with the DDD community
- **Theory of Constraints** — referenced for the concept of bottlenecks in the business flow
- **Lean Startup** — referenced for the culture of continuous experimentation

---

*Source: [50,000 Orange Stickies Later — Alberto Brandolini](https://www.youtube.com/watch?v=1i6QYvYhlYQ)*

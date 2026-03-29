# 9. Write to Drive Decisions

[Back to Capability Map](concept-map)

**The situation:** You had a great conversation in a meeting. Everyone agreed on the approach. Two weeks later, nobody can remember what was decided or why. Or: you have an important technical position, but you can't get 30 minutes with the right people. Or: a decision needs input from people in three time zones who will never be in the same room.

**What changes:** You learn that writing is not documentation — it's a tool of influence. An RFC isn't a formality; it's how you get a decision made without needing everyone in a room. An ADR isn't a record; it's how you prevent the same argument from happening every quarter. You develop the habit of writing the decision down *before* the meeting, so the meeting is about refinement, not discovery.

**You're ready when:** You've written an RFC or design doc that drove a real decision — not just described one after the fact. Someone disagreed with a specific section, you revised it, and the result was better than either of your original positions.

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Scaling the Practice of Architecture, Conversationally](https://martinfowler.com/articles/scaling-architecture-conversationally.html) — Andrew Harmel-Law | Article | 30 min | Writing as the mechanism that makes architecture collaborative, not top-down. ADRs and conversational practices. |
| [FSA Ch 19: Architecture Decisions](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch19.html) — Richards & Ford | Book | ~35 min | ADR structure, anti-patterns. The reference chapter for writing decisions that stick. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Writing an Engineering Strategy](https://lethain.com/eng-strategies/) — Will Larson | Article | 15 min | Strategy docs as the upstream artifact framing all downstream decisions. Overlaps with Cap 7 but here the focus is on writing craft. |
| [The Architect Elevator — Visiting the Upper Floors](https://martinfowler.com/articles/architect-elevator.html) — Gregor Hohpe | Article | 15 min | Writing for executives vs writing for engineers — same decision, different framing. |
| [FSA Ch 20: Analyzing Architecture Risk](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch20.html) — Richards & Ford | Book | ~30 min | Risk storming as a collaborative written exercise. Surfacing and documenting architectural risks systematically. |

### Practice This

Pick one architectural decision facing your team's platform (e.g., offline-first vs cloud-first for field data, build vs buy for report generation). Write a one-page decision document: context, options considered, recommendation, trade-offs, what you're giving up. Share it with a colleague and ask them to disagree with one specific point.

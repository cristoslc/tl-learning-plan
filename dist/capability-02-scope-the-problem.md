# 2. Scope the Problem

[Back to Capability Map](concept-map)

**The situation:** There's a vague mandate: "build a new platform." Or a specific one that's actually three problems wearing a trenchcoat. Everyone has opinions about what to build. Nobody has explicitly decided what's out of scope. You're six weeks into design before someone realizes half the team assumed mobile support was in scope and the other half assumed it wasn't.

**What changes:** You learn to frame problems before solving them. What's the actual question? Who are we building for first? What would we *not* build even if we could? You develop the discipline of writing a scope statement that's specific enough to be wrong — "MVP supports core services and product lines A, B, and C; remaining lines are post-launch" — so it can be debated and refined rather than left ambiguous.

**You're ready when:** Given a vague initiative, you can produce a one-page scope statement that names the problem, the audience, what's in, what's explicitly out, and what assumptions you're making. Your team can read it and disagree with specific points instead of talking past each other.

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Solving the Engineering Strategy Crisis](https://lethain.com/solving-the-engineering-strategy-crisis-videos/) — Will Larson ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/solving-the-engineering-strategy-crisis-will-larson.md)) | Video | 49 min | What engineering strategy is and how to make scope decisions visible, accountable, and improvable. |
| [Writing an Engineering Strategy](https://lethain.com/eng-strategies/) — Will Larson | Article | 15 min | Practical framework for strategy documents that scope work. Real examples from Stripe, Uber, Calm. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Core Domain Patterns](https://medium.com/nick-tune-tech-strategy-blog/core-domain-patterns-941f89446af5) — Nick Tune | Article | 10 min | Core Domain Charts: classify capabilities as core (build), supporting (buy), or generic (outsource). Structured scoping. |
| [FSA Ch 5: Identifying Architectural Characteristics](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch05.html) — Richards & Ford | Book | ~30 min | Extracting architectural priorities from domain concerns. The fewest characteristics necessary — scoping applied to architecture. |
| [FSA Ch 19: Architecture Decisions](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch19.html) — Richards & Ford | Book | ~35 min | ADRs as scope artifacts: documenting what was decided, why, and what was rejected. Anti-patterns: Covering Your Assets, Groundhog Day. |

### Practice This

Write a scope statement for your team's next major platform milestone. Which service offerings are in the first launch? Which business capabilities are fully in scope, which are partial, which are deferred? What platform services does that imply? Make it specific enough that someone could disagree with a particular line.

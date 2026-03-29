# 1. Smell-Test an Architectural Claim

[Back to Capability Map](concept-map)

**The situation:** Someone in a design review says "we need microservices for scalability" or "event sourcing is the right pattern here." It sounds reasonable. You're not sure if it actually is, but you don't have a way to push on it without sounding like you're just being difficult.

**What changes:** You develop a reflex: *what kind of claim is this?* Some claims are backed by decades of evidence (tight coupling increases change cost). Some are patterns that work in specific contexts (event sourcing — when you need audit trails and temporal queries). Some are rules of thumb being stated as laws. Some are conference hype. The response is different for each. You stop asking "is this right?" and start asking "what would have to be true for this to be right?"

**You're ready when:** You hear an architectural assertion in a meeting and your first instinct is to classify it, not accept or reject it. You can say "that's a reasonable pattern — what's the context that makes it fit here?" without preparation.

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [How to Think Like an Architect](https://www.youtube.com/watch?v=W7Krz__jJUg) — Mark Richards ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/how-to-think-like-an-architect-mark-richards.md)) | Video | 45 min | The "triangle of knowledge" — knowing what you don't know — and how to translate business needs into architectural characteristics. Practical daily habits, not theory. |
| ["Good Enough" Architecture](https://www.youtube.com/watch?v=PzEox3szeRc) — Stefan Tilkov ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/good-enough-architecture-stefan-tilkov.md)) | Video | 42 min | Six real architectures that went wrong. Teaches you to see when a claim has too much or too little architectural ambition — calibrates your instincts. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Thinking Like an Architect](https://www.infoq.com/presentations/architect-lessons/) — Gregor Hohpe ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/thinking-like-an-architect-gregor-hohpe.md)) | Video | 50 min | Two decades of practice distilled: how architects share decision models, reveal blind spots, and bridge organizational layers. |
| [Software Architecture: The Hard Parts](https://www.infoq.com/podcasts/software-architecture-hard-parts/) — Neal Ford & Mark Richards ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/software-architecture-hard-parts-infoq-podcast.md)) | Podcast | 37 min | The two laws: "everything is a trade-off" and "why is more important than how." How to evaluate distributed architecture decisions. |
| [Is High Quality Software Worth the Cost?](https://martinfowler.com/articles/is-quality-worth-cost.html) — Martin Fowler | Article | 15 min | Subverts the "quality vs. speed" trade-off — shows that internal quality (architecture) actually reduces cost over time. Essential for evaluating "we don't have time for good architecture." |
| [The Elephant in the Architecture](https://martinfowler.com/articles/value-architectural-attribute.html) — Martin Fowler & Birgitta Boeckeler | Article | 20 min | Business value as the most overlooked factor in architectural assessment. |
| [developertoarchitect.com/lessons](https://developertoarchitect.com/lessons/) — Mark Richards | Video series | 10 min each | 200+ bite-sized architecture lessons. Browse the catalog and pick what's relevant — good for filling specific gaps. |
| [FSA Ch 2: Architectural Thinking](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch02.html) — Richards & Ford | Book | ~45 min | Goes deeper than the Richards talk: how architects and developers should collaborate, technical breadth vs depth, analyzing trade-offs, and understanding business drivers. |
| [FSA Ch 4: Architecture Characteristics Defined](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch04.html) — Richards & Ford | Book | ~30 min | Systematic framework for the "-ilities" — operational, structural, and cross-cutting. How to select the fewest characteristics necessary to avoid over-engineering. |
| [BEA Ch 8: Pitfalls and Antipatterns](https://learning.oreilly.com/library/view/building-evolutionary-architectures/9781492097532/ch08.html) — Ford, Parsons et al. | Book | ~40 min | Pattern recognition for bad claims: Vendor King, Last 10% Trap, resume-driven development, inappropriate governance. Once you've read this, you'll spot these in the wild. |

### Practice This

Pick a claim from a recent design review or architecture proposal at your company. Write down: what kind of claim is this? What evidence would support it? What context would it need to be true? Bring your analysis to a session.

# Use AI as a Thinking Partner

[Back to Capability Map](concept-map)

Not numbered in the main sequence — this is a force multiplier you use alongside every other capability.

**The situation:** You have GitHub Copilot. Maybe you've tried Claude or ChatGPT. You use them for autocomplete or quick answers. But when you try to use them for something harder (analyze this design, find gaps in this proposal), the results are either too generic or hard to trust, and you can't always tell why.

**What changes:** You stop treating AI like a search engine and start treating it like a fast but uneven thinking partner. That means you lead the conversation — you provide the context, you set the constraints, you decide what's actually useful in the response. The AI gets better because *you* get better at asking. And you develop a healthy skepticism: AI output can sound authoritative whether it's right or wrong, so you learn to check its reasoning against your own domain knowledge instead of taking the confidence at face value.

**You're ready when:** You can take a document (a design proposal, a set of requirements) and run a structured AI-assisted analysis that produces findings you'd trust enough to bring into a review — with your own judgment applied on top, not just the AI's output.

### Start here

| Resource | Format | Time | Why this one |
|----------|--------|------|-------------|
| [Agentic Coding: Armin Ronacher](https://www.youtube.com/watch?v=bpWPEhO7RqE) — Armin Ronacher ([summary](https://github.com/cristoslc/tl-learning-plan/blob/main/dist/summaries/agentic-coding-armin-ronacher.md)) | Video | 71 min | The creator of Flask sharing his real production workflow with Claude Code — when agents excel, where they fail, and why the human stays in the loop. Grounded, hands-on perspective from someone shipping with these tools daily. |
| [AI Coding Degrades: Silent Failures Emerge](https://spectrum.ieee.org/ai-coding-degrades) — IEEE Spectrum | Article | 10 min | How LLMs produce code that avoids crashes but silently removes safety checks and fakes output formatting. The failure modes you need to recognize. |

### Go deeper

| Resource | Format | Time | What it adds |
|----------|--------|------|-------------|
| [Measuring AI Impact on Experienced Developer Productivity](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) — METR | Research + summary | 20 min | Rigorous study: AI tools made experienced developers 19% *slower* on familiar codebases — despite developers believing they were 20% faster. The gap between perceived and actual productivity. |
| [A Year of Vibes](https://lucumr.pocoo.org/2025/12/22/a-year-of-vibes/) — Armin Ronacher | Article | 15 min | Full-year retrospective on agentic coding in production — what worked, what didn't, how the workflow evolved. |
| [Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/) — Simon Willison | Guide | 30 min | Curated collection of practices for getting the best results from AI coding agents, from one of the most respected voices in the Python/open-source community. Living document — check back. |
| [AI Tooling for Software Engineers in 2026](https://newsletter.pragmaticengineer.com/p/ai-tooling-2026) — Gergely Orosz | Article | 25 min | Survey of ~1000 professional engineers on actual AI tool usage. Data-driven picture of how the industry works with these tools now, not how vendors say it should. |

### Practice This

Take a section of a recent architecture proposal (or any design document you're working with). Feed it to Claude or ChatGPT with specific context: "Here's a section of an architectural proposal for our platform. Here's what I know about the domain: [your knowledge]. What assumptions is this section making? Where are the gaps?" Compare the AI's findings to your own reading. Where did it add value? Where did it miss something you caught? Where did its confidence outrun its reasoning?

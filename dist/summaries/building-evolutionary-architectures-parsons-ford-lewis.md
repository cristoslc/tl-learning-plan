---
podcast_url: https://www.youtube.com/watch?v=m2ZlX1je3as
transcript_url:
updated: 2026-03-28
---

# Building Evolutionary Architectures — Rebecca Parsons, Neal Ford & James Lewis

- **Speakers:** Rebecca Parsons (CTO, ThoughtWorks), Neal Ford (ThoughtWorks), James Lewis (ThoughtWorks)
- **Event:** GOTO Book Club 2023
- **Format:** Panel discussion / interview
- **Duration:** ~46 minutes

## Key Takeaways

An evolutionary architecture supports guided, incremental change across multiple dimensions. Fitness functions — borrowed from evolutionary computing — are the mechanism that makes this practical by turning architectural governance into automated, objective, verifiable checks.

> 1. **Architecture must be designed to change, not to last** — the old mindset that architecture is "the foundation, the rock" is professionally irresponsible in a rapidly changing technology landscape. Five-year technology roadmaps were never realistic.
> 2. **Evolutionary architecture = guided + incremental + multiple dimensions** — "guided" comes from fitness functions, "incremental" means you constantly adapt to the current landscape, and "multiple dimensions" acknowledges you can't optimize for all -ilities simultaneously.
> 3. **Fitness functions are the unifying metaphor** — performance, security, code quality, coupling, observability — all become members of the same family: architectural governance. This gives you apples-to-apples comparisons between seemingly disparate concerns.
> 4. **Coupling is the enemy of evolvability** — the more implementation coupling leaks across boundaries, the less evolvable the architecture. The extreme case: exposing database tables as your integration architecture. Connascence (from 1993) provides a vocabulary for describing coupling types and their scope.
> 5. **Make governance objective, not fluffy** — "we need scalability" means nothing. Put a concrete number on it. Fitness functions force conversations between architects (who care about long-term asset value) and developers (who face delivery pressure), creating shared understanding.
> 6. **Implementing fitness functions forces prioritization** — unlike spreadsheets of principles that grow forever, having to implement automated checks imposes real-world time and resource constraints. You must decide which characteristics actually matter.

## Speaker Background

**Rebecca Parsons** is CTO of ThoughtWorks with a background in evolutionary computation, genetic algorithms (postdoc at Los Alamos), and programming languages. She originated the idea of applying evolutionary fitness functions to software architecture governance. **Neal Ford** is a director at ThoughtWorks who has co-authored multiple architecture books including *Fundamentals of Software Architecture* and *Software Architecture: The Hard Parts*. **James Lewis** is a director at ThoughtWorks who co-originated the term "microservices" with Martin Fowler.

## Core Thesis

Architecture isn't something you design once and defend forever — it's something that must evolve as the technology landscape, business requirements, and organizational context change. Fitness functions (from evolutionary computing) provide a mechanism to guide that evolution: automated, objective checks that verify your architecture maintains the characteristics you've identified as crucial. The second edition focuses on coupling as the core structural factor that determines evolvability, with bounded contexts (DDD) as the key mechanism for controlling coupling.

## Major Topics Discussed

### [[00:05:02]](https://youtu.be/m2ZlX1je3as?t=302) What Is Evolutionary Architecture?

Rebecca Parsons defines it as "guided incremental change across multiple dimensions." **Guided:** fitness functions define what matters for THIS system (a sandwich ordering system doesn't need high scalability). **Incremental:** constantly adapting to the current technology and business landscape. **Multiple dimensions:** you can't optimize for all -ilities — you pick and choose, but introduce evolvability as a first-class concern.

### [[00:08:07]](https://youtu.be/m2ZlX1je3as?t=487) What Changed in the Second Edition

The first edition surveyed architecture styles head-to-head. The second edition focuses on **coupling** as the fundamental factor. The more implementation coupling leaks across boundaries, the less evolvable the architecture. Example: a client exposed relational tables to their integration architecture — any single table change could wreck the ecosystem. Domain-driven design's bounded contexts translate into architecture terms as "protecting the ability to evolve structurally."

### [[00:11:01]](https://youtu.be/m2ZlX1je3as?t=661) Connascence: A Vocabulary for Coupling

From a 1993 book ("What Every Programmer Should Know About Object-Oriented Design") — connascence provides a taxonomy for coupling types (of name, of meaning, of identity/transactional). Key insight from 1993: the more connascence you have, the tighter its scope should be. This was essentially bounded contexts before Eric Evans named them. Dynamic connascence (transactional coupling) stretched across distributed systems is the most destructive form.

### [[00:15:00]](https://youtu.be/m2ZlX1je3as?t=900) Fitness Functions from Evolutionary Computing

The metaphor comes from optimization, not biology. In evolutionary computing, fitness functions define the landscape you're navigating to find solutions that balance competing objectives. For architecture: performance requirements, security requirements, code quality, coupling constraints — all become fitness functions. They look like unit tests but test architectural characteristics instead of behavior. Tools like ArchUnit let you encode constraints like "does my software respect my layering?"

### [[00:18:28]](https://youtu.be/m2ZlX1je3as?t=1108) The Mindset Shift

"When I first started talking about evolutionary architecture, people would come up to the stage and whisper 'don't you think you're being professionally irresponsible to talk about evolving an architecture?'" Architecture was seen as immutable — the foundation. But the technology landscape changes so rapidly that five-year roadmaps were fiction. The shift: start with "this stuff is going to have to change" and ask "what characteristics must I maintain through that change?"

### [[00:22:52]](https://youtu.be/m2ZlX1je3as?t=1372) Why Fitness Functions Beat Spreadsheets

You can keep adding principles to a spreadsheet forever. But implementing fitness functions imposes real constraints — you must prioritize. This forces the crucial conversation: architects (focused on long-term asset value) and developers (focused on delivery speed) have inherently conflicting goals. Fitness functions make governance objective, forcing both sides to communicate about what really matters. "In the perfect organization, enterprise architects all the way down to developers — everyone's equally unhappy."

### [[00:27:29]](https://youtu.be/m2ZlX1je3as?t=1649) Run Cost as a Fitness Function

The ThoughtWorks Technology Radar proposed "run cost as a fitness function" — teams should understand how much money (or energy) their systems consume. This is an example of fitness functions working for modern digital-native organizations (where teams own their architectures) just as well as traditional organizations with central architecture functions.

## Books, Tools & Resources Mentioned

- **Building Evolutionary Architectures** (2nd edition) — Parsons, Ford, Kua (the book being discussed)
- **What Every Programmer Should Know About Object-Oriented Design** (1993) — the origin of connascence as a coupling vocabulary
- **The Checklist Manifesto** — Atul Gawande (analogy for fitness functions as automated checklists)
- **ArchUnit** — tool for encoding architectural constraints as tests
- **ThoughtWorks Technology Radar** — cited for "run cost as a fitness function"
- **The Software Architect Elevator** — Gregor Hohpe (referenced for the concept of architects riding the elevator between levels)
- **Domain-Driven Design** — Eric Evans (bounded contexts as the mechanism for controlling coupling scope)

---

*Source: [Building Evolutionary Architectures — Parsons, Ford & Lewis (GOTO Book Club 2023)](https://www.youtube.com/watch?v=m2ZlX1je3as)*

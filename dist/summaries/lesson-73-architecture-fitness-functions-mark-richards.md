---
podcast_url: https://developertoarchitect.com/lessons/lesson73.html
transcript_url: https://www.youtube.com/watch?v=HouuoLsHUAc
updated: 2026-03-27
---

# Lesson 73: Architecture Fitness Functions — Mark Richards

- **Speaker:** Mark Richards, Hands-on Software Architect & Founder of Developer to Architect
- **Series:** Software Architecture Monday
- **Published:** November 18, 2019
- **Duration:** ~10 minutes

## Key Takeaways

Architecture fitness functions are automated (or manual) objective measurements that guard architectural characteristics — scalability, performance, security, code quality — and fire when changes violate those characteristics, preventing architectural drift before it reaches production.

> - **Fitness functions are governance automation.** Rather than relying on code reviews or documentation, they encode architectural constraints as executable tests that run continuously or on every commit.
> - **Four dimensions classify any fitness function:** atomic vs. holistic scope; triggered vs. continuous execution; automated vs. manual collection; trend vs. threshold measurement.
> - **Simian Army is the canonical production-scale example** — Chaos Monkey, Latency Monkey, Security Monkey, Janitor Monkey, Chaos Gorilla, and Chaos Kong each target a different architectural characteristic at escalating blast radii.
> - **Cyclomatic complexity enforcement shows micro-scale power** — a fitness function blocking deployment of code with complexity > 30 stops bad practices at the source, regardless of which layer a developer tries to hide the code in.
> - **Trend-based fitness functions beat threshold-based ones** for production monitoring because they filter outliers and catch gradual degradation (e.g., alert when average response time increases 20% as user load grows 10%).
> - **Fitness functions enable evolutionary architectures** — the system can change continuously while still being verifiably aligned with its original architectural aims.

## Speaker Background

Mark Richards is a Boston-based hands-on software architect and the founder of [developertoarchitect.com](https://developertoarchitect.com). He has decades of experience designing and implementing distributed systems, microservices architectures, and enterprise software. He is co-author of *Fundamentals of Software Architecture* (O'Reilly, with Neal Ford) and *Software Architecture: The Hard Parts* (O'Reilly, with Neal Ford, Pramod Sadalage, and Zhamak Dehghani). His *Software Architecture Monday* free lesson series covers practical architecture patterns, techniques, and principles for developers making the transition to architect roles.

## Core Thesis

Architectural characteristics — scalability, performance, security, maintainability — erode silently over time as the codebase evolves. Architecture fitness functions give teams an **objective, repeatable mechanism to measure those characteristics** and detect violations automatically. Borrowed from evolutionary computing (where a fitness function scores how close a candidate solution is to its goal), the concept was formalized for software architecture in *Building Evolutionary Architectures* and provides the enforcement layer that makes evolutionary architecture practical rather than theoretical.

## Major Topics Discussed

### [[00:00:00]](https://www.youtube.com/watch?v=HouuoLsHUAc?t=0) Introduction and Definition

Mark opens with the formal definition from *Building Evolutionary Architectures*: **"An architecture fitness function provides an objective integrity assessment of some sort of architectural characteristic."** He emphasises two complementary ideas: the software architecture definition (objective measurement of a characteristic) and the evolutionary computing definition (a mathematical basis for measuring how close a design is to achieving its aims). Together they frame fitness functions as both a monitoring tool and a feedback loop.

### [[00:01:16]](https://www.youtube.com/watch?v=HouuoLsHUAc?t=76) The Travelling Salesperson Problem as a Teaching Example

Mark uses the classic TSP problem to make the abstract concept concrete before applying it to software. The fitness function chosen is **route length**. The key question becomes: *"How do changes to the routing algorithm affect the length of the route?"* He demonstrates:

- Baseline route length: 3,200 km
- After an algorithm change: 3,460 km → fitness function **fails**, change is rejected
- After adding a stop in Brussels: still 3,200 km → fitness function **passes**, change is accepted

This illustrates that fitness functions produce a binary signal (pass/fail) that integrates naturally into a CI pipeline.

### [[00:03:51]](https://www.youtube.com/watch?v=HouuoLsHUAc?t=231) Four Categories of Fitness Functions

Mark outlines the classification matrix from *Building Evolutionary Architectures*:

- **Atomic vs. Holistic** — Atomic targets a single isolated area (e.g., one service's response time); holistic targets the whole system (e.g., end-to-end throughput under load).
- **Triggered vs. Continuous** — Triggered fires on an event such as a commit or deployment; continuous runs perpetually in production.
- **Automated vs. Manual** — Most fitness functions should be automated, but some operational concerns (e.g., counting the number of system crashes) are difficult to automate reliably and may remain manual.
- **Trend vs. Threshold** — Threshold checks whether a metric exceeds a hard number; trend checks whether the metric is moving in the wrong direction relative to another variable. Mark explicitly prefers trend-based functions because they eliminate outliers and detect gradual drift.

### [[00:04:54]](https://www.youtube.com/watch?v=HouuoLsHUAc?t=294) The Netflix Simian Army — Production-Scale Fitness Functions

Mark walks through the Netflix Simian Army as a compelling real-world example of holistic, continuous, automated fitness functions operating in production:

- **Chaos Monkey** — randomly terminates services/servers to test system resilience, throughput, and recovery behaviour.
- **Latency Monkey** — injects random artificial latency into requests to verify that timeouts are handled gracefully and circuit breakers trip correctly. Mark calls this "one of my favourites" and notes it is an ideal way to test circuit breaker implementations (covered in his Lesson 13/15).
- **Security Monkey** — probes for security vulnerabilities and also scans for **expired TLS certificates**, a commonly overlooked operational concern.
- **Janitor Monkey** — watches for unused resources, marks them, and destroys services that remain idle, reclaiming capacity.
- **Chaos Gorilla** — takes down an entire availability **region** to test cross-region failover in production.
- **Chaos Kong** — the most aggressive member; takes down an entire **availability zone (data centre)**, testing the highest tier of disaster recovery.

The escalating blast radius — from single service to full availability zone — illustrates that fitness functions can operate at any level of the system.

### [[00:07:04]](https://www.youtube.com/watch?v=HouuoLsHUAc?t=424) Cyclomatic Complexity — Developer-Facing Code Quality Fitness Function

Mark demonstrates how fitness functions protect code quality, not just operational characteristics. A fitness function is configured to **fail any deployment where cyclomatic complexity exceeds 30** (i.e., too many nested conditionals). In the example:

- A developer writes a giant `if/else` chain to handle 50 US states in the backend → deployment blocked.
- The developer tries to move the same logic to the JavaScript frontend layer → deployment blocked again, because the fitness function covers both layers.

Mark quotes Glenn Vandenberg: *"Bad developers will move heaven and earth to do the wrong thing."* Fitness functions make it structurally impossible to do so, and the blocked deployment triggers a teaching moment where the architect introduces the **Strategy design pattern** as the correct solution.

### [[00:08:33]](https://www.youtube.com/watch?v=HouuoLsHUAc?t=513) Trend-Based Production Monitoring

Returning to the scalability topic from Lesson 71, Mark demonstrates a **trend-based holistic fitness function**: alert when average response time increases by 20% *correlated with* a 10% increase in concurrent users. This intersection-based measurement avoids false positives from isolated spikes and catches real scalability regression early in production.

### [[00:09:02]](https://www.youtube.com/watch?v=HouuoLsHUAc?t=542) Closing — Resources and Series Context

Mark closes by recommending *Building Evolutionary Architectures* and pointing to his broader training offerings at developertoarchitect.com, including private training in architecture and microservices.

## Books, Tools & Resources Mentioned

- **[Building Evolutionary Architectures](https://www.amazon.com/Building-Evolutionary-Architectures-Support-Constant/dp/1491986360)** — Neal Ford, Rebecca Parsons, Patrick Kua (O'Reilly). The book that introduced architecture fitness functions to the software architecture community. Mark recommends it highly.
- **Netflix Simian Army** — Netflix's open-source suite of resilience fitness functions including Chaos Monkey, Latency Monkey, Security Monkey, Janitor Monkey, Chaos Gorilla, and Chaos Kong.
- **Lesson 71 (Measuring Scalability)** — Earlier lesson in the same series, referenced for context on trend-based monitoring and scalability metrics.
- **Lesson 13/15 (Circuit Breakers)** — Referenced in the context of Latency Monkey as the correct mechanism Latency Monkey tests.
- **Lesson 139 (Triggered vs. Continuous Fitness Functions)** — A later lesson that builds directly on this one, going deeper on the triggered/continuous dimension.
- **[developertoarchitect.com](https://developertoarchitect.com)** — Mark's site hosting the full Software Architecture Monday lesson archive, private training, and conference schedule.

---

*Source: [Lesson 73: Architecture Fitness Functions — Mark Richards](https://www.youtube.com/watch?v=HouuoLsHUAc)*

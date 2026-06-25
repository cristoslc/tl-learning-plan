---
podcast_url: https://youtu.be/WRg13Ze_UpY
transcript_url: https://youtu.be/WRg13Ze_UpY
gist_url: https://gist.github.com/cristoslc/b5e3f764ac2ec9dde24442935f063d5b
updated: 2026-04-17
---

# Modern Architecture 101 for New Engineers & Forgetful Experts - Jerry Nixon

- **Guest:** Jerry Nixon, Microsoft Field Engineer & Computer Science Professor
- **Hosts:** NDC Conferences
- **Podcast:** NDC Copenhagen 2025
- **Published:** 2025-11-19

## Key Takeaways

> Simplicity is the best architecture. An architect's primary job is deciding what to leave out, not what to add in. Every component you introduce is a problem you will have to solve later.

- **"Best practice" is often a cover for lazy argument.** Real-world constraints — budget, team skill, politics, timelines — mean what works for Google or Twitter may be disaster for your company.
- **An architect is the one responsible for the most expensive choice** — the decision hardest to reverse, which must be made in advance and revisited continuously throughout a project.
- **Defer decisions as long as possible.** The less you build now, the cheaper it is to change your mind later.
- **You can argue every box off the diagram.** Understanding a component well enough to reject it is the real test of architectural maturity.

## Guest Background

Jerry Nixon is a Microsoft field engineer on the SQL Server team, where he also works with the Data API Builder (DAB) team. He spent roughly a decade as a Microsoft developer evangelist and then years as a field engineer working with Microsoft's top 15 customers (the "F-15"). He is also a computer science professor at a university in Colorado, where he sees firsthand how overwhelming the modern software landscape is for new developers.

## Core Thesis

Nixon argues that modern software architecture is not about adopting every available technology — it is about understanding each component well enough to justify including it or, more importantly, excluding it. He walks through a full reference architecture piece by piece, showing that each addition solves a real problem but also introduces new complexity. The architect's soul is simplicity: minimize what you build, defer what you can, and say no early and often.

## Major Topics Discussed

### [[00:00:00]](https://youtu.be/WRg13Ze_UpY?t=0) There Is No Such Thing as a Best Practice

Nixon opens by challenging the phrase "best practice." Large companies like Twitter can afford incredible mistakes and pay their way out; your company cannot. What works at massive scale is not a universal prescription. Architecture practices evolve — spaghetti code (90s), multi-tier lasagna (2000s), microservices ravioli (2010s) — and all of them still work today in the right context. Architecture-shaming someone for using VB when their entire org runs on VB misunderstands the realities they face.

### [[00:09:01]](https://youtu.be/WRg13Ze_UpY?t=541) What Is an Architect?

An architect is the person responsible for the most expensive decision — the one that is costliest to change later and must be made in advance. Since every moment in a project is "now," this role persists throughout the entire lifecycle. More importantly, an architect's primary role is to figure out what must be **left out** of a solution. Every addition increases complexity; the less you have, the less there is to break.

### [[00:11:01]](https://youtu.be/WRg13Ze_UpY?t=661) The Tsunami of Architectural Choices

From source control to CI/CD, cloud provider, containers, serverless, language, frontend framework, backend framework, AI model, database, UI layout, delivery, packaging, telemetry, accessibility — the sheer volume of decisions an architect faces is overwhelming. Nixon emphasizes that you are not expected to make all of these at once. Defer them.

### [[00:14:54]](https://youtu.be/WRg13Ze_UpY?t=894) The Client and the Database

Every project starts with a client and a database. Nixon advocates separating them — having the client talk directly to a database leaks schema, couples concerns, and forces app developers to be good SQL developers. Introduce an API to abstract the database away.

### [[00:17:40]](https://youtu.be/WRg13Ze_UpY?t=1060) Move the API Next to the Database

Relocating the API from the client to the server removes database drivers from the client entirely. Database drivers are "nothing but trouble" — they require versioning, security updates, and regular upgrades. Server-side APIs also enable independent delivery cadences as long as the contract is maintained. Full telemetry (especially OpenTelemetry) should be planned upfront, not bolted on last.

### [[00:20:37]](https://youtu.be/WRg13Ze_UpY?t=1237) CQRS: Separate Read and Write Operations

Splitting the API into read and write operations is a "cheap and easy first step" to better performance. Write-heavy applications can scale their write path independently, while read operations run on a separate container or server. This pattern also extends to the database itself — use a read replica (available in every major database) so that read queries never impact write throughput.

### [[00:23:06]](https://youtu.be/WRg13Ze_UpY?t=1386) Eventual Consistency Is Inevitable

You cannot increase the speed of light. Read replicas introduce a slight delay — eventual consistency. If you do simultaneous read and write calls, the read will not yet reflect the write. This is a tradeoff worth accepting because the performance gains are so significant for such low technical effort.

### [[00:25:02]](https://youtu.be/WRg13Ze_UpY?t=1502) Services and the Service Bus

Breaking a monolithic API into services (micro or macro) enables isolated development, deployment, and upgrades. But services need to communicate — enter the service bus. The service bus is like a postman that routes messages between services, with features like timers, return-to-sender, and dead-letter handling. It also becomes the lever for integrating with existing systems (A, B, C, D) across the enterprise. You must also manage the dead-letter box — messages that fail to deliver.

### [[00:28:40]](https://youtu.be/WRg13Ze_UpY?t=1720) The API Manager (APIM)

An API Manager sits between the client and the API. It handles versioning transitions (v1 to v2, payload transformation), denial of service protection, load balancing, and makes multiple microservices feel like a single API surface. Nixon says if you have APIs and no APIM, "you're doing it wrong." It is painful to add retroactively but invaluable when you need to version an API without the original architect around.

### [[00:32:02]](https://youtu.be/WRg13Ze_UpY?t=1922) Caching: Level 1 and Level 2

- **Level 1 (in-memory):** Cache API responses in process memory. Even a single second of cache transforms API capacity. Eliminates stampeding (thousands of identical requests hitting the database simultaneously).
- **Level 2 (Redis/key-value):** Offload expensive query results to a fast key-value store. Redis avoids joins and complex lookups — single-index lookups are extremely fast.

Nixon recommends libraries like FusionCache (maintained by Jody, who also presented at NDC) for easy implementation.

### [[00:35:25]](https://youtu.be/WRg13Ze_UpY?t=2125) Retry Policy

In the real world, databases sometimes fail to respond due to network hiccups, not actual outages. A retry policy with exponential backoff (Nixon uses 5 retries) is a simple, non-exotic addition that prevents cascade failures.

### [[00:36:20]](https://youtu.be/WRg13Ze_UpY?t=2180) Queues

If your database can handle 100 operations but your API receives 1,000, a persisted queue smooths the spikes. Requests that cannot be processed immediately are queued and handled when capacity is available. The user gets an immediate "received" acknowledgment — the same pattern Outlook and most modern apps use. This is not suitable for credit card transactions but works for the vast majority of operations.

### [[00:39:44]](https://youtu.be/WRg13Ze_UpY?t=2384) Event Hubs and Change Data Capture

An event hub ingests database change events (e.g., SQL Server's change event streaming) and routes them to serverless functions or other handlers. This replaces polling — instead of asking "did anything change?" repeatedly (which slows the database), the database pushes changes to the event hub. The event hub can also push updates back to the client via WebSockets, eliminating the user's urge to hit F5.

### [[00:44:00]](https://youtu.be/WRg13Ze_UpY?t=2640) Static Content and CDN

Static assets (images, unchanged resources) should bypass application middleware entirely — drop them in a folder or use a dedicated static server. A CDN makes content faster for international users by caching closer to them. No cloud tier can beat the speed of light; a CDN is the practical workaround.

### [[00:45:50]](https://youtu.be/WRg13Ze_UpY?t=2750) Database Performance: Column Store, In-Memory Tables, No-Index Tables, and Graph

- **Column store:** A checkbox on a table that stores data vertically instead of horizontally. ~100x faster for aggregates and dramatically compresses data. Same SQL syntax — transparent to the developer.
- **No-index (hash) tables:** The absolute fastest way to write to a database — no index updates, no reordering. Also the most dangerous, stripping away all relational constraints. Use with extreme caution.
- **In-memory tables:** Tables stored in RAM with full transactional semantics. Reading is lightning-fast. Two modes: pure in-memory (lost on recycle) or memory + disk persistence (slightly slower writes, still insanely fast reads).
- **Graph databases:** SQL Server supports graph queries (MATCH across relationships) for scenarios like logistics and routing without moving data out of the relational database.

### [[00:53:01]](https://youtu.be/WRg13Ze_UpY?t=3181) Data API Builder (DAB)

Nixon's team ships Data API Builder — open source, free, supporting PostgreSQL, SQL Server, Cosmos DB, and MySQL. It replaces the repetitive "File New Project → Web API → Entity Framework" pattern that he calls "copy-and-paste inheritance." DAB also provides GraphQL endpoints and ships as a container.

### [[00:54:06]](https://youtu.be/WRg13Ze_UpY?t=3246) AI Integration: MCP Servers

AI models should not directly access databases. Instead, a remote MCP (Model Context Protocol) server sits between the model and the API, giving the AI controlled access to application data. Nixon strongly cautions against allowing models to generate and execute raw SQL against your database.

### [[00:55:06]](https://youtu.be/WRg13Ze_UpY?t=3306) Offline-First Client: Cache and Queue

Adding a cache and queue to the client gives users an Outlook-like offline experience — tunnel or internet outage does not interrupt work. Cache responses, queue requests, and sync when connectivity returns. Simple to add, transformative for user experience.

### [[00:56:16]](https://youtu.be/WRg13Ze_UpY?t=3376) Data Lake and ML

Enterprise data from all systems should flow into a data lake (ETL/ELT) for unified reporting and ML operations. But ML results must flow back into operational systems, not just dashboards — otherwise the intelligence never reaches the customer experience.

### [[00:57:55]](https://youtu.be/WRg13Ze_UpY?t=3475) Security: JWT and Fine-Grained Access Control

Nixon briefly covers JWT (JSON Web Tokens) from identity providers like Microsoft Entra ID. He recommends that high-level role categories live in the identity tenant, while fine-grained application-level access control is handled by the application itself, which rewrites the JWT with app-specific claims. This avoids polluting the tenant with application-specific roles while keeping security robust. He warns this is also one of the most dangerous things to get wrong.

## Books, Tools & Resources Mentioned

- **FusionCache** — .NET caching library with level 1 and level 2 support (maintained by Jody)
- **Redis** — Level 2 key-value cache
- **Polly** — .NET resilience/retry library
- **OpenTelemetry** — Cross-platform telemetry standard
- **Azure Service Bus** — Message routing between services
- **Azure Event Hubs** — High-throughput event ingestion
- **Azure API Management (APIM)** — API gateway, versioning, and load balancing
- **Data API Builder (DAB)** — Open-source auto-API for PostgreSQL, SQL Server, Cosmos DB, MySQL
- **SQL Server Column Store** — ~100x faster aggregates via vertical storage
- **SQL Server In-Memory OLTP** — RAM-backed tables with transactional semantics
- **SQL Server Graph DB** — MATCH queries for relationship traversal
- **Microsoft Entra ID** (formerly Azure AD) — Identity and JWT issuance
- **MCP (Model Context Protocol)** — AI model integration with application APIs

---

*Source: [Modern Architecture 101 for New Engineers & Forgetful Experts](https://youtu.be/WRg13Ze_UpY)*
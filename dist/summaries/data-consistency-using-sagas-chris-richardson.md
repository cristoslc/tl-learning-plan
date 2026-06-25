---
podcast_url: https://www.youtube.com/watch?v=YPbGW3Fnmbc
transcript_url:
updated: 2026-03-28
---

# Data Consistency in Microservices Using Sagas — Chris Richardson

- **Speaker:** Chris Richardson, microservices consultant, author of *Microservice Patterns*
- **Event:** Devoxx
- **Format:** Conference talk
- **Duration:** ~49 minutes

## Key Takeaways

In a microservice architecture, each service owns its data — which means ACID transactions can't span services. Sagas replace distributed transactions with a sequence of local transactions coordinated through asynchronous messaging.

> 1. **Database-per-service is non-negotiable** — sharing a database couples services, defeats autonomous teams, and makes schema changes a coordination nightmare. The only way services can access each other's data is through APIs.
> 2. **Two-phase commit is dead for microservices** — distributed transactions require all participants to be available, hold locks, and use compatible technology. Modern databases and message brokers often don't even support them.
> 3. **A saga is a sequence of local transactions** — instead of one distributed ACID transaction, break it into ordered steps. Each step commits locally, then triggers the next step via messaging.
> 4. **Compensating transactions replace rollback** — there's no automatic undo. If step N+1 fails, you must explicitly undo steps 1 through N. This requires thinking through every failure scenario and its business-level compensation.
> 5. **Orchestration beats choreography** — choreography scatters saga logic across services; an explicit saga orchestrator (a state machine) centralizes coordination, making the flow visible and the services unaware of each other.
> 6. **Transactional messaging is the foundation** — use the outbox pattern: write messages to a database table in the same local transaction as your data changes, then publish to a message broker via polling or transaction log tailing.

## Speaker Background

Chris Richardson is a software architect and author of *Microservice Patterns* (Manning) and the earlier *POJOs in Action*. He created an early PaaS (Cloud Foundry, acquired by SpringSource/VMware) and runs microservices.io, a comprehensive resource on microservice architecture patterns. He consults and trains organizations worldwide on microservice architecture, with deep experience in the transactional challenges of distributed systems.

## Core Thesis

The microservice architecture breaks the simple ACID transaction model we've relied on for decades. When data is encapsulated per service, cross-service transactions require a new model: sagas — sequences of local transactions coordinated through reliable asynchronous messaging. Sagas sacrifice automatic rollback and full isolation for the autonomy, loose coupling, and scalability that microservices demand. The trade-off is manageable but requires explicit design of compensating transactions, pending states, and transactional messaging infrastructure.

## Major Topics Discussed

### [[00:04:00]](https://youtu.be/YPbGW3Fnmbc?t=240) The Problem: From Monolith to Microservices

In a monolith, enforcing a business invariant (e.g., order totals can't exceed customer credit limit) is trivial: one transaction, one database, begin-commit-done. In microservices, orders belong to one service and customers to another — each with private data. You can't just SELECT across them in one transaction anymore. This is the fundamental tension: encapsulated data gives you loose coupling, but cross-cutting business rules need coordination.

### [[00:13:30]](https://youtu.be/YPbGW3Fnmbc?t=810) Why Distributed Transactions Don't Work

Two-phase commit (2PC/XA) has fallen out of favor: coordinator is a single point of failure, chatty protocol, locks held during voting, limited isolation levels, and — critically — many modern technologies (NoSQL databases, message brokers) don't support them at all. CAP theorem pushes toward availability over consistency. "We're using sagas to avoid 2PC, so we can't use 2PC as part of the implementation of a saga."

### [[00:15:02]](https://youtu.be/YPbGW3Fnmbc?t=902) The Saga Pattern

Originally from a 1987 paper, adapted for microservices. Instead of one distributed transaction spanning services A, B, C, you have a saga with three local transactions: T1 in A, T2 in B, T3 in C. Each commits independently and triggers the next step. If T2 fails, compensating transaction C1 undoes T1's effects. Example: create order -> reserve credit -> approve/reject order.

### [[00:18:18]](https://youtu.be/YPbGW3Fnmbc?t=1098) Compensating Transactions

There's no automatic rollback — you must program every undo path. Example: bank transfer debits account A, then finds account B is closed. Compensating transaction credits back to A. But what if A is also now closed? "Some higher-level business process has to kick off at that point." This is genuinely more complex than ACID rollback and requires thinking through all failure scenarios with domain experts.

### [[00:22:00]](https://youtu.be/YPbGW3Fnmbc?t=1320) API Design Implications

Two options when the saga is triggered by an HTTP request:
1. **Wait for saga completion** — simpler API semantics but reduces availability (all participants must be up)
2. **Return immediately** — return order ID with "pending" status, client polls or gets websocket notification. Better availability, but more complex client. Richardson prefers option 2: "You just want loosely coupled, highly available systems."

### [[00:26:33]](https://youtu.be/YPbGW3Fnmbc?t=1593) Isolation Anomalies and Pending States

Since each saga step commits immediately, other transactions can see intermediate (inconsistent) state. An order exists in "pending" state before credit is verified. What if a cancel request arrives while the create-order saga is still running? Do you interrupt the saga or wait for it to complete? "There are some really interesting design issues... the inconsistent data is actually exposed to other transactions while sagas are completing."

### [[00:28:50]](https://youtu.be/YPbGW3Fnmbc?t=1730) Choreography vs. Orchestration

**Choreography:** saga participants figure out what to do amongst themselves by subscribing to each other's events. Logic is scattered; creates cyclic dependencies.

**Orchestration:** a dedicated saga orchestrator (state machine) tells participants what to do via commands and processes their replies. Cleaner separation of concerns. Can be implicit (order object drives its own saga) or explicit (separate CreateOrderSaga object). Richardson demonstrates a simple DSL for defining saga state machines declaratively.

### [[00:39:01]](https://youtu.be/YPbGW3Fnmbc?t=2341) Transactional Messaging — The Outbox Pattern

The underlying infrastructure that makes sagas reliable. Problem: updating the database and sending a message must be atomic, but you can't use 2PC. Solution: insert messages into an "outbox" table in the same local ACID transaction as data changes. Then publish to the message broker via:
- **Polling** — periodically SELECT from the outbox table (works at high scale, but has latency and message-ordering edge cases)
- **Transaction log tailing** — monitor the database's commit log (MySQL binlog, DynamoDB streams, MongoDB oplog) for changes to the outbox table (Richardson's preferred approach, but database-specific)

## Books, Tools & Resources Mentioned

- **Microservice Patterns** — Chris Richardson (Manning; chapters on sagas, transactional messaging)
- **"Sagas" paper (1987)** — Hector Garcia-Molina & Kenneth Salem (the original saga concept for long-running transactions)
- **microservices.io** — Richardson's pattern catalog
- **Eventuate** — Richardson's platform for transactional business applications with microservices
- **MySQL binlog replication** — used for transaction log tailing
- **DynamoDB Streams, MongoDB oplog** — other database-specific change capture mechanisms

---

*Source: [Data Consistency in Microservices Using Sagas — Chris Richardson (Devoxx)](https://www.youtube.com/watch?v=YPbGW3Fnmbc)*

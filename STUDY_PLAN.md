# Ten-Week Integrated Study Plan

Assumption: 8–10 hours per week. With 4–5 hours, stretch each week into two.
Each week ends with one timed mock and a short written retrospective.

| Week | Core concepts | HLD case study | LLD / build exercise | Deliverable |
|---|---|---|---|---|
| 1 | Requirements, estimation, APIs, data models, OOP, SOLID | URL shortener | LRU cache | Design packet + tested cache |
| 2 | DNS, CDN, L4/L7, proxies, caching, Go concurrency | Rate limiter | Token bucket + sliding window | Load path and race-safe limiter |
| 3 | SQL/NoSQL, indexes, replication, consistency | Key-value store | In-memory file system | Read/write paths + persistence choices |
| 4 | Sharding, consistent hashing, queues, delivery semantics | Notification system | Extensible notification framework | Retry/dedupe design + adapters |
| 5 | Fan-out, counters, hot keys, event-driven systems | Social feed | Splitwise | Feed trade-off matrix + invariants |
| 6 | Streaming, object storage, media pipelines, backpressure | YouTube/Netflix | Task scheduler | Capacity model + worker implementation |
| 7 | WebSockets, presence, ordering, geo-indexes | WhatsApp or Uber | Elevator or ride matching | Stateful service design + mock |
| 8 | Transactions, ledgering, idempotency, Saga | Payment gateway | Order book or vending machine | Money invariants + failure tests |
| 9 | Search, RAG, embeddings, ranking, permissions | Document Q&A | RAG pipeline | Retrieval evaluation + citations |
| 10 | Inference, model gateways, agents, durable workflows | AI assistant / gateway | Tool runner | Full mock loop + gap-closing review |

## Session protocol

### Concept session (60 minutes)

1. Spend 10 minutes recalling the topic without notes.
2. Study for 30 minutes and draw the read/write or request path.
3. Spend 15 minutes answering the note's review questions.
4. Capture one unresolved question and one concrete trade-off.

### HLD practice (45 minutes + 15-minute review)

- 0–5: clarify functional/non-functional requirements.
- 5–10: estimate scale; declare assumptions.
- 10–15: API and data model.
- 15–30: architecture and critical flows.
- 30–38: bottlenecks, failures, consistency, security.
- 38–45: trade-offs, evolution, and summary.

### LLD practice (45 minutes + tests)

- 0–5: use cases, constraints, and invariants.
- 5–12: entities, value objects, and responsibilities.
- 12–18: interfaces and relationships.
- 18–35: implement the core happy path.
- 35–45: edge cases, concurrency, and extensibility.

## Spaced repetition

Review each design after 1 day, 1 week, and 3 weeks. On review, redraw it from
memory, then compare. Do not merely reread. A topic is “green” only after two
successful closed-note explanations.

## Assessment rubric (100 points)

- Requirements and scope: 10
- Estimation and constraints: 10
- API and data model: 15
- Architecture / class responsibilities: 20
- Critical flows and correctness: 15
- Scale, concurrency, and failure handling: 15
- Trade-offs and communication: 10
- Security and observability: 5

Aim for 70 by week 4, 80 by week 7, and 85+ in two consecutive final mocks.


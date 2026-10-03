# HLD Interview Framework

## 1. Clarify the problem

Turn a broad prompt into a contract. Identify actors, three to five core use
cases, explicit exclusions, scale, latency/availability targets, consistency,
retention, privacy, and geography. Confirm which path matters most.

Useful questions:

- Who creates data, who reads it, and who administers it?
- Is the workload read-heavy, write-heavy, bursty, or globally distributed?
- What must never happen? What can be temporarily stale?
- What is the latency target at p50 and p99?
- What is out of scope for this interview?

## 2. Estimate the dominant constraints

Use orders of magnitude. With `DAU`, actions per user per day, peak factor, item
size, and retention:

```text
average QPS = DAU × actions/day ÷ 86,400
peak QPS    = average QPS × peak factor
storage     = writes/day × bytes/write × retention days × replication factor
bandwidth   = QPS × response bytes
```

State assumptions. The goal is to expose the bottleneck, not fake precision.

## 3. Define contracts and ownership

Write the public API/event contracts and identify the source of truth for each
entity. Include identifiers, pagination, idempotency keys, versioning, error
semantics, and authorization boundaries. Prefer cursor pagination for mutable,
large collections.

## 4. Draw the high-level system

Start with the minimum viable path:

```text
client → edge/LB → stateless API → source-of-truth database
                         ├─ cache
                         └─ durable queue → async workers → derived stores
```

Do not add components without naming the requirement they satisfy.

## 5. Trace critical flows

Trace one write and one read. At every hop ask: timeout? retry? duplicate?
partial failure? ordering? overload? stale data? Define transaction boundaries
and what the client observes.

## 6. Deep dive and evolve

Select the dominant issue: partitioning, hot keys, consistency, fan-out, search,
media processing, geo-routing, or cost. Explain the simple design first, its
breaking point, and the next evolution.

## 7. Close well

Summarize requirements met, deliberate compromises, largest remaining risk,
metrics/SLOs, security controls, and the first future improvement.

## Common failure modes

- Architecture before requirements.
- A component shopping list without request/data flows.
- “Use NoSQL/Kafka/microservices” without workload-based justification.
- Ignoring retries, duplicates, hot partitions, deletion, or regional failure.
- Claiming CAP means choosing only two properties at all times. CAP describes
  behavior during a network partition; normal-operation latency/consistency is
  a separate choice.

## Active-recall questions

1. What five questions most change your design?
2. How do peak QPS and stored bytes lead to different bottlenecks?
3. Where should idempotency live, and how long should its records persist?
4. How would the design degrade when a cache, queue, or region fails?


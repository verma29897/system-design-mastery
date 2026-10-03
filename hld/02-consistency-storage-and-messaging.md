# Consistency, Storage, and Messaging

## Consistency vocabulary

- **Linearizable:** each operation appears atomic and respects real time.
- **Sequential:** all clients agree on an order, but it need not match real time.
- **Read-your-writes:** a client observes its completed writes.
- **Monotonic reads:** a client never moves backward to an older version.
- **Eventual:** replicas converge if updates stop.

Define consistency per operation. Payments may require a strongly consistent
ledger while status/search views are eventually consistent.

## CAP without the slogan

When a network partition prevents nodes from communicating, a replicated system
must either reject/delay some operations to preserve consistency or accept them
and risk divergent views. Partition tolerance is not normally optional in a
distributed system. PACELC adds the everyday trade-off: else, latency versus
consistency.

## SQL versus NoSQL

Choose from access patterns and invariants:

| Need | Usually favor |
|---|---|
| Multi-row constraints, joins, transactions | Relational database |
| Key-based access, flexible shape, horizontal partitioning | Key-value/document |
| Huge sequential writes and range scans | LSM-oriented store |
| Relationship traversal | Graph model (when traversal dominates) |
| Full-text relevance | Search index as a derived store |

The data model matters more than the label. Avoid dual sources of truth.

## Indexes

B-trees serve point lookups and ordered ranges with predictable reads. LSM trees
buffer and merge writes, improving write throughput at the cost of compaction
and read/write amplification. Every secondary index accelerates reads but adds
write, storage, and consistency cost.

## Replication and partitioning

- Leader/follower simplifies ordering; leader failover and replica lag matter.
- Multi-leader helps multi-region writes but creates conflict resolution.
- Leaderless quorum systems trade tunable availability and consistency.
- Hash sharding spreads load; range sharding supports scans but risks hotspots.
- Directory sharding enables placement control but adds routing metadata.

Consistent hashing reduces movement during membership changes, but virtual nodes,
load-aware placement, replication, and hot-key mitigation are still required.

## Messaging semantics

At-most-once may lose work. At-least-once may duplicate work. “Exactly once” is
usually an end-to-end effect: durable input, atomic state transition, stable
idempotency key, deduplication record, and safe output publication (often an
outbox). Consumers should tolerate redelivery.

## Review questions

1. Which invariant needs strong consistency and which views may lag?
2. What happens during replica failover?
3. How are partitions rebalanced without overload?
4. What makes an event consumer idempotent?


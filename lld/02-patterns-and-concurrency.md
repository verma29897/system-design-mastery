# Patterns and Concurrent Components

## Choose patterns from pressure

| Pressure | Candidate pattern |
|---|---|
| Select interchangeable policy | Strategy |
| Behavior changes by lifecycle state | State |
| Translate provider/domain contracts | Adapter |
| Add responsibilities around a component | Decorator |
| Hide a complicated subsystem | Facade |
| Notify independent listeners | Observer / events |
| Encapsulate queued/retriable work | Command |
| Ordered processing pipeline | Chain of Responsibility |
| Complex validated construction | Builder |

Patterns have costs: indirection, more types, debugging complexity, and sometimes
weaker compile-time visibility. Use the simplest design that supports the known
variation.

## Concurrent component checklist

- Define owned state and invariants.
- Choose mutex, RWMutex, atomic, channel ownership, or immutability intentionally.
- Specify blocking, cancellation, timeout, and shutdown semantics.
- Bound queues and goroutine creation.
- Avoid lock-order cycles and callbacks under locks.
- Make retries/idempotency explicit.
- Test races, cancellation, overload, and clock-sensitive behavior.

## Component notes

**LRU cache:** map gives O(1) lookup; doubly linked list gives O(1) recency moves
and tail eviction. One mutex can protect the compound invariant. Sharding reduces
contention but makes a globally exact LRU difficult.

**Rate limiter:** token bucket permits controlled bursts; sliding-window log is
accurate but expensive; sliding-window counter approximates with bounded state.
Distributed limiters need atomic state updates, clock assumptions, partition
policy, and a fail-open/fail-closed decision.

**Scheduler:** priority queue orders `runAt`; a timer wakes the dispatcher; a
bounded worker pool executes. Cancellation and rescheduling require identity and
state transitions. Persist jobs before acknowledging if restart survival matters.

**Order book:** maintain price ordering and FIFO within price. Match atomically;
emit fills after the book transition using an outbox or event log. Use integer
minor units/decimal representation, never binary floating point for money.


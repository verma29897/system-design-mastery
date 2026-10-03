# Curriculum Review

## What the original curriculum does well

- It covers the core distributed-systems toolbox and a strong set of interview
  case studies.
- HLD progresses from primitives to complete products.
- LLD includes concurrency and not just design-pattern vocabulary.
- AI systems are treated as production systems: routing, streaming, retrieval,
  permissions, evaluation, cost, and reliability all appear.

## Improvements made here

1. **Integrate HLD and LLD.** Studying related designs in the same week improves
   transfer: distributed rate limiting pairs with an in-process rate limiter;
   notification architecture pairs with channel/provider abstractions.
2. **Practice estimation from week 1.** QPS, storage, bandwidth, fan-out, and
   latency budgets are habits rather than a single lecture.
3. **Introduce reliability before large case studies.** Timeouts, idempotency,
   retries, backpressure, overload, observability, and graceful degradation are
   evaluated in every design.
4. **Use patterns as consequences, not goals.** Start with change points and
   invariants; name Strategy, State, Adapter, or Observer only after the design
   earns it.
5. **Add explicit artifacts.** Every problem produces requirements, estimates,
   APIs, a data model, a diagram, failure analysis, and trade-offs.
6. **Use progressive mocks.** Short mocks begin in week 2; waiting until the end
   hides communication and time-management problems.
7. **Separate delivery semantics.** “Exactly once” is framed as an end-to-end
   business effect built from durable state, idempotency, deduplication, and
   atomic boundaries—not a magic broker setting.
8. **Add security and operability.** Authentication, authorization, tenant
   isolation, abuse controls, privacy, SLOs, metrics, logs, and traces are
   standard design dimensions.

## Exit criteria

You are ready for interviews when you can consistently:

- clarify scope and define success metrics in under 5 minutes;
- estimate load and identify the dominant constraint;
- produce coherent APIs, data ownership, and a high-level architecture;
- trace critical writes and reads, including failures and retries;
- explain two meaningful trade-offs without hand-waving;
- adapt when an interviewer changes scale, consistency, or product requirements;
- implement a thread-safe LLD core with focused tests in 35–45 minutes.


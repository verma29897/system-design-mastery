# Networking, Caching, and Reliability

## Request path

DNS locates an endpoint; a CDN serves cacheable content near users; L4 load
balancing routes connections; L7 load balancing routes HTTP/gRPC requests by
host, path, headers, or policy; a reverse proxy terminates protocols and shields
services. Each layer needs timeouts, health checks, capacity, and observability.

## Caching patterns

- **Cache-aside:** application reads cache, falls back to DB, then fills cache.
- **Write-through:** write cache and backing store synchronously.
- **Write-back:** acknowledge cache first and persist later; fast but risks loss.
- **Refresh-ahead:** renew hot entries before expiry.

TTL limits staleness but does not guarantee freshness. Plan for stampedes using
request coalescing, jittered TTLs, stale-while-revalidate, and admission limits.
Prevent penetration with validation, negative caching, or Bloom filters. A cache
is a performance layer unless its durability semantics are explicitly designed.

## Reliability toolbox

- Timeouts bound resource occupation and must shrink across downstream calls.
- Retry only transient failures, with exponential backoff and jitter.
- Retry budgets prevent amplification during incidents.
- Circuit breakers stop calls to a failing dependency and probe recovery.
- Bulkheads isolate pools/queues so one dependency cannot consume everything.
- Backpressure rejects, queues within bounds, or sheds lower-priority work.
- Idempotency makes ambiguous retries safe.

## Observability

Start from user-visible SLOs. Track request rate, errors, latency percentiles,
saturation, queue age, retry volume, cache hit rate, replication lag, and business
correctness. Logs explain events; metrics reveal trends; traces connect a request
across boundaries. Alerts should be actionable and tied to symptoms/burn rate.

## Failure drill

For each dependency, answer: how detected, timeout, fallback, retry owner,
duplicate handling, backlog limit, data reconciliation, and customer impact.


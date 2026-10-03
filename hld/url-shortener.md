# URL Shortener — Worked Study Outline

This is a compact reference, not a script to memorize. Complete a closed-note
attempt before reading it.

## Scope and assumptions

Core: create a short link and redirect it. Optional: custom alias, expiry,
disable/delete, and asynchronous click analytics. Assume 100 million new links
per month, 100:1 redirect-to-create ratio, five-year retention, p99 redirects
under 100 ms, high redirect availability, and no requirement for immediate
analytics.

## Estimates

```text
writes/s average ≈ 100,000,000 ÷ (30 × 86,400) ≈ 39
reads/s average  ≈ 3,900; use 10× peak ≈ 39,000
links retained   ≈ 6 billion before expiry/deletion
key space        = base62^7 ≈ 3.5 trillion
```

Storage calculations must include the full record and indexes, not only the URL.
The dominant path is read latency and availability rather than write throughput.

## API

```http
POST /v1/links
Idempotency-Key: <client-generated-key>
{"url":"https://example.com/long","customAlias":null,"expiresAt":null}

201 {"code":"aZ91Kp2","shortUrl":"https://sho.rt/aZ91Kp2"}

GET /aZ91Kp2
302 Location: https://example.com/long
```

Use `302` when destinations may change or click tracking must see repeat visits;
`301` allows stronger browser caching but reduces server visibility/control.
Validate schemes and block abusive destinations according to product policy.

## Data and ID generation

```text
Link(code PK, destination, owner_id, created_at, expires_at, status, version)
Idempotency(owner_id + key PK, request_hash, result_code, expires_at)
ClickEvent(event_id, code, timestamp, coarse_geo, referrer, user_agent_class)
```

Two reasonable code strategies:

- Allocate a globally unique numeric ID and base62-encode it. Collision-free,
  compact, but requires a scalable allocator and may expose sequence information.
- Generate random codes and conditionally insert. Decentralized and opaque, but
  requires collision retry and enough entropy.

Hashing the URL alone mishandles collisions and prevents distinct links for the
same destination with different owners, expirations, or analytics.

## Architecture and flows

```text
Create: client → API → ID/code → primary link store → cache fill → response
Read:   client → edge/LB → redirect service → cache → link store → 302
                                        └→ event queue → analytics consumers
```

Redirect services are stateless. Cache by code with TTL bounded by link expiry;
negative-cache missing codes briefly. Analytics emission must not delay the
redirect. If the queue is unavailable, choose explicitly between dropping sampled
analytics and a bounded local buffer—never allow unbounded memory growth.

## Scaling and correctness

- Shard the link store by hash(code) for even placement.
- Replicate across failure domains; define whether stale replicas may briefly
  redirect a just-disabled link.
- Protect hot links with CDN/edge caching and request coalescing.
- Use cache versioning/invalidation for edits and disable operations.
- Make create retries safe with an idempotency record bound to request content.
- Rate-limit creation, detect malware/phishing, and prevent open-redirect abuse.

## Observability

Track redirect success, p50/p99 latency, cache hit rate, missing/expired rate,
store/replica errors, queue lag/drop rate, creation collisions, and abuse blocks.

## Trade-off prompts

1. What changes if links must be globally disabled within one second?
2. How do custom aliases affect partitioning and uniqueness?
3. What if one celebrity link receives one million requests per second?
4. How do deletion/privacy requirements propagate to analytics?


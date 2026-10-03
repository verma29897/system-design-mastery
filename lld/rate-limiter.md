# Rate Limiter

Expose `Allow(ctx, key, cost)` with deterministic clock injection. Implement token
bucket and optionally sliding counter as strategies. Protect compound state and
bound inactive-key memory. Test refill boundaries, bursts, clock movement,
concurrency, cancellation, and cleanup. Document whether failures allow or reject.


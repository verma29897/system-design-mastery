# Distributed Rate Limiter

Design per-user, per-tenant, and global limits at an API gateway. Compare token
bucket, fixed window, sliding log, and sliding counter. Define limit keys,
burst size, refill rate, atomic updates, clock behavior, response headers, and
fail-open versus fail-closed policy. Deep dives: Redis/Lua, local token leasing,
hot tenants, multi-region accuracy, configuration rollout, and abuse resistance.

Drill: preserve low latency at one million checks/s while keeping overshoot
bounded during partitions. Explain what “bounded” means numerically.


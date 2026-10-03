# Distributed Task Scheduler

Define one-time/recurring/delayed tasks, cancellation, priority, retries, and
execution guarantees. Persist tasks, partition by schedule time/tenant, lease due
work to bounded worker pools, heartbeat long jobs, reclaim expired leases, and
make handlers idempotent. Control noisy neighbors and retry storms.

Drill: recover from scheduler failover without silently losing or concurrently
executing the same non-idempotent job.


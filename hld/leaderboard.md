# Leaderboard and Distributed Counters

Support score updates, rank lookup, top-k, nearby ranks, seasons, and tie rules.
Compare Redis sorted sets, sharded ordered structures, and batch/stream materialized
views. Define atomic increments, dedupe keys, reconciliation with a source-of-truth
event log, hot-key mitigation, and season rollover.

Drill: provide global top 100 and exact user rank at high write volume while
making duplicate score events harmless.


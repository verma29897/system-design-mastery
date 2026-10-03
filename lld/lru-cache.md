# LRU Cache

Combine a hash map with a doubly linked list for O(1) get, put, recency move, and
tail eviction. Define zero-capacity and update semantics. One mutex protects the
map/list invariant; tests cover eviction order, replacement, concurrency, and race
detection. Extension drill: weighted capacity or TTL without breaking O(1) goals.


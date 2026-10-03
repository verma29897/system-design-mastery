# Payment Gateway

Define payment intent, authorization, capture, refund, webhook, reconciliation,
and ledger semantics. Use integer minor units, immutable double-entry entries,
idempotency keys, provider adapters, transactional outbox, and explicit state
transitions. A Saga coordinates external steps; it does not replace ledger truth.

Drill: resolve an ambiguous provider timeout safely and explain how reconciliation
repairs divergence without double-charging.


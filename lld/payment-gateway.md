# Payment Gateway

Model PaymentIntent, Attempt, Refund, Money, LedgerEntry, Provider, and state
machine. Adapter isolates provider differences; repository and outbox define the
atomic boundary. Bind idempotency keys to request hashes. Test ambiguous timeout,
callback duplication/order, partial refund, illegal transitions, and reconciliation.


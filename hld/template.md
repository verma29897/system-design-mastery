# HLD: <System>

## 1. Scope

### Functional requirements

- 

### Non-functional requirements

- Availability:
- Latency:
- Consistency:
- Durability/retention:
- Security/privacy:
- Explicitly out of scope:

## 2. Estimation

| Input | Assumption | Result / implication |
|---|---:|---|
| DAU | | |
| Peak read/write QPS | | |
| Object/request size | | |
| Storage + replication | | |
| Peak bandwidth | | |

## 3. APIs and events

Document auth, idempotency, pagination, versioning, and errors.

## 4. Data model and ownership

For each entity: key, important fields, indexes, source of truth, retention.

## 5. Architecture

Draw components and trust boundaries. Explain why each exists.

## 6. Critical flows

### Write path

### Read path

## 7. Deep dives

Partitioning, consistency, cache policy, asynchronous work, hotspots.

## 8. Failure handling

Timeouts, retries, duplicates, ordering, overload, region loss, reconciliation.

## 9. Security and observability

AuthN/AuthZ, abuse, encryption, privacy/deletion; SLIs, logs, traces, alerts.

## 10. Trade-offs and evolution

State current choice, rejected alternative, breaking point, and next design.


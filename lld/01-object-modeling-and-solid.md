# Object Modeling, SOLID, and the LLD Interview

## Method

1. Extract use cases, constraints, and failure cases.
2. Identify entities (identity), value objects (value equality), services
   (cross-entity behavior), and repositories/gateways (external boundaries).
3. Write invariants before methods.
4. Assign each behavior to the object with the needed information.
5. Introduce interfaces at change points or test boundaries.
6. Walk through a happy path, then failure and concurrency paths.
7. Implement the smallest core and test observable behavior.

## Relationships

- Association: objects know/use one another.
- Aggregation: a whole references independently-lived parts.
- Composition: the whole owns the parts' lifecycle.
- Inheritance: an `is-a` substitution; use sparingly.
- Interface composition: small capabilities combined at use sites.

Prefer composition when behavior varies independently. In Go, accept interfaces
where behavior is consumed and return concrete types where practical.

## SOLID as diagnostic tools

- **SRP:** one reason to change, not one method per type.
- **OCP:** add a variant without editing stable policy code.
- **LSP:** implementations preserve their interface's behavioral contract.
- **ISP:** clients depend only on capabilities they use.
- **DIP:** policy depends on abstractions; infrastructure plugs in.

Avoid ceremonial interfaces, getter-heavy anemic models, and pattern-first
design. A plain function is often the right abstraction.

## Invariants and concurrency

Examples: a parking spot holds at most one active vehicle; account balance is
derived from immutable ledger entries; an order's filled quantity never exceeds
its original quantity. Decide which lock or transaction protects each invariant,
keep critical sections small, and never call slow external code while holding a
lock. Run Go tests with the race detector.

## Review questions

1. Which rules belong inside entities versus an application service?
2. What must be atomic?
3. Which dependency is likely to vary?
4. Can each interface contract be stated without naming an implementation?


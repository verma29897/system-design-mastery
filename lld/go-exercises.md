# Go Exercises

Implement one component at a time as a small package with table-driven tests.
Suggested packages: `lru`, `ratelimit`, `scheduler`, `pubsub`, `orderbook`, and
`toolrunner`.

Definition of done:

- public contract and errors documented;
- core invariants listed in the package documentation;
- deterministic unit tests (inject a clock where time matters);
- cancellation and shutdown tested where applicable;
- bounded memory/goroutine behavior;
- `go test -race ./...` passes;
- benchmark added only when it answers a specific capacity question.


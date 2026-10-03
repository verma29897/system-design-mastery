# Task Scheduler

Use Task, Schedule, priority queue, Dispatcher, WorkerPool, CancellationToken, and
TaskStore. Inject a clock; keep the heap invariant under one owner/lock; bound the
worker queue. Define queued/running/completed/failed/cancelled transitions. Test
ordering, reschedule, cancellation races, retry, shutdown, and no goroutine leaks.


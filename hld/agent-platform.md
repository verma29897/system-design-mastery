# AI Agent Platform

Represent runs, steps, approvals, tool calls, artifacts, and checkpoints as a
durable workflow. Validate tool schemas; apply scoped credentials, policy checks,
timeouts, idempotency, isolation, and audit logs. Treat tool/retrieved output as
untrusted data and require approval for consequential actions.

Drill: resume after a worker crash immediately after a side-effecting tool call
without repeating the effect or falsely marking the step complete.


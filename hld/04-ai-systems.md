# AI Systems: RAG, Gateways, Assistants, and Agents

## RAG pipeline

```text
sources → parse/OCR → normalize → chunk → embed → vector/index stores
query → authorize → retrieve → hybrid merge → rerank → context pack
      → model → cited response → evaluation/feedback
```

Chunk boundaries should preserve meaning and metadata. Evaluate retrieval before
generation using recall@k, MRR/nDCG, citation coverage, and permission leakage.
Hybrid lexical/vector retrieval often handles exact names and semantic matches
better than either alone. Store source/version/offset metadata for citations and
deletion propagation.

## Model gateway

Normalize provider contracts while preserving capabilities. Route by policy,
quality, latency, region, context length, safety, and cost. Apply tenant quotas,
admission control, deadlines, retries only when safe, circuit breakers, fallback,
usage accounting, and semantic/prefix caching where policy permits.

Track time to first token, inter-token latency, total latency, tokens, cost,
error class, fallback rate, and answer quality. Batching improves throughput but
can harm first-token latency; continuous batching balances both.

## Streaming assistant

Persist a conversation/message record before invoking a model. Stream over SSE
for simple server-to-client tokens; use WebSockets when bidirectional real-time
events are required. Bound buffers and propagate cancellation. Store generation
state so disconnects and retries have defined behavior.

## Agent platform

Treat the agent as a durable state machine, not a loop living in one process:

```text
plan → request tool → validate policy → optional approval → execute
     → record result → observe → continue/finish/fail
```

Tool schemas require strict validation, scoped credentials, timeouts, output
limits, idempotency, audit logs, and isolation. Separate untrusted retrieved/tool
content from instructions. High-impact actions require explicit authorization
and often human approval.

## Evaluation

Maintain versioned datasets for task success, groundedness, retrieval relevance,
safety, latency, and cost. Combine deterministic checks, expert review, and
carefully calibrated model judges. Trace prompt/model/retrieval/tool versions so
regressions are reproducible.


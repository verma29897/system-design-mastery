# ChatGPT-Style Assistant

Design conversations/messages, model routing, context construction, moderation,
streaming, cancellation, regeneration, quotas, and usage accounting. Persist the
request before inference, stream with bounded SSE buffers, summarize long context,
and record prompt/model versions. Protect tenant data and degrade on overload.

Drill: recover from a client disconnect mid-generation while preserving billing,
message state, and a clear retry contract.


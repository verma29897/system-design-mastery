# Notification System

Model notification intent, user preferences, templates, channel routing, provider
adapters, scheduling, delivery attempts, and status callbacks. Use a durable queue
per priority/channel, idempotent workers, provider rate limits, retries with
jitter, dead-letter handling, and deduplication. Separate accepted, sent,
delivered, and read states.

Drill: send a campaign without delaying OTP messages; handle a provider outage
without duplicate user-visible notifications.


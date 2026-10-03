# LLD Case Studies

Use [the LLD template](template.md). Recommended progression:

1. [LRU Cache](lru-cache.md)
2. [Tic-Tac-Toe](tic-tac-toe.md)
3. [Vending Machine](vending-machine.md)
4. [Parking Lot](parking-lot.md)
5. [Snake and Ladder](snake-and-ladder.md)
6. [Rate Limiter](rate-limiter.md)
7. [Logging Framework](logging-framework.md)
8. [Notification System](notification-framework.md)
9. [In-Memory File System](file-system.md)
10. [Splitwise](splitwise.md)
11. [Task Scheduler](task-scheduler.md)
12. [Elevator System](elevator.md)
13. [Food Delivery](food-delivery.md)
14. [Ride Sharing](ride-sharing.md)
15. [Payment Gateway](payment-gateway.md)
16. [Trading / Order Book](order-book.md)
17. [Kafka](kafka.md)
18. [Chess](chess.md)
19. [Claude-style Assistant](ai-assistant.md)
20. [Multi-Provider Model Gateway](model-gateway.md)
21. [RAG Pipeline](rag-pipeline.md)
22. [AI Agent Tool Runner](tool-runner.md)

For every concurrent implementation, run `go test -race ./...` and document the
invariant protected by each lock or single-owner goroutine.

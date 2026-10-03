# Trading System / Order Book

Model Order, Side, Price, Quantity, PriceLevel, Book, Trade, and matching engine.
Use integer/decimal values. Maintain price priority and FIFO within a price; match
and update quantities atomically. Test partial/multiple fills, cancel races, market
orders, self-trade policy, and deterministic event ordering.


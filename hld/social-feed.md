# Social Feed

Model posts, follows, timelines, ranking, pagination, and visibility. Compare
fan-out-on-write with fan-out-on-read and use a hybrid for celebrity accounts.
Design event ingestion, timeline stores, cache, ranking features, deletion, and
privacy propagation. Avoid offset pagination and duplicate/missing items.

Drill: trace post creation and feed read; then handle a celebrity with 100 million
followers and a privacy change affecting cached feeds.


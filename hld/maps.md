# Maps and Routing

Separate map ingestion, tile generation/serving, geocoding, nearby search, traffic,
and route computation. Model the road network as a weighted graph; discuss A*,
bidirectional search, contraction hierarchies, and traffic-dependent weights.
Serve versioned vector/raster tiles through a CDN.

Drill: update road closures quickly without rebuilding the entire routing graph or
returning internally inconsistent tile versions.


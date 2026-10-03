# Ride Sharing

Model rider/driver state, location updates, nearby search, matching, trip lifecycle,
ETA, surge, and payment. Partition geography with H3/geohash cells, maintain an
ephemeral availability index, and commit assignment with a conditional transition
so one driver cannot accept two rides.

Drill: handle GPS noise, cross-cell searches, concurrent offers, reconnects, and
a regional hotspot after a stadium event.


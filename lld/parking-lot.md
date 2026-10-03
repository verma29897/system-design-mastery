# Parking Lot

Model Vehicle, Spot, Floor, Ticket, Gate, AllocationPolicy, and PricingPolicy.
Allocation and occupancy transition atomically; value objects represent plate,
time, and money. Keep spot selection separate from fee calculation. Test capacity,
vehicle compatibility, lost tickets, duplicate exits, and concurrent entry.


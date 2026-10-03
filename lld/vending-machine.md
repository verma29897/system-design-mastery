# Vending Machine

Model products, slots, inventory, money, transaction, dispenser, and explicit
Idle/Payment/Dispensing/OutOfService states. Preserve stock and cash invariants
across cancellation and failures. Separate payment hardware behind interfaces.
Test insufficient funds, change unavailable, concurrent selection, and dispense
failure with refund/repair behavior.


# Test Plan

## Test layers
1. Unit tests for business rules and calculation functions.
2. Integration tests for order creation, reservations, allocations and route planning.
3. Authorization tests for role and organization boundaries if a backend exists.
4. End-to-end tests for the judge-facing workflow.
5. Manual demo rehearsal on the actual presentation device and network.

## Critical unit tests
- Valid MOQ and pack multiples accepted; invalid multiples rejected.
- Offer selection ignores inactive, out-of-region or unauthorized offers.
- Lowest eligible estimated total cost wins under the approved demo policy.
- Split fulfillment never exceeds requested quantity.
- Confirmed price snapshot remains unchanged after offer price changes.
- Money calculations use paise/decimal-safe arithmetic.
- Weight-based freight allocations sum exactly to route freight after rounding.
- Capacity checks reject overweight/oversized route plans.
- Pickup precedes delivery for each job.
- Invalid state transitions are rejected.
- Duplicate idempotency key does not create a duplicate order.

## Integration tests
- Order placement reserves stock and writes allocations.
- Failed reservation leaves no partially confirmed order unless explicit partial allocation is supported.
- Cancellation releases the correct reservation exactly once.
- Supplier acceptance changes the correct allocation only.
- Route confirmation links jobs and prevents accidental double assignment.
- Driver stop update updates the route and relevant retailer timeline.
- Dashboard metrics reflect underlying scenario records.

## Security tests
- Retailer A cannot read Retailer B’s orders.
- Supplier A cannot modify Supplier B’s inventory or allocations.
- Dispatcher cannot change offer pricing unless explicitly authorized.
- Client-supplied organization IDs cannot bypass server-side authorization.
- Demo role switching is clearly restricted to demo mode.
- Secrets are not present in source control.

## End-to-end demo test
1. Open retailer role.
2. Compare offers for a seeded product.
3. Add valid quantity and confirm order.
4. Verify order number and allocation.
5. Open supplier role and accept/prepare the allocation.
6. Open dispatcher role and plan a route with at least two compatible deliveries.
7. Verify capacity and ordered stops.
8. Confirm route and advance one stop.
9. Verify retailer timeline updates.
10. Open dashboard and confirm KPIs reflect the actions.

## Performance and reliability checks
- App loads and navigates without console errors.
- Seed reset works repeatedly.
- Empty/error states are visible when providers are unavailable.
- Route screen remains usable without map tiles.
- Run lint, type check, tests and production build where configured.

## Evidence
Maintain `docs/BUILD_STATUS.md` with date, command, pass/fail result, and known limitations. Capture screenshots of the core workflow and a route screen for the submission.

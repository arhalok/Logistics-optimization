# User Flows

## Flow A — Retailer places an order
1. Retailer opens catalog.
2. Searches or filters products.
3. Opens SKU offer comparison.
4. Reviews supplier type, price, MOQ/case pack, stock status, estimated delivery and estimated freight.
5. Adds valid quantities to basket.
6. Reviews line totals and estimated order total.
7. Confirms order.
8. System validates offer status, region, authorization, pack rules and available-to-promise.
9. System reserves stock and creates supplier fulfillment allocations.
10. Retailer sees order confirmation, source allocation and status timeline.

### Failure paths
- Stock changed: explain the unavailable quantity and ask the retailer to revise or accept an explicit split.
- MOQ/case multiple invalid: show the valid minimum and increment.
- No eligible offer: show unavailable; do not fabricate supply.
- Order submit retried: same idempotency key must not create duplicate orders.
- Partial fulfillment: show each supplier allocation and remaining quantity.

## Flow B — Supplier accepts and prepares order
1. Supplier signs into the supplier workspace.
2. Views assigned order lines.
3. Opens order details, quantity, delivery location and requested window.
4. Accepts or rejects with reason.
5. Marks accepted items as ready for pickup.
6. The operations view updates using persistence/realtime if configured; otherwise refreshes from the demo repository.

## Flow C — Dispatcher plans shared route
1. Dispatcher opens eligible delivery jobs.
2. Selects a planning window and vehicle.
3. System excludes incompatible jobs and explains exclusion reasons.
4. Route planner returns an ordered stop list, load utilization, distance/time estimate and estimated route cost.
5. Dispatcher reviews the plan and confirms it.
6. Driver view shows assigned stops.
7. Driver marks pickup/delivery progress.
8. Retailer order timeline reflects delivery progress.

## Flow D — Admin manages demo scenario
1. Admin opens scenario dashboard.
2. Reviews sample retailers, suppliers, offers, stock, vehicles and jobs.
3. Can reset to the initial scenario.
4. Sees visible labels indicating sample data and simulated features.
5. Can inspect build status and open questions.

## Flow E — Judge-facing presentation
1. Start on a clear problem/solution dashboard.
2. Demonstrate supplier offer comparison.
3. Place an order and show supplier allocation.
4. Switch to operations and show multiple retailers’ jobs.
5. Plan/confirm a shared route.
6. Advance one delivery stop.
7. Show updated order status and a small set of scenario-derived KPIs.
8. Explain what is real in the prototype, what is simulated, and what would be integrated next.

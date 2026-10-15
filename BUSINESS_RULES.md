# Business Rules and Invariants

## 1. Supplier and offer model
- A catalog SKU is a product identity; a supplier offer is a particular supplier’s commercial offer for that SKU.
- An offer includes supplier organization, supplier type, SKU, price, unit of measure, case pack, MOQ, available quantity, lead time, service region, and offer validity.
- Distributor offers may be used only when the demo data explicitly marks the distributor as authorized for the brand/SKU and relevant region.
- Never infer authorization solely because a distributor lists a product.
- Offer eligibility is checked at order time, not only when the product page loads.
- For the prototype, supplier authorization is seeded and illustrative, not independently verified.

## 2. Units, pack sizes, and money
- Store quantities in a consistent base unit and preserve the displayed order unit/case pack.
- Quantity must satisfy MOQ and pack multiple. For example, if case pack = 12 and MOQ = 12, valid quantities are 12, 24, 36—not 13.
- Use integer paise for INR calculations or a decimal-safe money type.
- Keep a price snapshot on confirmed order lines: unit price, quantity, discount, freight allocation, and applicable illustrative tax fields. Later offer edits must not rewrite confirmed order values.
- Round only at defined calculation boundaries; document the rounding rule.
- Never add tax twice or describe a prototype estimate as a tax invoice.

## 3. Order and fulfillment separation
- An order is the retailer’s commercial request.
- An order line represents a requested SKU and quantity.
- A fulfillment allocation identifies the supplier/location and quantity assigned to fulfill a line.
- A shipment is a physical movement; it may carry fulfillment allocations for multiple orders if compatible.
- A route is an ordered plan for a vehicle; it may contain multiple pickup and delivery stops.
- Payment status is separate from order status. A delivered shipment does not automatically mean payment has settled.
- For a hackathon prototype, payment may be simulated and must be labelled.

## 4. Inventory reservation
- Available-to-promise = on-hand quantity − already reserved quantity − any safety stock configured for the demo.
- Never allocate more than available-to-promise.
- Reservation and order confirmation must be atomic in a real database. In a local prototype, the service layer must at least serialize updates and tests must cover competing orders.
- Reservation states: `held`, `committed`, `released`, `expired`.
- Cancellation releases only quantities that have not been picked/shipped, according to the implemented demo rule.
- Never silently substitute a product. A substitution requires explicit retailer acceptance.

## 5. Hybrid sourcing policy
Recommended demo policy, configurable in code:
1. Filter offers by active status, supplier authorization, region, MOQ/pack validity, and stock.
2. Estimate item cost and delivery contribution for each eligible offer.
3. Rank eligible offers by total estimated retailer cost, then delivery estimate, then a stable tie-breaker.
4. Allocate the line to the best eligible offer.
5. If one offer cannot supply the full quantity, split only if split fulfillment is enabled and the retailer-facing UI makes the split explicit.
6. Never choose an unauthorized distributor just because it is closer or cheaper.
7. Record the reason for allocation (e.g., “eligible, sufficient stock, lower estimated landed cost”). Do not describe this as an AI decision.

## 6. Shared-logistics compatibility
Two jobs may be consolidated only if they satisfy the demo’s declared rules:
- Same planning window or compatible dispatch window.
- Compatible origin/pickup sequence and supplier handling requirements.
- Vehicle capacity in weight and volume is not exceeded.
- Service region and delivery windows are compatible.
- Any cold-chain, fragile, hazardous, or other special handling flags are compatible; for the demo, either enforce the flags or exclude such SKUs.
- A shared route does not mean multiple sellers’ inventory is merged. It means physical delivery jobs are coordinated; commercial ownership and invoice responsibility remain separately recorded.

## 7. Freight allocation
- Route-level estimated freight is allocated across included orders using the chosen configured method.
- Prototype default: weight-based pro-rata if all demo SKUs have a positive known weight; otherwise use a disclosed equal-per-stop fallback.
- Formula for weight method: order freight share = route freight estimate × (order’s allocated shipment weight / total allocated shipment weight).
- Display “estimated freight” and the method used.
- If a route includes multiple pickup origins, the demo must either model pickup legs or explicitly state that its simplified estimate excludes some origin complexity.
- Estimated savings = baseline cost − shared-route estimate. The baseline definition and inputs must be visible. Never invent a savings percentage.

## 8. State transitions
- Order: `draft → placed → confirmed → partially_fulfilled | fulfilled → completed`; cancellation is allowed only from states defined by policy.
- Order line: `pending → allocated → partially_fulfilled → fulfilled`; may be `rejected` or `cancelled` with a reason.
- Shipment: `planned → assigned → picked_up → in_transit → delivered`; exceptions include `failed` or `cancelled`.
- Route: `draft → optimized → assigned → in_progress → completed`; may be `cancelled`.
- Stop: `pending → arrived → delivered`; exception statuses include `failed_attempt` and `skipped`, with reason required.
- These are separate state machines. Do not derive all statuses from one generic `status` field.

## 9. Auditability
Record actor, action, entity, timestamp, and relevant before/after values for critical demo operations such as price change, order confirmation, allocation, route confirmation, and delivery status.

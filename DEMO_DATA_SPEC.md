# Demo Data Specification

## Purpose
Create one deterministic scenario that makes the hybrid sourcing and shared-logistics behavior visible without depending on live partners.

## Synthetic scenario requirements
- Fictional/demo organization names or clearly marked sample organizations.
- A sample service area around Jaipur may be used, but locations and performance figures must be labelled synthetic.
- 3 retailers with distinct delivery points.
- 1 manufacturer and at least 2 distributors.
- 6–10 products across 3–4 categories.
- At least 3 products with multiple offers.
- At least one direct offer that wins under the configured selection policy.
- At least one authorized distributor offer that wins.
- At least one scenario requiring a split or showing why split fulfillment is unavailable.
- At least 2 vehicles with different capacity.
- At least 3 compatible delivery jobs.
- At least 1 deliberately excluded job with an understandable reason.
- Different stock quantities so reservation logic can be demonstrated.
- A product with MOQ/case-pack validation.

## Data integrity
- All quantities and prices must be plausible demo inputs, not claims about current market pricing.
- Store weights and volumes in consistent units.
- Give every location coordinates if a map is shown.
- Ensure the planned route is feasible with its chosen vehicle.
- Derive dashboard metrics from the seeded records and user actions.
- Include a reset function that returns to the initial deterministic scenario.
- Do not seed actual credentials, phone numbers or personal information.

## Suggested demonstration setup
1. Retailer A orders two SKUs.
2. SKU 1 selects a direct offer.
3. SKU 2 selects an eligible distributor offer due to stock, lead time or total estimate.
4. Retailer B has an existing compatible delivery job.
5. Dispatcher consolidates jobs for A and B into a route if constraints permit.
6. Driver marks a delivery complete.
7. Dashboard reflects updated route and delivery state.

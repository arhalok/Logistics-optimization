# 3–5 Minute Hackathon Demo Script

## Opening — 20 seconds
“Small kirana stores often buy through fragmented supply channels. Kirana Setu lets a store compare eligible manufacturer and distributor offers, place an order, and coordinate delivery with nearby stores through shared multi-stop routes.”

## Act 1 — Retailer procurement — 60 seconds
1. Open the retailer workspace.
2. Search for a product.
3. Compare the manufacturer offer with authorized distributor offers.
4. Explain MOQ, pack size, availability and estimated delivery.
5. Add a valid quantity and show the estimated total.
6. Confirm the order.
**Point to make:** The system does not just list products; it compares eligible supply options and explains its selection.

## Act 2 — Fulfillment transparency — 40 seconds
1. Open order details.
2. Show the price snapshot and supplier allocation.
3. Switch to the relevant supplier workspace.
4. Accept the order and mark it ready for pickup.
**Point to make:** Commercial order, supplier allocation and physical delivery are separate records.

## Act 3 — Shared logistics — 75 seconds
1. Open dispatcher view.
2. Show pending jobs and the selected vehicle capacity.
3. Plan a route with at least two compatible retailer deliveries.
4. Show ordered stops, load utilization, estimated distance/time and freight allocation.
5. Explain that the demo route is simulated unless a verified OSRM/VROOM integration is active.
6. Confirm route and open the driver view.
**Point to make:** Multiple retailers can share a compatible route while supplier ownership and order records remain distinct.

## Act 4 — Delivery and outcomes — 40 seconds
1. Mark a stop delivered.
2. Show the retailer order timeline update.
3. Show scenario-derived dashboard metrics.
**Point to make:** The operational action is connected to the retailer’s view and the metrics.

## Closing — 20 seconds
“The prototype demonstrates the core loop: eligible sourcing, transparent order allocation, and shared delivery planning. The next phase is validating the model with real retailers and suppliers, then integrating verified inventory, routing, payment and compliance services.”

## Judge questions to prepare for
- **Is the route optimization live?** State exactly which provider is configured, or say it is the deterministic demo planner.
- **Are suppliers real?** Explain whether records are synthetic and how authorization would be verified in a pilot.
- **Are payments and tax invoices live?** State that the prototype uses simulated/illustrative billing unless real integrations have been completed and reviewed.
- **How is savings calculated?** Show the baseline formula and input values; do not quote a percentage without a reproducible calculation.
- **What is the moat?** Explain the combination of hybrid supplier eligibility, order-level transparency, and coordinated local delivery—not merely an online catalog.

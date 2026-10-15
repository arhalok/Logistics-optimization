# Requirements and Acceptance Criteria

## Priority definitions
- **P0:** Must work for the demo.
- **P1:** Valuable if time permits.
- **P2:** Post-hackathon.

## P0 — Retailer experience
- Browse a seeded catalog with product name, brand, category, unit/case size, indicative price, stock/availability, supplier type, minimum quantity, and delivery estimate.
- Compare offers for the same SKU across direct manufacturer and authorized distributor channels.
- Add/remove items and change quantities.
- Enforce minimum order quantity and case-pack multiples with clear validation.
- Show item subtotal, estimated freight, taxes as illustrative only if shown, and total estimated payable. Clearly label tax/invoice figures as illustrative.
- Confirm an order and show an order reference and order details.
- View order lifecycle and fulfillment allocation. If a line is split, show each source and quantity.
- Display empty, loading, validation, and error states.

## P0 — Supplier operations
- Show the supplier’s assigned orders and relevant order lines.
- Allow a demo operator to accept/reject an order line or mark it ready for pickup, with permitted state transitions.
- Only show records belonging to the selected demo supplier organization.
- Distinguish manufacturer, distributor, and C&F partner roles.

## P0 — Shared logistics
- Show eligible pending deliveries and a route planning action.
- Group compatible delivery jobs using a documented, deterministic rule.
- Respect configured vehicle capacity and required pickup-before-delivery precedence if represented in the scenario.
- Present route stops in order, vehicle/load utilization, estimated distance/time, and which orders each stop serves.
- If using a real OSRM/VROOM integration, identify it and show errors/fallback. Otherwise display “Demo route plan”.
- Allow dispatcher to assign/confirm a route and a driver to advance stop status.
- Support a list-based route view even if map tiles or routing services are unavailable.

## P0 — Admin and demo controls
- Seeded scenario with realistic but synthetic retailers, suppliers, products, offers, stock, vehicles, and delivery locations.
- Reset/reload demo scenario without corrupting the database.
- A role switcher is acceptable for hackathon demonstration only; label it “Demo role switcher”. It must not be mistaken for production authorization.
- Dashboard numbers must derive from current demo data rather than arbitrary hardcoded totals.

## P0 — Technical quality
- Responsive design, especially at laptop presentation size and mobile retailer size.
- No broken navigation or inert primary actions.
- Type-check/build succeeds.
- Critical business rules have automated tests or documented manual verification.
- README has exact setup instructions and limitations.

## P1
- English/Hindi language toggle for core labels.
- Product search and category filters.
- Low-stock and delivery exception alerts.
- Freight allocation explanation (weight-based default, with all weights synthetic).
- CSV export of demo orders or route manifest.
- QR-like order reference or proof-of-delivery photo placeholder, clearly simulated.

## P2
- Real payment gateway, real supplier ERP integrations, credit/ledger, tax invoice automation, returns/RMA, advanced analytics, production identity verification, multi-city scaling.

## Acceptance criteria for the hackathon demo
1. A judge can understand the product in 30 seconds from the landing/dashboard.
2. The retailer can complete a seeded purchase without manually editing data.
3. The system displays which supplier fulfills each order line and why.
4. At least two retailer deliveries can appear on a single shared route when the scenario’s compatibility rules allow it.
5. The route screen shows ordered stops, estimated distance/time, and vehicle capacity status.
6. Route stop statuses can be advanced and the retailer-facing order status updates.
7. A refresh does not silently erase the order if persistence is enabled; if local-only state is used, this limitation is disclosed.
8. No unsupported live-integration or compliance claims appear in the UI or pitch.
9. Critical tests pass and the team can explain the routing and fulfillment logic.

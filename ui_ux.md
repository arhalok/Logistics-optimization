
Loading older messages…







































































































































































Kirana Setu — Blinkit-Inspired UI/UX Prototype Specification
Purpose: Build a visually polished, Blinkit-inspired quick-commerce experience adapted for B2B kirana procurement and shared logistics. Use the supplied Kisan Setu screenshots as layout inspiration for role-based portals and operations pages, but create a distinct Kirana Setu brand and workflow. Do not copy Blinkit branding, assets, or proprietary UI exactly.

1. Product direction
Kirana Setu is a B2B procurement and delivery coordination platform for neighborhood kirana stores. The prototype combines:

A fast, familiar, mobile-first shopping experience inspired by quick-commerce patterns.
Hybrid sourcing: direct manufacturer/brand offers plus authorized distributor/C&F offers.
Shared logistics: compatible orders from multiple stores can be consolidated into capacity-aware multi-stop routes.
Separate workspaces for Retailer, Supplier, Logistics/Dispatcher, Driver, and Admin.
The UI should feel as quick and easy as a modern quick-commerce app, while the operations portal should be as clear as a logistics control center.

2. Design goals
A judge understands the product in 10 seconds.
Retailers can find products, compare supplier offers, build a basket, and place a demo order without confusion.
The product looks polished and consistent across mobile and desktop.
The logistics route screen visibly demonstrates the key innovation.
Every key interaction works; no decorative primary buttons.
Demo-only behavior is labelled honestly.
3. Brand and visual system
Brand personality
Fast, reliable, local, transparent, operationally smart.

Suggested visual direction
Primary: deep green for trust and supply-chain identity.
Accent: bright lime/green for primary actions and positive states.
Neutral surfaces: warm white or very light gray.
Text: dark charcoal, high contrast.
Use a limited amber accent for warnings and route/dispatch status.
Rounded cards, soft borders, subtle shadows, generous whitespace.
Strong typography hierarchy, readable tables, clean iconography.
Avoid overusing gradients, excessive glassmorphism, or too many colors.
UI feel
Retailer side: quick-commerce simplicity—large search, category chips, product cards, prominent basket, quick quantity controls.
Operations side: logistics SaaS—compact KPIs, status filters, tables, route map/list, clear actions.
Mobile first for retailer and driver; desktop optimized for supplier, dispatcher, and admin.
Suggested tokens
:root {
  --ks-primary: #16834A;
  --ks-primary-dark: #0B5D35;
  --ks-accent: #B8F34A;
  --ks-warning: #E99A16;
  --ks-danger: #D94A4A;
  --ks-bg: #F6F8F6;
  --ks-surface: #FFFFFF;
  --ks-text: #17211B;
  --ks-muted: #68756C;
  --ks-border: #E1E8E2;
  --ks-radius-card: 18px;
  --ks-radius-control: 12px;
}
These are proposed design tokens; the team may adjust them if it preserves visual consistency and accessibility.

4. Information architecture
Public/entry screen
Kirana Setu logo/wordmark.
Short headline: “Your store. Better supply. Smarter delivery.”
Supporting line: “Compare trusted supply options and coordinate deliveries with nearby stores.”
Role cards:
Retailer
Manufacturer / Brand
Distributor / C&F
Logistics / Dispatcher
Driver
Admin
“Launch demo” action.
Small note: “Prototype with synthetic sample data.”
Retailer portal — Blinkit-inspired flow
Navigation:

Home
Shop
Offers
Orders
Account
Home:

Greeting and store name.
Prominent search bar: “Search products, brands, or categories”.
Category tiles: Staples, Beverages, Snacks, Personal Care, Home Care, Dairy (only seed categories that exist).
Quick reorder section.
“Popular with nearby stores” only if it is clearly labelled as demo scenario data.
Offer banner: do not invent actual discounts; show seeded demo offers with clear terms.
Sticky basket summary on desktop and bottom basket bar on mobile.
Shop/catalog:

Search and category filters.
Product cards with image/placeholder, name, brand, unit/case size, selected offer price, supplier type, availability, MOQ, and delivery estimate.
Quick add (+) quantity controls.
Case-pack validation.
Offer comparison button.
Offer comparison:

Show direct manufacturer offer and authorized distributor offers side-by-side.
Compare unit/case price, MOQ, stock, delivery estimate, estimated freight, and estimated landed cost.
Explain why an offer is eligible and why the recommended option ranks first.
Never imply a distributor is authorized unless a seeded authorization record supports it.
Mark supplier data as sample data.
Basket:

Item quantity controls.
Clear pack-size and MOQ requirements.
Subtotal, estimated freight, optional illustrative tax, estimated total.
Supplier allocation preview.
Clear “Place demo order” CTA.
Label: “Prototype estimate — not a tax invoice.”
Order confirmation:

Order number, estimated total, fulfillment source by line, and next steps.
A simple timeline: Order placed → Supplier accepted → Ready for pickup → Out for delivery → Delivered.
Statuses should reflect actual prototype state, not pre-filled fake progress.
Orders:

Active and past demo orders.
Filters by status.
Order detail screen with line items, fulfillment allocations, shipment/route information and delivery status.
5. Product card requirements
Every product card should show:

Product image or coherent category placeholder.
Product name and brand.
Pack/unit size.
Price and price unit.
Supplier label: “Brand direct” or “Authorized distributor”.
Availability indicator.
MOQ/case pack where relevant.
Add/quantity control.
Compare offers action where multiple offers exist.
Do not show fake stock precision or false urgency. Use “In stock (sample data)” or a clearly seeded quantity when appropriate.

6. Supplier workspaces
Manufacturer / Brand portal
Overview KPIs: assigned order lines, pending acceptance, ready for pickup.
Product offers and indicative price lists.
Stock view from synthetic data.
Assigned orders.
Accept/reject allocation with reason.
Mark ready for pickup.
Activity history.
Distributor / C&F portal
Same core operational pattern, but show authorization status and service region.
Only show offers that exist in the demo dataset.
Clearly distinguish brand-direct supply from distributor fulfillment.
Support order acceptance, rejection with reason, and ready-for-pickup status.
7. Logistics / dispatcher portal — showcase screen
This is the most important screen after retailer checkout.

Header:

“Shared Delivery Control Center”
Planning window and service-area selector (demo values).
Status chips: Ready for planning, Planned, Assigned, In transit, Delivered.
KPI cards:

Eligible delivery jobs.
Active routes.
Estimated route distance.
Vehicle capacity utilization.
Estimated freight per order.
Main layout:

Left panel: delivery job queue with retailer, supplier pickup, weight/volume, readiness and compatibility.
Center/right: map with numbered stops if a map provider is available.
Persistent list view as a fallback if map tiles are unavailable.
Route summary panel with vehicle, ordered stops, distance/time estimate, estimated freight and capacity usage.
“Plan shared route” and “Confirm route” actions.
“Excluded jobs” section that explains why a job was not included (capacity, incompatible window, missing location, not ready).
Route plan behavior:

Consolidate at least two compatible retailer jobs in the seeded demo.
Check vehicle weight and volume capacity.
Preserve pickup-before-delivery constraints when multiple pickups are modelled.
Show the planner type: “Demo route plan” unless OSRM/VROOM integration has been configured and verified.
Route metrics must be calculated from the scenario or returned by a verified provider.
Show the baseline definition before showing estimated savings.
8. Driver portal
Mobile-first screen:

Assigned route and vehicle.
Route progress (e.g., stop 2 of 4).
Next stop card with address label and order reference.
Pickup/delivery instruction.
Actions: Arrived, Mark delivered, Failed attempt.
Require a reason for failed attempt.
Proof-of-delivery photo/signature can be simulated only if labelled “Demo POD”; do not imply an actual file was stored if it was not.
Offline behavior can be represented as a planned feature unless actually implemented.
9. Admin portal
Overview of demo scenario and data freshness.
Manage sample organizations, products, offers, supplier authorization records, inventory and vehicles.
Scenario reset button.
Integration status: Database, Map, Routing, Payments, Notifications.
Status labels: Connected, Unavailable, Simulated, Not configured.
Audit activity feed.
Open questions and known limitations.
Demo role switcher allowed only as an explicitly labelled prototype feature.
10. Core end-to-end interaction
Open the entry screen and choose Retailer.
Search for a seeded FMCG product.
Compare manufacturer and authorized distributor offers.
Add valid quantities to the basket.
Review estimated total and supplier allocation.
Place demo order.
Switch to the supplier workspace and accept the assigned allocation.
Mark the allocation ready for pickup.
Open the dispatcher control center.
Select at least two compatible delivery jobs and plan a shared route.
Review stop order, vehicle capacity, distance/time, estimated freight and excluded jobs.
Confirm route.
Open driver view and mark one delivery completed.
Return to retailer order details and show the updated timeline.
End on dashboard metrics derived from the demo scenario.
11. Interaction quality requirements
All primary buttons must work.
Add-to-basket controls update the basket count and totals.
Search and filters change the visible products.
Quantity controls enforce MOQ and case-pack increments.
Offer selection updates the selected offer and estimated total.
Place order validates current stock and offer eligibility.
Supplier actions update order/allocation status.
Route planning returns a route plan or a clear validation error.
Confirm route assigns jobs and prevents accidental double assignment.
Driver status updates the route and retailer timeline.
Dashboard KPIs reflect actual seeded/current state.
Reset restores the deterministic demo scenario.
Show loading, empty, success, and error states.
Keep the route list usable if the map fails.
12. Accessibility and responsive behavior
Retailer screens should work at 360px mobile width.
Operations screens should work at laptop presentation resolution and remain usable on tablet.
Use semantic labels, visible focus, keyboard navigation, sufficient contrast and clear validation messages.
Status must be conveyed with text as well as color.
Do not place essential controls only on hover.
Use responsive tables or cards rather than forcing wide tables onto mobile.
13. Technical guardrails
Use the existing repository stack if already configured; do not replace it without explaining why.
Prefer Next.js + TypeScript if the repository is not yet set up.
Keep domain logic in typed services, not buried in UI components.
Use a service/repository boundary so seeded local data can later be replaced with Supabase/PostgreSQL.
Use integer paise or decimal-safe arithmetic for money.
Keep order, allocation, shipment, route, stop and payment statuses separate.
Use synthetic data and clear demo labels.
Do not claim real payment, tax, supplier, or routing integrations unless verified.
Add tests for offer eligibility, pack rules, stock reservation, route capacity, valid state transitions and duplicate order submissions.
14. Acceptance criteria for the visual prototype
The prototype is ready to show when:

It feels like a cohesive quick-commerce B2B product, not five disconnected admin pages.
The retailer journey is simple and visually polished.
The offer comparison clearly communicates the hybrid supply model.
The dispatcher route screen makes shared logistics obvious.
At least two retailers can share a feasible demo route.
Delivery status updates propagate through the demo flow.
All main interactions work.
Sample/simulated functionality is disclosed.
The team can reset and rehearse the demo reliably.
15. Antigravity execution prompt
Read this entire file and the rest of the Kirana Setu project specification before coding. Inspect the existing repository and screenshots first. Build a distinct Kirana Setu interface with quick-commerce simplicity on the retailer side and a logistics control center for dispatch. Use the screenshots as structural inspiration, not as a pixel-perfect copy. Implement the complete happy path: catalog → offer comparison → basket → order → supplier acceptance → shared route plan → driver delivery update → refreshed retailer timeline/dashboard. Use synthetic demo data, enforce the business rules, make every primary control functional, and clearly label simulated providers. Before coding, list ambiguities and inspect the current code. After each milestone, run available checks and report actual results and limitations.



⋮⋮⋮⋮

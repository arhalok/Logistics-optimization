# UI/UX Specification — Hackathon Quality Bar

## Visual direction
Build a modern, trustworthy B2B operations product—not a generic admin template. Use a restrained palette, generous spacing, clear hierarchy, high-contrast text, consistent iconography, crisp tables/cards, and a strong primary action per screen. Prefer a polished desktop operations view and a fast mobile retailer flow.

## Design principles
- Show the business value in the first viewport.
- Use realistic synthetic data and believable operational details.
- Keep the primary retailer journey short.
- Make complex sourcing/logistics decisions explainable.
- Distinguish status with both text and color; never rely on color alone.
- Use INR formatting consistently.
- Show explicit “Sample data”, “Demo route plan”, “Estimated freight”, and “Prototype only” labels where appropriate.
- Every primary button must work and show feedback.

## Required screens
### 1. Landing / overview
- One-sentence value proposition.
- Clear role entry points: Retailer, Supplier, Dispatcher, Admin.
- Compact metrics derived from the seeded scenario.
- “Start demo” action.

### 2. Retailer catalog
- Search, categories and availability filters.
- Product cards with product/brand, pack size, offer price, stock label, supplier type and delivery estimate.
- Compare offers action.
- Add-to-basket quantity control that enforces MOQ/case pack.

### 3. Offer comparison
- Side-by-side manufacturer and distributor offers.
- Price, MOQ, pack size, availability, estimated delivery and estimated freight.
- “Why this offer?” explanation: eligibility, stock and estimated total cost.
- Authorization badge only when backed by the seeded authorization record; label sample supplier data.

### 4. Basket and checkout
- Quantity and pack validation.
- Item subtotal, estimated freight, illustrative tax if included, estimated total.
- Supplier allocation preview.
- Disclaimer: “Prototype estimate; not a tax invoice.”
- Confirm order button with loading/success/error feedback.

### 5. Order details
- Order reference and status timeline.
- Lines and price snapshots.
- Supplier allocation and split fulfillment if applicable.
- Shipment/route linkage when assigned.
- Delivery status and demo proof of delivery.

### 6. Supplier workspace
- Assigned order lines, quantities, delivery locations, status.
- Accept/reject and mark ready for pickup actions.
- Reason required for rejection.
- Supplier identity and role clearly visible.

### 7. Dispatcher operations
- Queue of eligible jobs with reason and compatibility.
- Vehicle selector with capacity.
- Plan shared route action.
- Map + stop list; list remains available if map fails.
- Load utilization, distance/time, cost estimate and exclusions.
- Confirm route action.

### 8. Driver route view
- Mobile-first stop cards.
- Pickup/delivery details and order references.
- Mark arrived, delivered, or failed attempt with reason.
- Proof-of-delivery is simulated unless actual upload storage exists.

### 9. Admin / scenario controls
- Demo scenario overview, sample entities, reset scenario.
- Integration health/status labels.
- Build limitations and open questions.

## Accessibility and responsiveness
- Keyboard-accessible controls and visible focus states.
- Proper labels for inputs.
- Modal/dialog focus management.
- Responsive layout at 360px mobile width, tablet and desktop.
- Loading skeletons, empty states, error messages, and success confirmations.
- Avoid tiny text in the judge-facing dashboard.

## Content tone
Use concise, professional copy. Avoid unsupported claims such as “AI-powered” unless a real evaluated model exists. Prefer “eligible-offer selection” and “shared route planning”.

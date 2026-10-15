# Kirana Setu — Antigravity Hackathon Prototype Kit

**Purpose:** A self-contained product and engineering brief for building a polished hackathon prototype of Kirana Setu. The project is inspired by the user-provided Kisan Setu reference, but does not depend on access to Kisan Setu source code, private APIs, database, credentials, or deployment.

## Product in one sentence
Kirana Setu helps neighborhood kirana stores procure products from manufacturers and authorized distributors while coordinating compatible deliveries into shared, multi-stop routes.

## Decisions already selected
- **Supply model:** Hybrid marketplace — direct manufacturer/brand fulfillment and authorized distributor/C&F fulfillment.
- **Delivery model:** Shared logistics — consolidate compatible orders into multi-stop routes.
- **Demo target:** A credible, visually strong, end-to-end prototype for a hackathon, not a production-ready commerce, tax, payment, or dispatch platform.
- **Reference use:** Kisan Setu is conceptual inspiration only. Rebuild the product independently.

## Read in this order
1. `AGENTS.md` — rules for Antigravity.
2. `PROJECT_BRIEF.md` — what the product is and the hackathon story.
3. `REQUIREMENTS.md` — prototype scope and acceptance criteria.
4. `USER_FLOWS.md` and `BUSINESS_RULES.md` — how it must behave.
5. `ARCHITECTURE.md` and `DATABASE.md` — technical direction and data model.
6. `API_CONTRACT.md` — service contracts, even if the prototype uses local services.
7. `LOGISTICS_SPEC.md` — shared delivery and route optimization.
8. `UI_UX_SPEC.md` — screens, interaction and visual quality.
9. `DEMO_SCRIPT.md` — predictable presentation flow.
10. `TEST_PLAN.md`, `IMPLEMENTATION_PLAN.md`, and `OPEN_QUESTIONS.md`.

## Prototype truthfulness rule
A feature may be labelled **live**, **simulated**, or **planned**. Never present seeded data, mock payments, sample supplier authorizations, or a heuristic route as a live third-party integration. The demo should be impressive because the workflow is coherent and the result is measurable—not because it pretends to have integrations it does not have.

## Suggested stack
- Next.js + TypeScript
- Tailwind CSS and a consistent component system
- Supabase/PostgreSQL if the team has time and credentials; otherwise use a typed local/demo repository behind a service interface
- Leaflet + OpenStreetMap tiles for a map when network access is available; always provide a list-based route fallback
- OSRM for road-distance/duration estimates and VROOM for vehicle-routing optimization only if the team can configure and verify them; otherwise label the deterministic demo optimizer as simulated

## Required submission
A working prototype, a README with setup instructions, seeded demo accounts/data, automated tests for the critical business rules, screenshots or a short demo recording, and a limitations section.

# Implementation Plan — Hackathon Prototype

## Milestone 0 — Inspect and plan
- Read all project docs.
- Inspect current repository and identify existing work.
- Record assumptions and contradictions in `OPEN_QUESTIONS.md`.
- Produce `docs/BUILD_STATUS.md`.
**Exit:** scope and architecture understood; no unresolved blocker is silently assumed.

## Milestone 1 — Product shell and visual system
- Set up Next.js, TypeScript, linting and tests.
- Create responsive navigation and role workspaces.
- Establish typography, spacing, color, components, status badges and layout.
- Seed synthetic scenario data.
**Exit:** all main screens exist, navigation works, no broken primary actions.

## Milestone 2 — Catalog and offer comparison
- Implement products, supplier offers and authorization eligibility.
- Implement search/filter and offer comparison.
- Add MOQ and case-pack validation.
**Exit:** retailer can compare offers and add valid quantities.

## Milestone 3 — Order and inventory
- Implement basket, checkout, order creation and order details.
- Implement reservations and supplier allocation.
- Snapshot prices and record allocation reasons.
**Exit:** order can be placed, no oversell in tested scenarios, order details are correct.

## Milestone 4 — Supplier workflow
- Supplier order queue.
- Accept/reject and ready-for-pickup transitions.
- Timeline and audit events.
**Exit:** supplier actions change the appropriate order/allocation state.

## Milestone 5 — Shared logistics
- Create delivery jobs from ready allocations.
- Filter compatibility and plan route.
- Add vehicle capacity, stops, estimates and route confirmation.
- Add real routing integration only if time allows and it is verified; otherwise deterministic demo planner.
**Exit:** at least two compatible jobs share a feasible route and the UI discloses planner mode.

## Milestone 6 — Driver and metrics
- Mobile stop list and status updates.
- Proof-of-delivery simulation.
- Dashboard metrics derived from scenario records.
**Exit:** delivery progress updates retailer status and metrics.

## Milestone 7 — Hardening and presentation
- Run tests, lint, type checks and build.
- Fix visible defects.
- Rehearse the demo on a clean browser session.
- Confirm reset behavior and demo credentials.
- Prepare screenshots, 3-minute script and limitations slide.
**Exit:** reliable end-to-end demonstration with honest limitations.

## Time allocation guidance
For a short hackathon, prioritize milestones 1–3, then a narrow but real shared-route flow in milestone 5. Do not spend most of the time on complex production tax/payment features or microservices. A coherent end-to-end flow is more valuable than many unfinished screens.

## Definition of done
A milestone is complete only when its acceptance criteria pass, errors are handled, tests are run or limitations recorded, and the build status is updated.

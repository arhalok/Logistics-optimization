# Decision Log

## Approved project decisions
### D-001 — Hybrid supply model
**Decision:** Support direct manufacturer/brand offers and authorized distributor/C&F offers.
**Reason:** Gives the demo a realistic sourcing comparison and fallback path.
**Consequences:** Supplier offers and authorization records must be separate entities.

### D-002 — Shared logistics
**Decision:** Plan compatible multi-stop delivery routes across multiple retailer jobs.
**Reason:** This is a core differentiator, not a cosmetic map feature.
**Consequences:** Need delivery jobs, vehicles, route plans, ordered stops, capacity checks and clear route estimates.

### D-003 — Hackathon prototype scope
**Decision:** Prioritize one end-to-end workflow over a broad unfinished platform.
**Reason:** Reliability and explainability matter in a live judging environment.
**Consequences:** Payment, tax, credit, ERP integrations and production onboarding are deferred or simulated with visible labels.

### D-004 — Modular monolith
**Decision:** Start with a modular monolith.
**Reason:** Reduces integration and deployment risk for a small hackathon team.
**Consequences:** Maintain domain boundaries and provider interfaces; do not split into microservices prematurely.

### D-005 — Truthful demo data
**Decision:** Use synthetic scenario data and label it.
**Reason:** No real supplier integrations or verified authorization data are provided.
**Consequences:** Demo claims must distinguish measured scenario outputs from market-wide claims.

## Change control
Do not silently override these decisions. Propose a change with reason, scope impact, migration impact, test impact and approval status.

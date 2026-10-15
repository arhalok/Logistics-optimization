# Antigravity Kickoff Prompt — Kirana Setu

Read `AGENTS.md` and every project specification before modifying code. This is a hackathon prototype, not a production marketplace.

First inspect the repository. Then:
1. Summarize the intended product, user roles, architecture, core business invariants and demo workflow.
2. List contradictions, missing decisions and technical risks in `OPEN_QUESTIONS.md`.
3. Create/update `docs/BUILD_STATUS.md` with each feature marked `implemented`, `tested`, `simulated`, `blocked`, or `not started`.
4. Propose a milestone plan aligned to `IMPLEMENTATION_PLAN.md`; do not start unrelated features.
5. Implement the smallest complete end-to-end slice: catalog and offer comparison → valid basket/order → supplier allocation → delivery job → shared route plan → delivery status update → dashboard update.
6. Use synthetic demo data only. Label simulated routing/payment/tax behavior. Never claim live integrations unless verified.
7. Enforce MOQ/case packs, supplier authorization, stock reservations, immutable price snapshots, capacity constraints, pickup-before-delivery, idempotency and valid state transitions.
8. Add tests for critical invariants and run typecheck, lint, tests and build. Report exact outcomes; do not fabricate test results.
9. Ensure the demo works when external map/routing services are unavailable, using a clearly labelled route-list fallback.
10. Deliver exact setup instructions, demo steps, test results, screenshots if available, and known limitations.

Do not assume access to Kisan Setu source code. Treat the supplied Kisan Setu file as conceptual inspiration only. Ask before making any irreversible or high-impact product decision.

# Antigravity Instructions — Kirana Setu

## Mission
Build a polished, reliable hackathon prototype for Kirana Setu, a B2B procurement and shared-logistics platform for Indian kirana stores. The approved product decisions are a hybrid supplier model and shared multi-stop delivery.

## Authority order
If instructions conflict, use this order:
1. Explicit user decisions in the conversation.
2. `PROJECT_BRIEF.md` and approved decisions in `DECISIONS.md`.
3. `REQUIREMENTS.md`, `BUSINESS_RULES.md`, `USER_FLOWS.md`, and `API_CONTRACT.md`.
4. Architecture and implementation details in other documents.
5. Your own assumptions, which must never override an approved decision.

## Anti-hallucination rules
1. Do not claim access to Kisan Setu source code, private services, credentials, or internal data. Its file is inspiration only.
2. Do not invent a real supplier, real authorization, live inventory feed, delivery partner, payment integration, or government integration. Use clearly labelled synthetic demo data.
3. When a requirement is ambiguous, write it to `OPEN_QUESTIONS.md`, describe the impact, propose a default, and label that default as unapproved. For the hackathon, use the safest reversible demo behavior.
4. Do not claim route optimization is live unless a real routing engine has been configured and its output verified. A deterministic simulated optimizer must be labelled “Demo optimization”.
5. Do not claim payments, tax calculations, GST/TCS compliance, invoices, credit underwriting, or e-way bills are production-ready. Demo billing is illustrative only and must be marked accordingly.
6. Do not hardcode fake success for buttons. Each visible action must work, show validation/errors, or be explicitly labelled as a disabled future feature.
7. Do not add features outside the MVP before the core end-to-end scenario works.
8. Do not use secrets in source code. Put variable names in `.env.example`; keep actual credentials local.
9. Never trust frontend-only authorization. If a backend is present, validate permissions on the server and apply database access controls.
10. Never mark a test as passed unless it was actually run and passed. Report unrun tests honestly.

## Required working method
1. Inspect the repository and all project docs before coding.
2. Summarize the architecture and identify contradictions/open questions.
3. Create `docs/BUILD_STATUS.md` with implemented, tested, simulated, blocked, and not-started features.
4. Build in milestones from `IMPLEMENTATION_PLAN.md`.
5. Before each milestone, list files to be changed and acceptance criteria.
6. After each milestone, run available type checks, lint, tests, and build; fix regressions before moving on.
7. Keep schema migrations versioned and repeatable if a database is used.
8. Add tests for stock reservation, supplier eligibility, order split, route capacity, and idempotent order creation.
9. Keep documentation updated when behavior changes.
10. At completion, provide exact setup commands, demo credentials, test results, known limitations, and a 3-minute presentation flow.

## Code quality
- TypeScript strict mode where feasible.
- Avoid `any` unless justified and isolated.
- Use typed domain models and a service/repository boundary so local demo data can later be replaced by Supabase/API implementations.
- Use integer paise or a decimal-safe money representation; do not use floating-point arithmetic for authoritative money totals.
- Use stable IDs and timestamps.
- Make order confirmation and inventory reservation atomic when using a real database.
- Keep order, fulfillment, shipment, route, and payment states separate.
- Use accessible labels, keyboard-operable controls, responsive layouts, and visible loading/empty/error states.

## Demo labels
Use labels such as:
- “Sample data”
- “Simulated payment”
- “Demo route plan”
- “Estimated freight”
- “Prototype only — not a tax invoice”

## Definition of done
A feature is done only when its UI, domain logic, error states, tests, and documentation are aligned. A screenshot alone does not count as functional completion.

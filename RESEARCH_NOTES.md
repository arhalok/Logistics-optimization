# Research Notes and Evidence Policy

## Purpose
Keep product assumptions and external evidence separate. This prototype can be demonstrated using synthetic data; any claims about the Indian kirana market, supplier behavior, savings, legal requirements or competitor capabilities need source-backed validation before appearing as facts in a pitch.

## Research questions for the team
1. How do target kirana stores currently procure FMCG products: direct brands, wholesalers, distributors, C&F agents, digital B2B apps, or a mix?
2. What are typical minimum order quantities, case-pack requirements, delivery windows, payment terms and return policies for the categories selected for the pilot?
3. How do local distributors verify territory/product authorization?
4. Which costs can realistically be shared across multiple retailer deliveries, and who pays them?
5. What supplier/retailer density is needed to make consolidation useful?
6. Which competitor features are confirmed by current product documentation versus marketing claims?
7. Which tax, invoicing, payment, privacy and movement rules apply to the actual proposed business model?

## Source hierarchy
Prefer:
1. Official government/regulator documentation for legal and tax questions.
2. Official product documentation for technology capabilities.
3. Company documentation and product terms for competitor features.
4. Reputable research/industry reports with methodology and publication date.
5. Interviews or surveys with clearly described sample size and limitations.
6. General articles only as secondary context.

## Research log template
| Claim or question | Finding | Source URL/title | Publisher | Published/accessed date | Evidence quality | How it affects design |
|---|---|---|---|---|---|---|
| Example: route matrix support | Fill after checking current docs | | | | | |

## Evidence labels
- **Verified:** supported by a current authoritative source or documented test.
- **Observed:** collected from interviews or prototype test; state sample size.
- **Assumption:** plausible but not yet validated.
- **Synthetic demo input:** invented solely to demonstrate behavior.
- **Decision:** product choice, not an external fact.

## Technical reference starting points
- Next.js documentation: https://nextjs.org/docs
- TypeScript handbook: https://www.typescriptlang.org/docs/
- Supabase documentation: https://supabase.com/docs
- OSRM API documentation: https://project-osrm.org/docs/
- VROOM project/documentation: https://github.com/VROOM-Project/vroom
- OpenStreetMap copyright and attribution: https://www.openstreetmap.org/copyright

Check current versions and terms at implementation time. Do not assume a public demo endpoint has production-grade availability, service levels or unrestricted usage.

## Pitch discipline
Do not state “saves 30%”, “98% on-time”, “AI optimized”, “compliant with GST”, or similar claims unless the team can show the calculation, test, evidence and scope. For hackathon demonstration, use phrases such as “in this synthetic scenario, the route estimate is X versus the defined baseline Y”.

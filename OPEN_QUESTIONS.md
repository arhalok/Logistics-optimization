# Open Questions and Explicit Assumptions

This document prevents assumptions from being mistaken for confirmed requirements.

| Question | Prototype default | Risk if wrong | Status |
|---|---|---|---|
| Who is seller of record? | Do not decide for production; show supplier allocation and illustrative order summary only | Invoices, tax, liability and returns depend on it | Open |
| Who invoices the retailer? | Prototype invoice-like summary labelled “not a tax invoice” | Incorrect invoice treatment | Open |
| Who collects payment? | Simulated payment status only | Settlement, compliance and refund complexity | Open |
| Is split fulfillment allowed? | Yes for demo only when explicitly shown to retailer | Multiple delivery fees and partial orders | Confirmed for prototype behavior; commercial policy open |
| What is the real supplier authorization source? | Seeded authorization records labelled synthetic | Counterfeit/unauthorized supply risk | Open |
| Which freight allocation is commercially accepted? | Weight-based if all weights exist; otherwise equal per stop with disclosure | Perceived unfairness or inaccurate margin | Open |
| What delivery SLA is promised? | Display estimate only; no guarantee | Customer trust and liability | Open |
| Which routing provider is configured? | Deterministic demo planner until OSRM/VROOM is verified | Demo could misrepresent route quality | Open |
| Which city is the pilot? | Use sample Jaipur-area scenario for demo only | Operational assumptions may not generalize | Open |
| Is credit enabled? | No credit/BNPL feature in MVP | Credit risk and collections | Deferred |
| Are returns implemented? | Show only if core flow is stable; no blanket 7-day rule | FMCG expiry/damage policy differs by seller/category | Deferred |
| Are tax figures accurate? | Omit or label illustrative; no compliance claim | Legal/tax exposure | Open |

## Decision process
For every resolved question, add:
- decision
- rationale
- owner/approver
- date
- affected requirements/schema/APIs
- migration or UI changes required

Record approved decisions in `DECISIONS.md`.

# Security, Privacy and Compliance Boundaries

## Hackathon security minimum
- Never commit API keys, database passwords, service-role keys, or payment secrets.
- Use `.env.local` locally and commit only `.env.example`.
- Validate authorization on the server if a backend is used.
- Apply database row-level security for tenant-owned data if Supabase/PostgreSQL is used.
- Limit demo role switching to an explicit demo environment; do not confuse it with production auth.
- Use synthetic names, addresses, phone numbers and GST-like identifiers only if clearly marked fake. Prefer not to use real personal data.
- Avoid collecting sensitive data that is not required for the prototype.
- Do not store raw card numbers, CVV, UPI PINs or bank credentials.
- Log critical actions without leaking secrets or unnecessary personal data.

## Production topics requiring separate review
- Seller-of-record, invoicing and contract structure.
- GST registration, invoice contents, marketplace obligations and any applicable TCS/TDS treatment.
- E-way bill applicability based on actual transaction, goods, value and movement facts.
- Payment aggregator/provider rules, refunds and settlement.
- Retailer and supplier KYC/verification.
- Data protection, notice/consent, retention, deletion and incident response.
- Product-specific handling, expiry, damage, recall and returns policies.
- Carrier contracts, insurance and proof-of-delivery retention.

This document is not legal, tax, or accounting advice. The prototype must not claim compliance certification. Verify current rules with official sources and qualified professionals before a live pilot.

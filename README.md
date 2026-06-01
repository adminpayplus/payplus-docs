# payplus-docs

PayPlus development documentation repository.

PayPlus is a controlled bill, fee, rent, invoice, and approved-obligation payment application. This repository stores the human-readable source documents, technical specifications, AI build-execution materials, and traceability records used to guide development.

## Documentation Layers

```text
Human source docs
-> Technical and operational specifications
-> AI build-execution materials
-> Code, tests, migrations, and release evidence
-> Traceability updates
```

## Key Folders

- `docs/00-foundation/`: governance, product positioning, business model, regulatory, and compliance foundation.
- `docs/01-product/`: PRD, user journeys, disclosures, notifications, and user-facing behavior.
- `docs/02-payment-domain/`: payment, payout, reconciliation, refund, cancellation, and chargeback behavior.
- `docs/03-bill-verification/`: bill category, document AI/OCR, evidence, and payee verification.
- `docs/04-growth-ecosystem/`: promotion engine, coupons, vouchers, referrals, membership, and partner offers.
- `docs/05-risk-compliance-privacy/`: AML, anti-cashout, fraud, privacy, and retention.
- `docs/06-engineering/`: architecture, APIs, data model, transaction states, and audit events.
- `docs/07-security-access-control/`: security, tokenization, authentication, access control, and admin controls.
- `docs/08-qa-release-operations/`: testing, UAT, go-live, monitoring, incidents, and admin operations.
- `docs/09-ai-build-execution/`: AI-agent implementation context and prompt materials derived from approved docs.
- `docs/traceability/`: requirements, controls, tests, decisions, and open-question linkage.

See `AGENTS.md` for AI assistant workflow rules.

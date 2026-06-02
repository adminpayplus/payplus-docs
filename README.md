# payplus-docs

PayPlus development documentation repository.

PayPlus is a controlled bill, fee, rent, invoice, domestic helper, driver, personal service, and approved-obligation payment application. This repository stores the human-readable source documents, technical specifications, AI build-execution materials, and traceability records used to guide development.

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
- `docs/05-risk-compliance-privacy/`: AML, anti-cashout, fraud, privacy, data classification, masking, approved-purpose access, and retention.
- `docs/06-engineering/`: architecture, APIs, data model, field metadata, lineage, transaction states, and audit events.
- `docs/07-security-access-control/`: security, tokenization, authentication, access control, and admin controls.
- `docs/08-qa-release-operations/`: testing, UAT, go-live, monitoring, incidents, and admin operations.
- `docs/09-ai-build-execution/`: reserved AI-agent implementation context and prompt materials derived from approved docs. Do not treat legacy context files as current source of truth unless regenerated.
- `docs/traceability/`: requirements, controls, tests, decisions, and open-question linkage.

Start with `docs/README.md` for document navigation and `AGENTS.md` for AI assistant workflow rules.

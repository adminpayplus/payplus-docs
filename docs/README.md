
# PayPlus Documentation Index

This folder contains the PayPlus documentation set.

Use `docs/00-foundation/doc-00-documentation-governance.md` as the documentation governance source of truth. Use `AGENTS.md` for AI assistant workflow rules.

## Current Baseline

| Layer | Status | Notes |
| --- | --- | --- |
| Human source documents | Active for DOC-00 to DOC-15 | Founder Working Baseline unless a document says otherwise. |
| Technical and operational specifications | Planned or partial for DOC-16 to DOC-22 | DOC-18 now contains the current Founder Working Baseline for data model, transaction state, audit event, reporting, and AI-ready data-engine requirements. Other partial placeholders are acceptable until drafted. |
| AI build-execution materials | Reserved | Regenerate from current human and technical specs before use. |
| Traceability | Starter registers | Expand when stable requirement/control/test IDs are finalized. |

## Folder Map

| Folder | Purpose |
| --- | --- |
| `00-foundation/` | Governance, product positioning, business model, regulatory assessment, and compliance control framework. |
| `01-product/` | Master PRD, UX flows, disclosures, notifications, and user-facing behavior. |
| `02-payment-domain/` | Payment requests, funding, settlement, payout, reconciliation, refunds, cancellations, disputes, and chargebacks. |
| `03-bill-verification/` | Bill category, evidence, AI/OCR, extracted data, duplicate evidence, and payee verification requirements. |
| `04-growth-ecosystem/` | Promotion engine, coupons, vouchers, discount codes, referrals, membership, partner rewards, and campaign controls. |
| `05-risk-compliance-privacy/` | AML, anti-cashout, fraud, dynamic auth, privacy, data classification, approved-purpose access, masking, and retention. |
| `06-engineering/` | Technical architecture, API/integration specs, data model, transaction states, audit events, and OpenAPI placeholder. |
| `07-security-access-control/` | Security, tokenization, authentication, PCI, access control, and admin control specs. |
| `08-qa-release-operations/` | Testing, UAT, go-live, monitoring, incidents, operations, and admin dashboard workflow. |
| `09-ai-build-execution/` | Reserved AI execution materials. Legacy context files are non-authoritative unless refreshed. |
| `99-isms-policies/` | ISMS and security policy library. |
| `traceability/` | Requirements traceability and open-question registers. |

## Reading Order

1. `DOC-00` for governance and source-of-truth rules.
2. `DOC-01` to `DOC-04` for PayPlus foundation, business, regulatory, and control baseline.
3. `DOC-05` to `DOC-08` for product, UX, disclosure, notification, and communication behavior.
4. `DOC-09` to `DOC-11` for payment, payout, reconciliation, refund, cancellation, dispute, and chargeback behavior.
5. `DOC-12` to `DOC-15` for evidence verification, promotion engine, risk controls, privacy, data classification, and retention.
6. `DOC-16` to `DOC-22` when drafted for technical architecture, integrations, data model, security, testing, monitoring, and admin operations.

## AI/Data-Engine Alignment

The recent AI/data-engine strategy update is traceable through:

- `06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md` as the technical baseline for structured events, metadata, lineage, model-use eligibility, audit events, and reporting.
- `04-growth-ecosystem/payplus-data-strategy-ai-marketing-research.md` as supporting research context, not a source-of-truth requirements document.
- `traceability/open-questions-register.md` item `OQ-XDOC-012` for remaining data-engine, model governance, partner reporting, and external activation decisions.

## Current Product Baseline

PayPlus is a controlled, evidence-backed, payer-authorized payment service for eligible bills, fees, rent, invoices, domestic helper, driver, personal service, and approved obligations.

PayPlus is not a wallet, stored-value account, unrestricted P2P transfer app, cashout product, remittance product, lending product, or open money-request marketplace.

Bill payments, fee payments, rent/tenancy payments, payee-created requests, multi-card payment, domestic helper payments, driver payments, personal service payments, and user payment instructions are MVP scope where supported by acceptable evidence and enabled controls.

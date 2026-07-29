
# PayPlus Documentation Index

This folder contains the PayPlus documentation set.

Use `docs/00-foundation/doc-00-documentation-governance.md` as the documentation governance and ranked source-of-truth authority. Use `AGENTS.md` as the repository Operating Contract and Routing Layer. Use the [`PayPlus Platform Design Principles`](00-foundation/payplus-platform-design-principles.md) for durable platform doctrine and the [`Outcome, Resolution, Message and Notification Framework`](00-foundation/payplus-outcome-message-notification-framework.md) for the detailed Outcome → Resolution → Message/CTA/Notification chain.

Enter the operating architecture through the [`Documentation System`](documentation-system/README.md) and its independent [`Documentation Architecture Map`](documentation-system/documentation-architecture-map.md). All documentation work uses the [`Documentation Development Workflow`](documentation-system/payplus-documentation-development-workflow.md), the sole owner of the complete Documentation Lifecycle and its gates. The directory README routes to the Parallel Procedure and the DOC-07 and Prototype Specialist Guides without duplicating their rules. Substantive commits are recorded in [`changelog/changelog.md`](changelog/changelog.md) and [`decision-log/decisionlog.md`](decision-log/decisionlog.md).

## Current Baseline

| Layer | Status | Notes |
| --- | --- | --- |
| Human source documents | Active for DOC-00 to DOC-15 | Founder Working Baseline unless a document says otherwise. DOC-06 is now a parent family with DOC-06A to DOC-06D child documents. |
| Technical and operational specifications | Planned or partial for DOC-16 to DOC-22 | DOC-18 now contains the current Founder Working Baseline for data model, transaction state, audit event, reporting, and AI-ready data-engine requirements. Other partial placeholders are acceptable until drafted. |
| AI build-execution materials | Reserved | Regenerate from current human and technical specs before use. |
| Traceability | Starter registers | Expand when stable requirement/control/test IDs are finalized. |

## Folder Map

| Folder | Purpose |
| --- | --- |
| `00-foundation/` | Governance, product positioning, business model, regulatory assessment, and compliance control framework. |
| `documentation-system/` | Documentation operating architecture, canonical lifecycle workflow, optional procedure, specialist guides, and architecture navigation. |
| `01-product/` | Master PRD, DOC-06 UX/navigation child documents, disclosures, notifications, and user-facing behavior. |
| `02-payment-domain/` | Payment requests, funding, settlement, payout, reconciliation, refunds, cancellations, disputes, and chargebacks. |
| `03-bill-verification/` | Bill category, evidence, AI/OCR, extracted data, duplicate evidence, and payee verification requirements. |
| `04-growth-ecosystem/` | Promotion engine, coupons, vouchers, discount codes, referrals, membership, partner rewards, and campaign controls. |
| `05-risk-compliance-privacy/` | AML, anti-cashout, fraud, dynamic auth, privacy, data classification, approved-purpose access, masking, and retention. |
| `06-engineering/` | Technical architecture, API/integration specs, data model, transaction states, audit events, and OpenAPI placeholder. |
| `07-security-access-control/` | Security, tokenization, authentication, PCI, access control, and admin control specs. |
| `08-qa-release-operations/` | Testing, UAT, go-live, monitoring, incidents, operations, and admin dashboard workflow. |
| `09-ai-build-execution/` | Reserved AI execution materials. Legacy context files are non-authoritative unless refreshed. |
| `99-isms-policies/` | ISMS and security policy library. |
| `changelog/` | Append-only documentation delivery history linked to substantive commits. |
| `decision-log/` | Append-only accepted decision records linked to owning documents and substantive commits. |
| `diagrams/` | Governed route, product-structure, and user-flow visual references. |
| `glossary/` | Controlled PayPlus terminology and source-owner references. |
| `prototypes/` | Prototype register. Current and archived artifacts appear only when registered under the Prototype Design and Validation Specialist Guide and governed through the canonical Documentation Development Workflow. |
| `traceability/` | Requirements traceability, route register, open-question register, and status-display alignment references. |

## Reading Order

1. `DOC-00` for governance and source-of-truth rules.
2. `DOC-01` to `DOC-04` for PayPlus foundation, business, regulatory, and control baseline.
3. `DOC-05` to `DOC-08` for product, UX, disclosure, notification, and communication behavior. Read `DOC-06` as the parent UX family map, then `DOC-06A` to `DOC-06D` for core journeys, navigation/route taxonomy, Bills/rent/tenancy UX, and UX acceptance/test mapping.
4. `DOC-09` to `DOC-11` for payment, payout, reconciliation, refund, cancellation, dispute, and chargeback behavior.
5. `DOC-12` to `DOC-15` for evidence verification, promotion engine, risk controls, privacy, data classification, and retention.
6. `DOC-16` to `DOC-22` when drafted for technical architecture, integrations, data model, security, testing, monitoring, and admin operations.

For user-facing status labels across checkout, activity, receipts, statements, notifications, Bills/rent surfaces, and future admin display, also check `traceability/status-display-reference-matrix.md`. The matrix aligns display labels only; domain documents own system status meaning and DOC-18 owns the future canonical status/event taxonomy.

For product destination identity, parentage, type, ownership, and definition status, use `traceability/route-register.md`. Route behavior remains owned by the applicable DOC-06 family or domain document.

## AI/Data-Engine Alignment

The recent AI/data-engine strategy update is traceable through:

- `06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md` as the technical baseline for structured events, metadata, lineage, model-use eligibility, audit events, and reporting.
- `04-growth-ecosystem/payplus-data-strategy-ai-marketing-research.md` as supporting research context, not a source-of-truth requirements document.
- `traceability/open-questions-register.md` item `OQ-XDOC-012` for remaining data-engine, model governance, partner reporting, and external activation decisions.

## Current Product Baseline

PayPlus is a controlled, evidence-backed, payer-authorized payment service for eligible bills, fees, rent, invoices, domestic helper, driver, personal service, and approved obligations.

PayPlus is not a wallet, stored-value account, unrestricted P2P transfer app, cashout product, remittance product, lending product, or open money-request marketplace.

Bill payments, fee payments, rent/tenancy payments, payee-created requests, multi-card payment, domestic helper payments, driver payments, personal service payments, and user payment instructions are MVP scope where supported by acceptable evidence and enabled controls.

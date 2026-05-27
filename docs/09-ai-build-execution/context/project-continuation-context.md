# project-continuation-context.md

## Project

PayPlus — a controlled bill, rent, fee, and approved-payee payment application.

PayPlus is intended to enable eligible users to pay eligible real-world bills or approved payment obligations using supported payment methods, potentially including card-funded payments and future multi-source payment flows, while avoiding wallet, stored-value, unrestricted P2P transfer, remittance, cashout, or cash-advance behavior unless separately assessed and approved.

The documentation repository is being developed as a professional fintech/product/payment/compliance/risk/security/operations/engineering documentation suite, with an additional AI build-execution layer for agentic coding and vibe-coding workflows.

---

## Current Date

2026-05-27

---

## Current Repository Structure

The repository has been restructured according to the combined professional documentation plus AI build-execution model.

Current structure:

```text
payplus-docs/
├── docs/
│   ├── 00-foundation/
│   │   ├── doc-00-documentation-governance.md
│   │   ├── doc-01-project-charter-product-positioning.md
│   │   ├── doc-02-business-model-unit-economics.md
│   │   ├── doc-03-regulatory-psp-acquirer-assessment.md
│   │   └── doc-04-compliance-certification-roadmap-control-framework.md
│   ├── 01-product/
│   │   ├── doc-05-master-prd-feature-requirement-index.md
│   │   ├── doc-06-user-journey-ux-flow-service-blueprint.md
│   │   ├── doc-07-content-disclosure-user-authorization-spec.md
│   │   └── doc-08-notification-receipt-communication-spec.md
│   ├── 02-payment-domain/
│   │   ├── doc-09-payment-request-multi-funding-source-settlement.md
│   │   ├── doc-10-payout-reconciliation.md
│   │   └── doc-11-refund-cancellation-chargeback.md
│   ├── 03-bill-verification/
│   │   └── doc-12-bill-category-document-ai-ocr-payee-verification-spec.md
│   ├── 04-growth-ecosystem/
│   │   └── doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md
│   ├── 05-risk-compliance-privacy/
│   │   ├── doc-14-aml-anti-cashout-fraud-dynamic-auth-risk-control-spec.md
│   │   └── doc-15-privacy-data-protection-record-retention-spec.md
│   ├── 06-engineering/
│   │   ├── api/
│   │   │   └── openapi.yaml
│   │   ├── doc-16-technical-architecture-spec.md
│   │   ├── doc-17-api-third-party-integration-spec.md
│   │   └── doc-18-data-model-transaction-state-audit-event-spec.md
│   ├── 07-security-access-control/
│   │   └── doc-19-security-tokenization-authentication-admin-control-spec.md
│   ├── 08-qa-release-operations/
│   │   ├── doc-20-testing-uat-golive-checklist.md
│   │   └── doc-21-monitoring-incident-response-operational-sops.md
│   ├── 09-ai-build-execution/
│   │   ├── 01-structured-prd.md
│   │   ├── 02-ui-prototype-prd.md
│   │   ├── 03-technical-architecture-prd.md
│   │   ├── 04-development-task-list.md
│   │   ├── 05-agent-coding-rules.md
│   │   ├── 06-feature-build-sequence.md
│   │   ├── 07-definition-of-done.md
│   │   ├── 08-test-generation-instructions.md
│   │   ├── 09-ai-prompt-pack.md
│   │   ├── 10-agent-context-index.md
│   │   ├── context/
│   │   │   ├── bill-verification-context.md
│   │   │   ├── payment-core-context.md
│   │   │   ├── project-continuation-context.md
│   │   │   ├── promotion-engine-context.md
│   │   │   ├── refund-chargeback-context.md
│   │   │   └── security-context.md
│   │   └── README.md
│   ├── 99-isms-policies/
│   │   ├── 99-01-information-security-policy.md
│   │   ├── 99-02-acceptable-use-policy.md
│   │   ├── 99-03-access-control-policy.md
│   │   ├── 99-04-cryptography-policy.md
│   │   ├── 99-05-data-classification-handling-policy.md
│   │   ├── 99-06-asset-management-policy.md
│   │   ├── 99-07-supplier-vendor-security-policy.md
│   │   ├── 99-08-hr-security-policy.md
│   │   ├── 99-09-physical-environmental-security-policy.md
│   │   ├── 99-10-change-management-policy.md
│   │   ├── 99-11-vulnerability-management-policy.md
│   │   ├── 99-12-secure-development-policy.md
│   │   ├── 99-13-incident-management-policy.md
│   │   ├── 99-14-business-continuity-disaster-recovery-policy.md
│   │   ├── 99-15-logging-monitoring-policy.md
│   │   ├── 99-16-backup-restore-policy.md
│   │   ├── 99-17-risk-assessment-methodology.md
│   │   ├── 99-18-statement-of-applicability.md
│   │   ├── 99-19-internal-audit-programme.md
│   │   ├── 99-20-management-review-procedure.md
│   │   └── README.md
│   ├── change-requests/
│   │   └── README.md
│   ├── changelog/
│   │   └── changelog.md
│   ├── decision-log/
│   │   └── README.md
│   ├── diagrams/
│   │   └── README.md
│   ├── glossary/
│   │   └── glossary.md
│   ├── README.md
│   ├── templates/
│   │   ├── adr-template.md
│   │   ├── api-spec-template.md
│   │   ├── change-request-template.md
│   │   ├── core-spec-template.md
│   │   ├── rulebook-template.md
│   │   └── test-case-template.md
│   └── traceability/
│       ├── open-questions-register.md
│       └── requirements-traceability-matrix.md
└── README.md
```

---

## Structure Change Summary

The repository was updated to combine:

1. **Professional product/payment/compliance documentation**
2. **AI-agent-friendly build execution documentation**

This change was based on the clarification that the original structure from Specialist A was strong for professional fintech documentation, while Specialist B’s recommendation was useful for agentic coding and vibe-coding execution.

The new structure preserves both purposes.

---

## Structure Logic

### `00-foundation/`

Purpose:

- Governance, project charter, business model, regulatory assessment, PSP/acquirer assessment, compliance roadmap, and launch-control framework.

Role:

- Establishes the source-of-truth foundation for product, compliance, partner, commercial, and launch-readiness decisions.

Current important docs:

- `DOC-00`
- `DOC-01`
- `DOC-02`
- `DOC-03`
- `DOC-04`

---

### `01-product/`

Purpose:

- Product requirements, user journeys, UX flows, disclosures, authorization, notifications, receipts, and communication rules.

Role:

- Converts foundation strategy and compliance requirements into user-facing and internal product requirements.

Current important docs:

- `DOC-05`
- `DOC-06`
- `DOC-07`
- `DOC-08`

---

### `02-payment-domain/`

Purpose:

- Payment request, funding source, settlement, payout, reconciliation, refund, cancellation, chargeback, and dispute specifications.

Role:

- Defines the detailed payment operating model and transaction lifecycle.

Current important docs:

- `DOC-09`
- `DOC-10`
- `DOC-11`

---

### `03-bill-verification/`

Purpose:

- Bill category rules, document upload, AI/OCR extraction, bill validation, payee verification, and evidence requirements.

Role:

- Ensures PayPlus remains anchored to real bills and approved payment obligations.

Current important doc:

- `DOC-12`

---

### `04-growth-ecosystem/`

Purpose:

- Promotions, coupons, vouchers, referrals, memberships, and campaign rules.

Role:

- Defines optional or gated commercial-growth features without compromising compliance, refund, fraud, or accounting integrity.

Current important doc:

- `DOC-13`

---

### `05-risk-compliance-privacy/`

Purpose:

- AML, anti-cashout, fraud, sanctions, dynamic authentication, privacy, data protection, and record retention.

Role:

- Converts risk and compliance expectations into operational product controls.

Current important docs:

- `DOC-14`
- `DOC-15`

---

### `06-engineering/`

Purpose:

- Technical architecture, API, third-party integration, OpenAPI spec, data model, transaction states, audit events, and reporting design.

Role:

- Converts product and payment requirements into implementation architecture.

Current important docs:

- `DOC-16`
- `DOC-17`
- `DOC-18`
- `api/openapi.yaml`

---

### `07-security-access-control/`

Purpose:

- Security, tokenization, authentication, admin controls, access control, and PCI-related product security requirements.

Role:

- Defines secure access and payment-data handling requirements.

Current important doc:

- `DOC-19`

---

### `08-qa-release-operations/`

Purpose:

- Testing, UAT, go-live checklist, monitoring, incident response, operational SOPs, and runbooks.

Role:

- Converts product, compliance, security, and payment requirements into release-readiness and operating procedures.

Current important docs:

- `DOC-20`
- `DOC-21`

---

### `09-ai-build-execution/`

Purpose:

- AI-friendly implementation layer for agentic coding and vibe-coding.

Role:

- Translates human source-of-truth documents into structured, task-based, machine-readable development instructions.

Important principle:

```text
09-ai-build-execution is derived from 00–08 and must not override or contradict 00–08.
```

Core files:

- `01-structured-prd.md`
- `02-ui-prototype-prd.md`
- `03-technical-architecture-prd.md`
- `04-development-task-list.md`
- `05-agent-coding-rules.md`
- `06-feature-build-sequence.md`
- `07-definition-of-done.md`
- `08-test-generation-instructions.md`
- `09-ai-prompt-pack.md`
- `10-agent-context-index.md`

---

### `09-ai-build-execution/context/`

Purpose:

- Compressed AI memory and domain-specific context.

Role:

- Replaces the older standalone `ai-context/` folder by moving AI context under the AI execution layer.

Current context files:

- `project-continuation-context.md`
- `payment-core-context.md`
- `bill-verification-context.md`
- `promotion-engine-context.md`
- `refund-chargeback-context.md`
- `security-context.md`

Logic:

```text
09/context = what AI should remember.
09/*.md = what AI should execute.
00–08 = what humans approve as source of truth.
```

---

### `99-isms-policies/`

Purpose:

- Information security management system policy library.

Role:

- Supports future security maturity, partner review, internal controls, audit readiness, and certification preparation.

Current contents include:

- Information security policy
- Acceptable use policy
- Access control policy
- Cryptography policy
- Data classification and handling policy
- Asset management policy
- Vendor security policy
- HR security policy
- Physical/environmental security policy
- Change management policy
- Vulnerability management policy
- Secure development policy
- Incident management policy
- Business continuity/disaster recovery policy
- Logging and monitoring policy
- Backup and restore policy
- Risk assessment methodology
- Statement of applicability
- Internal audit programme
- Management review procedure

---

### Supporting Folders

| Folder | Purpose |
| --- | --- |
| `change-requests/` | Controlled change-request workflow. |
| `changelog/` | Chronological documentation/product change history. |
| `decision-log/` | ADRs and major product, architecture, compliance, and operating decisions. |
| `diagrams/` | Architecture, flow, sequence, state, and service blueprint diagrams. |
| `glossary/` | Shared terminology. |
| `templates/` | Reusable documentation and process templates. |
| `traceability/` | Requirements traceability matrix and open questions register. |

---

## Current Documentation Strategy

The current documentation strategy is:

```text
00–08 = Human source-of-truth documentation.
09 = AI build-execution package derived from 00–08.
09/context = compressed AI memory and continuation context.
99 = ISMS/security policy library.
traceability = requirement, control, and open-question linkage.
change-requests = controlled change workflow.
decision-log = formal decision and ADR tracking.
```

This structure intentionally avoids mixing human approval documents with AI coding prompts.

The intended flow is:

```text
Human source docs → AI execution docs → controlled implementation tasks → tests/evidence → traceability updates.
```

---

## Working Style

The user is proceeding document by document.

Preferred response style:

- Produce the complete document in Markdown.
- Wrap the full document in a single Markdown code block when requested.
- Use YAML-style front matter for formal docs.
- Use stable document IDs.
- Include structured sections.
- Include tables where useful.
- Avoid overly casual commentary.
- Do not add unnecessary legal disclaimers unless they belong in the document.
- Keep documents internally consistent with prior docs.
- Treat PayPlus as a serious fintech/payments product.
- Favor practical launch-readiness, compliance-readiness, partner-readiness, security-readiness, operational-readiness, and AI-build-readiness.
- Use `TBD`, `Open`, or explicit placeholders when factual product decisions are not yet known.
- Maintain traceability to upstream and downstream documents.
- Where a document belongs to `09-ai-build-execution`, make it explicit that it is derived from the human source-of-truth documents and must not override them.

---

## Product Context

PayPlus appears to involve:

- User onboarding
- User account/profile
- User eligibility
- Bill/rent/fee payment initiation
- Approved bill categories
- Bill document upload
- OCR or AI-assisted bill extraction
- Bill validation
- Payee verification
- Possible landlord or biller verification
- Supported funding source selection
- Tokenized card or other payment method support
- Possible future multi-card or multi-source funding
- Payment quote
- Service fee calculation
- User disclosure and authorization
- PSP/acquirer processing
- Payment status tracking
- Payout to billers/payees
- Settlement
- Reconciliation
- Refunds
- Cancellations
- Chargebacks
- Disputes
- Receipts
- Notifications
- Promotions/coupons/referrals/membership
- Admin console
- Risk controls
- AML/sanctions screening where applicable
- Anti-cashout controls
- Privacy and record retention
- PCI/security/tokenization considerations
- Audit logs
- Operational monitoring
- Incident response
- AI-assisted development workflow

No final product, legal, regulatory, jurisdictional, PSP/acquirer, MCC, fee, payout, or funds-flow conclusion has been provided yet.

---

## Document Suite Conventions

Formal human-readable documents should generally include:

1. YAML front matter:
   - `document_id`
   - `title`
   - `version`
   - `status`
   - `owner`
   - `reviewers`
   - `approvers`
   - `last_updated`
   - `classification`
   - `related_documents`

2. Main heading:
   - `# DOC-XX — Title`

3. Core sections appropriate to the document.

4. Structured tables for:
   - Requirements
   - Gates
   - Controls
   - Assumptions
   - Constraints
   - Dependencies
   - Risks
   - Open questions
   - Acceptance criteria
   - Version history

5. Version history with prior drafts where applicable.

6. Cross-document consistency:
   - Use references like `DOC-03`, `DOC-04`, etc.
   - Ensure downstream document impacts remain aligned.
   - If the document feeds the AI execution layer, include references to the corresponding `09-ai-build-execution` documents.

AI build-execution documents should generally include:

1. Purpose and source-of-truth statement.
2. Source documents.
3. Scope.
4. Structured, machine-readable sections.
5. Requirement IDs, task IDs, screen IDs, API references, or test IDs where useful.
6. Explicit AI guardrails.
7. Dependencies.
8. Acceptance criteria.
9. Definition of Done.
10. Open questions.
11. Traceability back to `00–08`.

---

## Completed or Drafted Documents

### `DOC-00 — Documentation Governance`

Status: Previously drafted.

Likely role:

- Governs document suite.
- Defines ownership, review, approvals, versioning, document taxonomy, change control, and maintenance process.

Use as the governance anchor for all subsequent docs.

---

### `DOC-01 — Project Charter & Product Positioning`

Status: Previously drafted.

Likely role:

- Defines PayPlus project purpose, scope, product thesis, stakeholders, objectives, and positioning.
- Sets strategic foundation.

---

### `DOC-02 — Business Model & Unit Economics`

Status: Completed/reframed.

Important framing:

- PayPlus monetizes through service fees and possibly other revenue streams.
- Unit economics depend on:
  - Processing fees
  - Interchange/scheme/acquirer costs
  - Payout costs
  - Refund costs
  - Chargeback costs
  - Fraud losses
  - Reserves/holdbacks
  - Support costs
  - Promotion costs
  - Financing or prefunding costs
  - Settlement timing
- Must model gross margin, contribution margin, break-even, and sensitivity by category/payment method.
- Connects heavily to `DOC-03`, `DOC-04`, `DOC-09`, `DOC-10`, `DOC-11`, `DOC-14`, and `DOC-18`.

---

### `DOC-03 — Regulatory, PSP & Acquirer Assessment`

Status: Completed as version `0.2.0`.

Important framing:

- Foundation assessment framework.
- Does not provide final legal advice or final regulatory conclusions.
- Used before launch, new jurisdiction, new bill category, new payee type, new payment method, multi-card launch, funds-flow change, payout change, pricing/fee change, new PSP/acquirer/provider, material risk changes, or regulatory/card-network changes.

Important concepts to preserve:

- No product flow should launch without documented regulatory role assessment.
- No unsupported category should launch without partner/legal/compliance approval.
- Funds-flow changes trigger reassessment.
- PSP/acquirer written confirmation is preferred.
- MCC/classification may affect cost, issuer behavior, user complaints, and legal/partner obligations.
- Multi-card/multi-source payment requires special review.
- Partner contracts must support refunds, chargebacks, reconciliation, settlement, reserves, reporting, and data/security obligations.

---

### `DOC-04 — Compliance Certification Roadmap & Control Framework`

Status: Completed/reframed as version `0.3.0`.

Important framing:

- PayPlus-specific compliance certification framework.
- Converts `DOC-03` outputs and other obligations into controls, gates, evidence, testing, and launch certification.
- “Compliance certification” is defined broadly as documented internal and partner-supported readiness, not necessarily a single external certificate.
- Strongly MVP-focused and launch-readiness oriented.

Important concepts to preserve:

- T0 controls are non-waivable launch blockers.
- T1 controls are critical launch controls.
- Compliance controls must become product and engineering requirements where applicable.
- MVP should remain conservative, narrow, and scope-specific.
- Product should avoid unsupported funds flows, unapproved categories, self-payments, risky categories, cross-border, FX, wallet/stored value, payout before funding certainty, and multi-card unless separately approved.
- Fee, timing, refund, role, and user-responsibility disclosures are launch-critical.
- Daily reconciliation is a launch blocker.
- Evidence repository and launch approval signatures are required.
- `DOC-20` should convert `DOC-04` controls into executable go/no-go checklist.
- `09-ai-build-execution` should convert T0/T1 controls into AI build requirements, task guardrails, acceptance criteria, and Definition of Done items.

---

### `DOC-05 — Master PRD & Feature Requirement Index`

Status: Drafted as version `0.1.0`.

Path:

```text
docs/01-product/doc-05-master-prd-feature-requirement-index.md
```

Last updated:

```text
2026-05-26
```

Important role:

`DOC-05` is now the master human-readable PRD and feature requirement index for PayPlus.

It establishes:

- Executive review and product alignment
- Product definition
- Product boundaries
- Prohibited product behaviors
- MVP product scope
- Candidate MVP bill categories
- Deferred and non-MVP scope
- User roles and personas
- Core user journeys
- Requirement taxonomy
- Requirement priority and criticality model
- Requirement status model
- Feature domain index
- Master requirement index
- Governance and scope requirements
- User account/profile/eligibility requirements
- Bill request/category/document requirements
- Payee requirements
- Quote/fee/disclosure/authorization requirements
- Payment/funding source requirements
- Multi-card/multi-source requirements
- Status/payout/lifecycle requirements
- Refund/cancellation/dispute/chargeback requirements
- Promotion requirements
- Risk/sanctions/fraud/anti-cashout requirements
- Admin/operations/support requirements
- Data/ledger/evidence/audit requirements
- Notification/receipt/communication requirements
- Security/privacy/access requirements
- Reporting/analytics requirements
- Non-functional requirements
- Compliance-critical product requirements
- Payment-app design requirements
- Commercial requirements
- UX/content requirements
- Admin/internal tooling requirements
- Data/evidence requirements
- Release/change-control requirements
- Traceability matrix
- Assumptions
- Constraints
- Dependencies
- Risks
- Downstream document impact
- Open questions
- Acceptance criteria
- Version history

Important `DOC-05` themes to preserve:

#### PayPlus Remains a Controlled Bill-Payment Product

PayPlus is not a general wallet, stored-value account, remittance product, unrestricted P2P app, cashout product, or cash-advance product.

#### Bill/Payment Obligation Anchoring Is Required

Product flows must remain tied to valid bills, approved categories, structured bill details, bill evidence, verified payees, or approved payment obligations.

#### Launch Scope Must Be Narrow and Configurable

MVP should launch only within approved jurisdiction, bill categories, payment methods, payout method, partner setup, and funds flow.

#### Multi-Card / Multi-Source Is Gated by Default

Multi-card or multi-source funding must remain disabled, deferred, or feature-gated unless separately approved through regulatory, PSP/acquirer, payment, reconciliation, refund, chargeback, risk, and operational review.

#### Fee and Authorization Disclosure Are T0 Requirements

Before authorization, the user must see:

- Bill amount
- Service fee
- Taxes if applicable
- Promotion discount if applicable
- Total amount charged
- PayPlus role
- Expected payment timing
- Refund/cancellation rules
- User responsibility

The system must capture durable authorization evidence.

#### Payee Verification Is Core to Anti-Cashout

Payout must not proceed until payee verification or approved payee exception conditions are satisfied.

#### Admin and Operations Tooling Is MVP-Critical

Admin review, manual review, payout exception handling, risk review, reconciliation support, refund handling, and evidence retrieval are not optional post-launch items.

#### Data and Evidence Are Product Requirements

PayPlus must support durable traceability across:

- User
- Bill
- Payee
- Quote
- Authorization
- Payment
- Risk decision
- Payout
- Refund
- Chargeback
- Promotion
- Reconciliation
- Communication
- Admin action

#### Reconciliation Remains a Launch Blocker

Daily reconciliation across PSP settlement, payout, fees, refunds, chargebacks, reserves, and ledger records is required.

#### DOC-05 Feeds the AI Build-Execution Layer

`DOC-05` should be a major source for:

- `09-ai-build-execution/01-structured-prd.md`
- `09-ai-build-execution/02-ui-prototype-prd.md`
- `09-ai-build-execution/04-development-task-list.md`
- `09-ai-build-execution/05-agent-coding-rules.md`
- `09-ai-build-execution/10-agent-context-index.md`

---

## Current Next Human Source Document

The next recommended human source-of-truth document is:

```text
docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md
```

### `DOC-06 — User Journey, UX Flow & Service Blueprint`

Expected purpose:

`DOC-06` should convert the master product requirements in `DOC-05` into user journeys, screen-level experience flows, service blueprints, internal operations touchpoints, decision points, failure states, and end-to-end lifecycle views.

It should cover:

- New user journey
- Returning user journey
- User onboarding
- Profile and eligibility flow
- Bill payment request journey
- Bill category selection flow
- Bill upload and OCR/review journey
- Bill validation flow
- Payee capture and verification journey
- Quote and service-fee review journey
- Disclosure and authorization journey
- Payment success/failure journey
- Manual review journey
- Risk review journey
- Payout processing journey
- Payout failure journey
- Refund/cancellation journey
- Dispute/chargeback support journey
- Receipt and notification touchpoints
- Admin and operations service blueprint
- Customer support touchpoints
- Finance/reconciliation touchpoints
- Risk/compliance intervention points

It should include UX states such as:

- Empty
- Loading
- Pending
- Draft
- Under review
- Blocked
- Action required
- Approved
- Rejected
- Payment failed
- Payout processing
- Payout failed
- Completed
- Cancelled
- Refunded
- Disputed
- Expired

It should define handoff points between:

- User app
- Admin console
- PSP/acquirer
- Payout provider
- OCR/document AI
- Risk engine
- Compliance review
- Operations review
- Support
- Finance
- Reconciliation
- Notification service
- Audit/evidence store

It should feed downstream documents:

- `DOC-07`
- `DOC-08`
- `DOC-09`
- `DOC-10`
- `DOC-11`
- `DOC-12`
- `DOC-14`
- `DOC-18`
- `DOC-20`
- `DOC-21`
- `09-ai-build-execution/02-ui-prototype-prd.md`

---

## Future AI Build-Execution Documents

After enough human source documents exist, populate the `09-ai-build-execution` documents.

### `09-ai-build-execution/01-structured-prd.md`

Purpose:

- AI-readable structured PRD.
- Derived mainly from `DOC-05`, `DOC-06`, `DOC-07`, `DOC-09`, `DOC-12`, `DOC-14`, `DOC-16`, `DOC-18`, and `DOC-19`.

Should include:

- Product summary
- User personas
- Feature modules
- User stories
- Functional requirements
- Non-functional requirements
- Business rules
- States
- Permissions
- Edge cases
- Acceptance criteria
- Out-of-scope items
- Traceability to source docs

---

### `09-ai-build-execution/02-ui-prototype-prd.md`

Purpose:

- Screen-by-screen UI specification for AI-assisted UI generation.

Should include:

- User app screens
- Admin console screens
- Route names
- Screen purpose
- Components
- Fields
- Field validation
- Loading states
- Empty states
- Error states
- Success states
- Responsive behavior
- Accessibility expectations
- Disclosure and consent points
- Acceptance criteria

Derived mainly from:

- `DOC-05`
- `DOC-06`
- `DOC-07`
- `DOC-08`
- `DOC-14`
- `DOC-19`

---

### `09-ai-build-execution/03-technical-architecture-prd.md`

Purpose:

- Implementation-focused architecture for AI coding agents.

Should include:

- Selected stack
- Frontend architecture
- Backend architecture
- Database architecture
- Payment integration pattern
- OCR/AI integration pattern
- Risk engine pattern
- Notification pattern
- Admin console architecture
- Observability
- Local development setup
- Environment assumptions
- Coding constraints
- Forbidden shortcuts

Derived mainly from:

- `DOC-16`
- `DOC-17`
- `DOC-18`
- `DOC-19`
- `DOC-21`

---

### `09-ai-build-execution/04-development-task-list.md`

Purpose:

- Practical task backlog for AI-assisted development.

Should include phases such as:

1. Repository and environment setup.
2. Authentication and user account.
3. User profile and eligibility.
4. Bill upload and verification.
5. Payee verification.
6. Payment request creation.
7. Funding source tokenization.
8. Payment authorization.
9. Payment processing.
10. Payout.
11. Reconciliation.
12. Refund and cancellation.
13. Chargeback support.
14. Notification and receipt.
15. Promotion engine.
16. Risk and fraud controls.
17. Admin console.
18. Security hardening.
19. Observability and incident response.
20. UAT and go-live readiness.

Each task should include:

- Task ID
- Title
- Goal
- Source documents
- Dependencies
- Implementation steps
- Data model changes
- API changes
- UI changes
- Tests
- Acceptance criteria
- Definition of Done
- AI agent guardrails

---

### `09-ai-build-execution/05-agent-coding-rules.md`

Purpose:

- Non-negotiable rules for AI coding agents.

Should include rules such as:

- Do not invent business rules.
- Do not bypass payment state machine.
- Do not store raw card data.
- Do not log tokens, credentials, PII, or sensitive payment details.
- Use integer minor units for all money values.
- Use idempotency keys for payment-mutating requests.
- All state changes must create audit events.
- Webhooks must verify signatures.
- External provider calls must include timeout, retry, and error handling.
- All admin actions must be permission-checked and audit-logged.
- If unclear, create an open question instead of inventing behavior.

---

### `09-ai-build-execution/06-feature-build-sequence.md`

Purpose:

- Defines safe build order for AI-assisted development.

Recommended MVP sequence:

1. Project skeleton.
2. Authentication.
3. User profile.
4. Bill category selection.
5. Bill upload.
6. Bill OCR/extraction.
7. Bill verification.
8. Payee verification.
9. Payment request draft creation.
10. Funding source tokenization.
11. Payment confirmation.
12. Payment processing.
13. Receipt generation.
14. Admin review console.
15. Basic reconciliation.
16. Refund request.
17. Notification.
18. Risk rules.
19. Logging and monitoring.
20. UAT readiness.

---

### `09-ai-build-execution/07-definition-of-done.md`

Purpose:

- Defines completion criteria for features and tasks.

Should require:

- Requirement linked to source document
- UI implemented where required
- API implemented where required
- Data migration included where required
- Validation implemented
- Permission checks implemented
- Audit logs implemented for sensitive actions
- Error handling implemented
- Tests added
- Documentation updated
- No sensitive data logged
- Acceptance criteria met

---

### `09-ai-build-execution/08-test-generation-instructions.md`

Purpose:

- Guides AI-generated test coverage.

Should include:

- Unit tests
- Integration tests
- API contract tests
- E2E tests
- Security tests
- Payment state-machine tests
- Webhook tests
- Reconciliation tests
- Refund tests
- Permission tests
- Failure-mode tests

---

### `09-ai-build-execution/09-ai-prompt-pack.md`

Purpose:

- Reusable prompt templates for AI development workflows.

Should include prompts for:

- Feature implementation
- Test generation
- Bug fix
- Refactor
- API generation
- UI screen generation
- Data model migration
- Security review
- Documentation update
- Open-question extraction

---

### `09-ai-build-execution/10-agent-context-index.md`

Purpose:

- Tells AI agents which documents to read for each type of task.

Example mapping:

- Payment request task:
  - `DOC-05`
  - `DOC-09`
  - `DOC-18`
  - `09/01-structured-prd.md`
  - `09/05-agent-coding-rules.md`

- Refund task:
  - `DOC-11`
  - `DOC-18`
  - `09/04-development-task-list.md`
  - `09/05-agent-coding-rules.md`

- Bill verification task:
  - `DOC-12`
  - `09/context/bill-verification-context.md`
  - `09/02-ui-prototype-prd.md`

- Security/auth task:
  - `DOC-19`
  - `99-03-access-control-policy.md`
  - `99-12-secure-development-policy.md`
  - `09/context/security-context.md`

---

## Recommended Future Plan

### Phase 1 — Repository Structure and Governance

Status: Mostly complete.

Completed:

- Adopted `09-ai-build-execution/`.
- Moved AI context purpose into `09-ai-build-execution/context/`.
- Preserved `00–08` as human source-of-truth docs.
- Preserved `99-isms-policies/`.
- Corrected prior naming issues:
  - `07-security-access-control/` has no trailing space.
  - `decision-log/` is correctly spelled.
  - `diagrams/` includes a README.
  - `adr-template.md` has a Markdown extension.

Remaining actions:

- Ensure `DOC-00` reflects the updated repository structure and AI execution layer.
- Ensure `docs/README.md` explains the source-of-truth hierarchy.
- Ensure `09-ai-build-execution/README.md` clearly states that `09` is derived from `00–08` and must not override them.
- Ensure `traceability/open-questions-register.md` tracks open questions from each document.

---

### Phase 2 — Complete Human Source-of-Truth MVP Docs

Status: In progress.

Current completion:

- `DOC-00` drafted.
- `DOC-01` drafted.
- `DOC-02` drafted/reframed.
- `DOC-03` completed as `0.2.0`.
- `DOC-04` completed/reframed as `0.3.0`.
- `DOC-05` drafted as `0.1.0`.

Next priority:

1. `DOC-06 — User Journey, UX Flow & Service Blueprint`
2. `DOC-07 — Content, Disclosure & User Authorization Spec`
3. `DOC-08 — Notification, Receipt & Communication Spec`
4. `DOC-09 — Payment Request, Multi-Funding Source & Settlement`
5. `DOC-10 — Payout & Reconciliation`
6. `DOC-11 — Refund, Cancellation & Chargeback`
7. `DOC-12 — Bill Category, Document AI/OCR & Payee Verification`
8. `DOC-14 — AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control`
9. `DOC-15 — Privacy, Data Protection & Record Retention`
10. `DOC-16 — Technical Architecture Spec`
11. `DOC-18 — Data Model, Transaction State & Audit Event Spec`
12. `DOC-19 — Security, Tokenization, Authentication & Admin Control`
13. `DOC-20 — Testing, UAT & Go-Live Checklist`

Documents such as `DOC-13`, `DOC-17`, and `DOC-21` remain important but may be sequenced according to MVP needs.

---

### Phase 3 — Build Traceability

Status: Not yet complete.

Actions:

- Add `DOC-05` requirements to `traceability/requirements-traceability-matrix.md`.
- Add `DOC-05` open questions to `traceability/open-questions-register.md`.
- Ensure each `P0` and `T0/T1` requirement maps to:
  - Downstream spec
  - Test case
  - Evidence record
  - Launch gate where applicable

Important `DOC-05` requirement families to trace:

- `REQ-05-GOV-*`
- `REQ-05-USR-*`
- `REQ-05-BILL-*`
- `REQ-05-PAYEE-*`
- `REQ-05-QUOTE-*`
- `REQ-05-PAY-*`
- `REQ-05-MULTI-*`
- `REQ-05-PAYOUT-*`
- `REQ-05-REFUND-*`
- `REQ-05-RISK-*`
- `REQ-05-OPS-*`
- `REQ-05-DATA-*`
- `REQ-05-COMM-*`
- `REQ-05-SEC-*`
- `REQ-05-NFR-*`

---

### Phase 4 — Convert Human Docs into AI Execution Pack

Status: Planned.

Actions:

After `DOC-05`, `DOC-06`, `DOC-07`, `DOC-09`, `DOC-12`, `DOC-14`, `DOC-16`, `DOC-18`, and `DOC-19` have enough substance, populate:

- `09-ai-build-execution/01-structured-prd.md`
- `09-ai-build-execution/02-ui-prototype-prd.md`
- `09-ai-build-execution/03-technical-architecture-prd.md`
- `09-ai-build-execution/04-development-task-list.md`
- `09-ai-build-execution/05-agent-coding-rules.md`
- `09-ai-build-execution/10-agent-context-index.md`

Do not wait for every `00–08` document to be perfect before starting `09`; however, every AI execution item should cite its source document or mark the source as `TBD`.

---

### Phase 5 — AI-Assisted Development Workflow

Status: Future.

Recommended workflow:

1. Choose one task from `09-ai-build-execution/04-development-task-list.md`.
2. Use `09-ai-build-execution/10-agent-context-index.md` to identify required source docs.
3. Provide the AI agent only relevant context.
4. Instruct the AI agent to implement only the selected task.
5. Require tests and documentation updates.
6. Record unresolved issues in `traceability/open-questions-register.md`.
7. Record major decisions in `decision-log/`.
8. Update `requirements-traceability-matrix.md`.

Avoid broad prompts such as:

```text
Build the whole PayPlus app.
```

Prefer narrow prompts such as:

```text
Implement TASK-012: Create Payment Request Draft API.

Read:
- docs/01-product/doc-05-master-prd-feature-requirement-index.md
- docs/02-payment-domain/doc-09-payment-request-multi-funding-source-settlement.md
- docs/06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md
- docs/09-ai-build-execution/05-agent-coding-rules.md

Implement only TASK-012.
Do not implement settlement, refunds, promotions, or reconciliation.
All payment-mutating endpoints must support idempotency.
All state transitions must write audit events.
```

---

### Phase 6 — Launch Readiness

Status: Future.

Before go-live, ensure:

- `DOC-03` assessment is complete for actual launch scope.
- `DOC-04` T0/T1 controls are satisfied.
- `DOC-05` P0/T0/T1 requirements are mapped to tests and evidence.
- `DOC-20` go-live checklist is complete.
- PSP/acquirer support is documented.
- Payout provider support is documented.
- Approved bill categories are locked.
- Prohibited and restricted categories are enforced.
- Disclosures are implemented and tested.
- Consent and authorization logs are retained.
- Fraud/velocity/anti-cashout controls are live.
- Payee verification process is operational.
- Reconciliation is tested daily.
- Refund/cancellation/chargeback procedures are operational.
- Monitoring and incident response are ready.
- Security/access controls are tested.
- Open blockers are resolved or formally deferred.
- Launch approval is signed.

---

## Cross-Document Themes to Preserve

### Launch Is Scope-Specific

Approval for one jurisdiction, category, partner, payment method, payout method, funds flow, or user segment does not approve others.

### Human Docs Are Source of Truth

Documents in `00–08` are authoritative. The `09` layer is derived from them and should not override them.

### AI Docs Are Execution Aids

The `09-ai-build-execution` folder exists to help AI agents and developers build safely, incrementally, and consistently.

### Compliance Controls Are Product Requirements

Disclosures, consent capture, category blocking, verification, risk routing, evidence retention, and audit logs are product requirements, not afterthoughts.

### PSP/Acquirer Approval Matters

Product assumptions must be subordinate to PSP/acquirer, payout provider, card network, and legal constraints.

### Funds Flow Drives Everything

Regulatory role, licensing, settlement, reconciliation, refund, chargeback, risk, and accounting treatment depend on funds flow.

### Multi-Source Funding Is High Complexity

Multi-card or multi-source funding must be deferred, restricted, or separately certified unless explicitly approved as MVP scope.

### Payee Verification Is Central

Payee verification and self-payment/collusion controls are core to anti-cashout and fraud prevention.

### Fee Disclosure Is Launch-Critical

Service fee, bill amount, total charge, payment timing, PayPlus role, refund/cancellation rules, and user responsibility must be clear before authorization.

### Reconciliation Is Not Optional

Daily reconciliation across user charge, fees, PSP settlement, payout, refunds, chargebacks, reserves, and ledger is a launch blocker.

### Admin Tooling Is MVP-Critical

Manual review, risk review, payout exceptions, refunds, disputes, support, and reconciliation cannot be treated as afterthoughts.

### Evidence Matters

Every critical control should produce durable evidence in a known system of record.

### Change Management Is Mandatory

New category, jurisdiction, funds flow, fee model, payment method, payout method, provider, or material product change triggers reassessment.

### AI Agents Need Guardrails

AI-assisted coding must be constrained by source documents, agent coding rules, feature build sequence, Definition of Done, test expectations, and task boundaries.

---

## Known Open Strategic Questions

These remain unresolved and should continue appearing as open questions where relevant:

- What jurisdiction will PayPlus launch in first?
- What exact MVP bill categories are in scope?
- Is rent included in MVP?
- Are school fees, utilities, government fees, insurance, medical bills, loan payments, or credit card repayments included or excluded?
- What exact MVP funds flow will be used?
- What is PayPlus’s legal/regulatory role?
- Is PayPlus merchant of record, agent, PayFac, marketplace, money transmitter, technical provider, or another role?
- What licensing, exemption, or partner coverage applies?
- Which PSP/acquirer will support MVP?
- What MCC or transaction classification applies?
- Will transactions be treated as purchase, quasi-cash, account funding, money transfer, cash advance, or another classification?
- What payout provider and payout rail will be used?
- Does payout occur before settlement or before funding certainty?
- What settlement timing, reserves, holdbacks, or prefunding apply?
- What transaction, user, card, payee, and velocity limits apply?
- What payee verification is required?
- What sanctions screening is required?
- What fraud and anti-cashout rules are required at launch?
- Is multi-card or multi-source funding included in MVP or deferred?
- Is OCR required for MVP, or is manual upload/review sufficient?
- What admin review workflows are required before payment processing?
- What PCI scope applies?
- What disclosures must be shown before authorization?
- What consent and authorization records must be retained?
- What records must be retained, and for how long?
- What systems of record will store consent, authorization, risk decisions, payouts, refunds, disputes, and reconciliation evidence?
- What technical stack will be used?
- What authentication provider will be used?
- What logging, monitoring, and alerting stack will be used?
- Who has final authority to approve MVP launch?

---

## Current State Summary

The PayPlus documentation repo has now been restructured into a mature dual-purpose documentation system:

```text
Professional source docs + AI build-execution layer
```

Completed structural changes:

- Added `09-ai-build-execution/`.
- Moved AI context files into `09-ai-build-execution/context/`.
- Preserved `00–08` as human-readable source-of-truth documentation.
- Preserved `99-isms-policies/` for ISMS/security policy maturity.
- Preserved traceability, change request, changelog, decision log, diagram, glossary, and template support folders.
- Corrected prior naming issues.

Completed or drafted document status:

| Document | Status |
| --- | --- |
| `DOC-00` | Drafted / previously created |
| `DOC-01` | Drafted / previously created |
| `DOC-02` | Drafted / reframed |
| `DOC-03` | Completed as `0.2.0` |
| `DOC-04` | Completed/reframed as `0.3.0` |
| `DOC-05` | Drafted as `0.1.0` |

Immediate next step:

```text
Draft DOC-06 — User Journey, UX Flow & Service Blueprint
```

Recommended next prompt:

```text
Draft docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md for PayPlus.

Use the current project-continuation-context.md and DOC-05 as primary upstream context.
Make it consistent with DOC-03, DOC-04, and DOC-05.
Treat DOC-06 as the human source-of-truth user journey, UX flow, and service blueprint document.
Include YAML front matter, purpose, scope, out of scope, source-of-truth relationship, journey principles, personas, end-to-end journeys, screen/flow inventory, service blueprints, user states, internal operations states, risk/compliance intervention points, failure and exception journeys, notification touchpoints, data/evidence touchpoints, assumptions, constraints, dependencies, risks, downstream document impact, open questions, acceptance criteria, and version history.
Wrap the full document in a single Markdown code block.
```

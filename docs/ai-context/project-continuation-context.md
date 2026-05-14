markdown
# PayPlus Documentation Repo — Project Continuation Context

## 1. Purpose of This File

This file preserves the working context for the PayPlus documentation repository.

Use this file when starting a new AI conversation so the assistant can continue the documentation work without relying on previous chat history.

This file is intended to prevent context loss around:

- repository structure
- documentation strategy
- source-of-truth hierarchy
- document numbering
- template requirements
- build sequence
- PayPlus-specific product principles
- current next steps

This file is not the product specification itself.

Approved `DOC-XX` documents, approved ADRs, approved rulebooks, and approved policy documents remain the source of truth.

---

## 2. Project Summary

We are building the documentation repository for **PayPlus**.

PayPlus is a payment-related product involving:

- payment requests
- multi-funding-source payment logic
- payout and reconciliation
- refund, cancellation, and chargeback
- bill category verification
- bill document verification
- document AI / OCR
- payee verification
- promotion engine
- anti-cashout controls
- fraud and risk controls
- AML-related controls
- privacy and data protection
- API and third-party integration
- security and access control
- QA, release, monitoring, and incident response
- ISMS policy documentation

The goal is to create a professional docs-as-code repository that can serve as:

- product source of truth
- engineering specification base
- compliance and risk documentation base
- QA and release reference
- AI coding-agent context
- decision and traceability system

---

## 3. Current Repository Structure

The current repository structure is approximately:

```text
payplus-docs/
├── README.md
└── docs/
    ├── 00-foundation/
    ├── 01-product/
    ├── 02-payment-domain/
    ├── 03-bill-verification/
    ├── 04-growth-ecosystem/
    ├── 05-risk-compliance-privacy/
    ├── 06-engineering/
    ├── 07-security-access-control/
    ├── 08-qa-release-operations/
    ├── 99-isms-policies/
    ├── ai-context/
    ├── changelog/
    ├── decision-log/
    ├── glossary/
    ├── templates/
    └── traceability/

Important note:

ai-context/, templates/, decision-log/, glossary/, traceability/, and changelog/ are currently under docs/.
Although they might be cleaner at the repository root, do not move them for now.
The current location is acceptable if README files clearly state that these are repository-level supporting documentation assets.
4. Non-Negotiable Decisions
The following decisions have already been made for the current phase:

Do not reorganize the directory structure at this stage.
Keep the current folder structure under docs/.
Add or improve README files before writing detailed product specs.
Add documentation governance before scaling document creation.
Upgrade templates before generating large numbers of detailed documents.
Lock document numbering to prevent document ID drift.
Build foundation docs before detailed product, payment, engineering, or ISMS docs.
Treat AI context as guidance only, not as source of truth.
Do not overbuild all ISMS policies before core PayPlus product and payment documentation stabilizes.
5. Source-of-Truth Hierarchy
Use the following source-of-truth order:

Approved core DOC-XX specifications
Approved ADRs
Approved rulebooks
API, data model, and test specifications
ISMS policies, where relevant
AI context summaries
AI context files are compressed guidance for AI coding agents.

AI context files are not the source of truth.

If there is any conflict, the approved DOC-XX specification, approved ADR, approved rulebook, or approved policy takes precedence over AI context.

6. Core Documentation Domains
The main documentation domains are:

text
00-foundation/
01-product/
02-payment-domain/
03-bill-verification/
04-growth-ecosystem/
05-risk-compliance-privacy/
06-engineering/
07-security-access-control/
08-qa-release-operations/
99-isms-policies/

Domain purposes:

Folder	Purpose
00-foundation/	Documentation governance, project charter, regulatory roadmap, compliance roadmap
01-product/	Product requirements, user journeys, UX flows, communication and notification rules
02-payment-domain/	Payment request, funding source, settlement, payout, reconciliation, refund, cancellation, chargeback
03-bill-verification/	Bill categories, document AI/OCR, bill validation, payee verification
04-growth-ecosystem/	Promotion engine, campaign rules, referral or growth mechanics if needed
05-risk-compliance-privacy/	AML, anti-cashout, fraud controls, privacy, retention, compliance
06-engineering/	Architecture, API, integrations, data model, ledger, reporting
07-security-access-control/	Security architecture, tokenization, access control, admin permissions
08-qa-release-operations/	Testing, UAT, release, go-live checklist, monitoring, incident response, runbooks
99-isms-policies/	Information security management system policies and procedures
7. Core DOC Numbering
Use this numbering unless the user explicitly changes it:

text
DOC-00 Documentation Governance
DOC-01 Project Charter & Product Positioning
DOC-02 Business Model, Unit Economics & Commercial Model
DOC-03 Regulatory, PSP & Acquirer Assessment
DOC-04 Compliance Certification Roadmap

DOC-05 Master PRD & Feature Requirements
DOC-06 User Journey, UX Flow & Service Blueprint
DOC-07 Content, Disclosure & User Communication
DOC-08 Notification, Receipt & Communication Rules

DOC-09 Payment Request, Multi-Funding Source & Settlement
DOC-10 Payout & Reconciliation
DOC-11 Refund, Cancellation & Chargeback

DOC-12 Bill Category, Document AI/OCR & Payee Verification

DOC-13 Promotion Engine & Campaign Rules

DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
DOC-15 Privacy, Data Protection & Retention

DOC-16 Technical Architecture
DOC-17 API & Third-party Integration
DOC-18 Data Model, Transaction Ledger & Reporting

DOC-19 Security, Tokenization & Access Control

DOC-20 Testing, UAT, Release & Go-Live Checklist
DOC-21 Monitoring, Incident Response & Operations Runbook

Recommended paths:

text
docs/00-foundation/doc-00-documentation-governance.md
docs/00-foundation/doc-01-project-charter-product-positioning.md
docs/00-foundation/doc-02-business-model-unit-economics-commercial-model.md
docs/00-foundation/doc-03-regulatory-psp-acquirer-assessment.md
docs/00-foundation/doc-04-compliance-certification-roadmap.md

docs/01-product/doc-05-master-prd-feature-requirements.md
docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md
docs/01-product/doc-07-content-disclosure-user-communication.md
docs/01-product/doc-08-notification-receipt-communication-rules.md

docs/02-payment-domain/doc-09-payment-request-multi-funding-source-settlement.md
docs/02-payment-domain/doc-10-payout-reconciliation.md
docs/02-payment-domain/doc-11-refund-cancellation-chargeback.md

docs/03-bill-verification/doc-12-bill-category-document-ai-ocr-payee-verification.md

docs/04-growth-ecosystem/doc-13-promotion-engine-campaign-rules.md

docs/05-risk-compliance-privacy/doc-14-aml-anti-cashout-fraud-risk-controls.md
docs/05-risk-compliance-privacy/doc-15-privacy-data-protection-retention.md

docs/06-engineering/doc-16-technical-architecture.md
docs/06-engineering/doc-17-api-third-party-integration.md
docs/06-engineering/doc-18-data-model-transaction-ledger-reporting.md

docs/07-security-access-control/doc-19-security-tokenization-access-control.md

docs/08-qa-release-operations/doc-20-testing-uat-release-go-live-checklist.md
docs/08-qa-release-operations/doc-21-monitoring-incident-response-operations-runbook.md

8. Supporting Folders
Supporting folders are currently under docs/:

text
docs/ai-context/
docs/changelog/
docs/decision-log/
docs/glossary/
docs/templates/
docs/traceability/

Do not move these folders at this stage.

Their purpose:

Folder	Purpose
docs/ai-context/	Compressed AI coding-agent context and continuation context
docs/changelog/	Documentation and decision change history
docs/decision-log/	ADRs and major decisions
docs/glossary/	Shared terminology
docs/templates/	Document templates
docs/traceability/	Requirement, test, question, and decision traceability
Recommended files:

text
docs/ai-context/README.md
docs/ai-context/project-continuation-context.md

docs/changelog/README.md
docs/changelog/documentation-changelog.md

docs/decision-log/README.md

docs/glossary/README.md
docs/glossary/glossary.md

docs/templates/README.md
docs/templates/core-spec-template.md
docs/templates/adr-template.md
docs/templates/api-spec-template.md
docs/templates/rulebook-template.md
docs/templates/test-case-template.md
docs/templates/change-request-template.md
docs/templates/policy-template.md

docs/traceability/README.md
docs/traceability/open-questions-register.md
docs/traceability/requirements-traceability-matrix.md

If an ADR template exists without .md, rename it to:

text
adr-template.md

9. ISMS Policy Scope
The repo includes an ISMS policy folder:

text
docs/99-isms-policies/

It should eventually contain around 20 ISMS-related documents, including:

information security policy
acceptable use policy
access control policy
cryptography policy
data classification and handling policy
asset management policy
supplier / vendor security policy
HR security policy
physical / environmental security policy
change management policy
vulnerability management policy
secure development policy
incident management policy
business continuity / disaster recovery policy
logging and monitoring policy
backup and restore policy
risk assessment methodology
statement of applicability
internal audit program
management review procedure
Add or maintain one of the following:

text
docs/99-isms-policies/README.md

or:

text
docs/99-isms-policies/99-00-isms-index.md

The ISMS index should track:

policy ID
policy name
owner
status
version
last reviewed date
next review date
review frequency
ISO / SOC / PCI mapping if applicable
related PayPlus docs, if applicable
Do not fully build all ISMS policies before the core product, payment, risk, security, and engineering docs are stable.

10. Template Quality Requirements
Templates must be professional and implementation-ready.

They should not be lightweight placeholders.

10.1 Core Spec Template Requirements
The core spec template should include:

YAML front matter
document control
AI summary
purpose
source-of-truth statement
scope
out of scope
assumptions
key definitions
roles and actors
business context
business rules
functional requirements
non-functional requirements
user flows or process flows
state model, where applicable
data requirements
API / integration requirements
security requirements
privacy requirements
compliance requirements
audit logging requirements
evidence requirements
error handling
edge cases
dependencies
risks and mitigations
open questions
ADR links
traceability
acceptance criteria
test mapping
approval
changelog
10.2 ADR Template Requirements
The ADR template should include:

status
context
decision drivers
options considered
decision
rationale
consequences
impact assessment
risks and mitigations
reversibility
affected documents
follow-up actions
approval
changelog
10.3 API Spec Template Requirements
The API spec template should include:

endpoint summary
ownership
authentication
authorization
idempotency
headers
path parameters
query parameters
request schema
response schema
error responses
webhook behavior, where applicable
retry behavior, where applicable
duplicate handling, where applicable
audit events
rate limits
observability
security notes
privacy notes
compliance notes
test mapping
10.4 Rulebook Template Requirements
The rulebook template should include:

rule ID
rule name
rule purpose
rule evaluation context
trigger
conditions
action / decision
priority
conflict resolution
effective date
expiry date
owner
audit logging
monitoring metrics
test cases
lifecycle
change control
10.5 Test Case Template Requirements
The test case template should include:

test case ID
related requirement IDs
related rule IDs
related ADRs
preconditions
test data
steps
expected result
actual result
evidence
automation notes
negative tests
edge case tests
regression checklist
defects
sign-off
10.6 Required Templates
The templates folder should contain:

text
docs/templates/core-spec-template.md
docs/templates/adr-template.md
docs/templates/api-spec-template.md
docs/templates/rulebook-template.md
docs/templates/test-case-template.md
docs/templates/change-request-template.md
docs/templates/policy-template.md

11. Recommended Build Sequence
Follow this order.

Batch 1 — Repo Governance
Create or update:

text
README.md
docs/README.md
docs/00-foundation/doc-00-documentation-governance.md

Batch 2 — Templates
Create or update:

text
docs/templates/README.md
docs/templates/core-spec-template.md
docs/templates/adr-template.md
docs/templates/api-spec-template.md
docs/templates/rulebook-template.md
docs/templates/test-case-template.md
docs/templates/change-request-template.md
docs/templates/policy-template.md

Batch 3 — Registers and Supporting Indexes
Create or update:

text
docs/ai-context/README.md
docs/changelog/README.md
docs/changelog/documentation-changelog.md
docs/decision-log/README.md
docs/glossary/README.md
docs/glossary/glossary.md
docs/traceability/README.md
docs/traceability/open-questions-register.md
docs/traceability/requirements-traceability-matrix.md
docs/99-isms-policies/README.md

Batch 4 — Foundation Docs
Create or update:

text
docs/00-foundation/doc-01-project-charter-product-positioning.md
docs/00-foundation/doc-02-business-model-unit-economics-commercial-model.md
docs/00-foundation/doc-03-regulatory-psp-acquirer-assessment.md
docs/00-foundation/doc-04-compliance-certification-roadmap.md

Batch 5 — Product Docs
Create or update:

text
docs/01-product/doc-05-master-prd-feature-requirements.md
docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md
docs/01-product/doc-07-content-disclosure-user-communication.md
docs/01-product/doc-08-notification-receipt-communication-rules.md

Batch 6 — Payment Domain Docs
Create or update:

text
docs/02-payment-domain/doc-09-payment-request-multi-funding-source-settlement.md
docs/02-payment-domain/doc-10-payout-reconciliation.md
docs/02-payment-domain/doc-11-refund-cancellation-chargeback.md

Batch 7 — Bill Verification and Growth
Create or update:

text
docs/03-bill-verification/doc-12-bill-category-document-ai-ocr-payee-verification.md
docs/04-growth-ecosystem/doc-13-promotion-engine-campaign-rules.md

Batch 8 — Risk, Compliance, and Privacy
Create or update:

text
docs/05-risk-compliance-privacy/doc-14-aml-anti-cashout-fraud-risk-controls.md
docs/05-risk-compliance-privacy/doc-15-privacy-data-protection-retention.md

Batch 9 — Engineering
Create or update:

text
docs/06-engineering/doc-16-technical-architecture.md
docs/06-engineering/doc-17-api-third-party-integration.md
docs/06-engineering/doc-18-data-model-transaction-ledger-reporting.md

Batch 10 — Security and Operations
Create or update:

text
docs/07-security-access-control/doc-19-security-tokenization-access-control.md
docs/08-qa-release-operations/doc-20-testing-uat-release-go-live-checklist.md
docs/08-qa-release-operations/doc-21-monitoring-incident-response-operations-runbook.md

Batch 11 — ISMS Skeletons
Create or update ISMS policy skeletons under:

text
docs/99-isms-policies/

Do this after the core PayPlus product, payment, engineering, risk, and security docs are stable enough.

After each batch, update this continuation file.

12. Documentation Maturity Levels
Use these maturity levels when creating or reviewing documents.

Level 0 — Skeleton
Contains:

purpose
scope
out of scope
definitions
open questions
owner
status
Level 1 — Concept Spec
Adds:

business rules
high-level flows
MVP / Post-MVP split
key dependencies
major risks
initial requirements
unresolved assumptions
Level 2 — Build-Ready Spec
Adds:

detailed requirements
state model
edge cases
API implications
data requirements
security requirements
privacy requirements
acceptance criteria
test mapping
audit logging expectations
Level 3 — Operational / Audit-Ready Spec
Adds:

runbook
evidence requirements
monitoring
alerting
SLA / SLO where applicable
control mapping
review cycle
approval records
operational ownership
For initial repo setup, most documents can start at Level 0 or Level 1.

For payment, risk, promotion, API, security, and operations docs, the target should eventually be Level 2 or Level 3.

13. PayPlus Product Principles
For PayPlus documentation, follow these principles:

Do not treat brainstorming notes as approved source of truth.
Every important requirement should have a requirement ID.
Every important business rule should have a rule ID.
Every important requirement should eventually map to test cases.
Payment flows must have state models.
Payment write APIs should use idempotency.
Webhooks must define signature verification, retry behavior, timeout behavior, and duplicate handling.
Promotion engine must define reservation, consumption, reversal, refund, expiry, stacking, and abuse prevention behavior.
Refund and chargeback behavior must align with payment, promotion, payout, reconciliation, and ledger.
Payout and reconciliation must define settlement timing, matching logic, exception handling, and evidence.
Bill verification must define supported bill categories, document requirements, validation logic, and rejection reasons.
Payee verification must define matching logic, mismatch handling, and escalation path.
Risk controls must define anti-cashout behavior, fraud signals, AML-related review triggers, and manual review flows.
Privacy docs must define data categories, retention, deletion, access, masking, and disclosure controls.
Security docs must define authentication, authorization, tokenization, secrets handling, and admin access controls.
Audit logging is required for payment, admin, security, promotion, risk, and compliance-relevant events.
AI context files must be updated only after the source specification is updated.
Do not overbuild all ISMS policies at the start; create index and skeletons first.

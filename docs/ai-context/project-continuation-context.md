# Project Continuation Context

## 1. Purpose

This file is the continuation anchor for the PayPlus documentation project.

Use this file to restore project context across AI sessions and prevent drift.

This file records:

- The current repository structure.
- The current documentation progress.
- The purpose of each planned documentation file.
- The known drafted documents.
- The next recommended documentation step.
- The AI working rules for future sessions.

This file should be updated whenever:

- A document changes status.
- A new documentation decision is made.
- The repo structure changes.
- The drafting sequence changes.
- A major assumption is resolved.

---

## 2. Source of Truth

The current documentation governance source of truth is:

```text
docs/00-foundation/doc-00-documentation-governance.md
```

Known drafted foundation documents:

```text
docs/00-foundation/doc-00-documentation-governance.md
docs/00-foundation/doc-01-project-charter-product-positioning.md
docs/00-foundation/doc-02-business-model-unit-economics.md
```

The repo structure source is:

```text
payplus_repo_structure.txt
```

If a future AI session does not receive the actual content of a drafted document, it must not invent exact wording, rules, IDs, traceability references, decisions, or acceptance criteria from that document.

---

## 3. Project Summary

PayPlus is a **Payment & Bill Settlement Platform**.

PayPlus helps users pay approved bills through supported funding methods while preserving a bill-backed payment model.

PayPlus coordinates:

- Bill capture and verification.
- Payee validation.
- Payment request creation.
- Multi-funding-source payment logic.
- PSP/acquirer routing.
- Settlement.
- Payee payout.
- Reconciliation.
- Refunds.
- Cancellations.
- Chargebacks.
- Promotions.
- Fraud and AML controls.
- Anti-cashout controls.
- Privacy and data protection.
- Security and access control.
- Monitoring.
- Incident response.
- Operational SOPs.
- Compliance evidence.

PayPlus must remain bill-backed.

PayPlus is not:

- A general wallet.
- A stored value product.
- A cashout product.
- A general remittance product.
- A bank.
- A lending product.
- A crypto product.
- An unrestricted peer-to-peer transfer product.

The documentation must preserve this positioning unless a formal change request updates the project scope.

---

## 4. Repo Structure

```text
docs/
├── 00-foundation
│   ├── doc-00-documentation-governance.md
│   ├── doc-01-project-charter-product-positioning.md
│   ├── doc-02-business-model-unit-economics.md
│   ├── doc-03-regulatory-psp-acquirer-assessment.md
│   └── doc-04-compliance-certification-roadmap-control-framework.md
├── 01-product
│   ├── doc-05-master-prd-feature-requirement-index.md
│   ├── doc-06-user-journey-ux-flow-service-blueprint.md
│   ├── doc-07-content-disclosure-user-authorization-spec.md
│   └── doc-08-notification-receipt-communication-spec.md
├── 02-payment-domain
│   ├── doc-09-payment-request-multi-funding-source-settlement.md
│   ├── doc-10-payout-reconciliation.md
│   └── doc-11-refund-cancellation-chargeback.md
├── 03-bill-verification
│   └── doc-12-bill-category-document-ai-ocr-payee-verification-spec.md
├── 04-growth-ecosystem
│   └── doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md
├── 05-risk-compliance-privacy
│   ├── doc-14-aml-anti-cashout-fraud-dynamic-auth-risk-control-spec.md
│   └── doc-15-privacy-data-protection-record-retention-spec.md
├── 06-engineering
│   ├── api
│   │   └── openapi.yaml
│   ├── doc-16-technical-architecture-spec.md
│   ├── doc-17-api-third-party-integration-spec.md
│   └── doc-18-data-model-transaction-state-audit-event-spec.md
├── 07-security-access-control 
│   └── doc-19-security-tokenization-authentication-admin-control-spec.md
├── 08-qa-release-operations
│   ├── doc-20-testing-uat-golive-checklist.md
│   └── doc-21-monitoring-incident-response-operational-sops.md
├── 99-isms-policies
│   ├── 99-01-information-security-policy.md
│   ├── 99-02-acceptable-use-policy.md
│   ├── 99-03-access-control-policy.md
│   ├── 99-04-cryptography-policy.md
│   ├── 99-05-data-classification-handling-policy.md
│   ├── 99-06-asset-management-policy.md
│   ├── 99-07-supplier-vendor-security-policy.md
│   ├── 99-08-hr-security-policy.md
│   ├── 99-09-physical-environmental-security-policy.md
│   ├── 99-10-change-management-policy.md
│   ├── 99-11-vulnerability-management-policy.md
│   ├── 99-12-secure-development-policy.md
│   ├── 99-13-incident-management-policy.md
│   ├── 99-14-business-continuity-disaster-recovery-policy.md
│   ├── 99-15-logging-monitoring-policy.md
│   ├── 99-16-backup-restore-policy.md
│   ├── 99-17-risk-assessment-methodology.md
│   ├── 99-18-statement-of-applicability.md
│   ├── 99-19-internal-audit-programme.md
│   ├── 99-20-management-review-procedure.md
│   └── README.md
├── ai-context
│   ├── bill-verification-context.md
│   ├── payment-core-context.md
│   ├── project-continuation-context.md
│   ├── promotion-engine-context.md
│   ├── README.md
│   ├── refund-chargeback-context.md
│   └── security-context.md
├── change-requests
│   └── README.md
├── changelog
│   └── changelog.md
├── desicion-log
│   └── README.md
├── glossary
│   └── glossary.md
├── templates
│   ├── adr-template
│   ├── api-spec-template.md
│   ├── change-request-template.md
│   ├── core-spec-template.md
│   ├── rulebook-template.md
│   └── test-case-template.md
├── traceability
│   ├── open-questions-register.md
│   └── requirements-traceability-matrix.md
├── diagrams
└── README.md
```

---

## 5. Important Repo Path Notes

### 5.1 `desicion-log`

The repo currently contains:

```text
docs/desicion-log/
```

This appears to be misspelled.

Do not rename it unless a formal change request or explicit user instruction approves the correction.

### 5.2 `07-security-access-control`

The repo structure shows:

```text
docs/07-security-access-control /
```

There may be a trailing space after `control`.

Confirm the actual filesystem path before scripting, linking, or generating path-sensitive references.

---

## 6. Documentation Status Summary

### 6.1 Drafted Documents

| File | Status | Purpose |
|---|---|---|
| `docs/00-foundation/doc-00-documentation-governance.md` | Drafted | Defines documentation governance, source-of-truth rules, ownership, versioning, status model, change control, traceability, review flow, and AI usage rules. |
| `docs/00-foundation/doc-01-project-charter-product-positioning.md` | Drafted | Defines the PayPlus product charter, product scope, market positioning, value proposition, target users, non-goals, and strategic boundaries. |
| `docs/00-foundation/doc-02-business-model-unit-economics.md` | Drafted | Defines the PayPlus business model, revenue model, cost model, commercial assumptions, unit economics, profitability drivers, and business constraints. |

### 6.2 Planned Documents

| File | Status | Purpose |
|---|---|---|
| `docs/00-foundation/doc-03-regulatory-psp-acquirer-assessment.md` | Planned | Assess regulatory considerations, PSP options, acquirer dependencies, licensing assumptions, payment method feasibility, settlement constraints, and operating model implications. |
| `docs/00-foundation/doc-04-compliance-certification-roadmap-control-framework.md` | Planned | Define the compliance roadmap, certification plan, control framework, evidence requirements, policy dependencies, and compliance-readiness milestones. |
| `docs/01-product/doc-05-master-prd-feature-requirement-index.md` | Planned | Define the master product requirements document, feature index, requirement hierarchy, product modules, MVP scope, and traceability baseline. |
| `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md` | Planned | Define user journeys, service blueprints, UX flows, operational touchpoints, exception handling flows, and frontstage/backstage responsibilities. |
| `docs/01-product/doc-07-content-disclosure-user-authorization-spec.md` | Planned | Define user-facing content, consent language, disclosures, authorizations, confirmation screens, permission capture, and user acknowledgement requirements. |
| `docs/01-product/doc-08-notification-receipt-communication-spec.md` | Planned | Define notification events, receipt content, communication channels, timing, message templates, delivery rules, and audit requirements. |
| `docs/02-payment-domain/doc-09-payment-request-multi-funding-source-settlement.md` | Planned | Define payment request lifecycle, funding-source selection, split/multi-source payment logic, authorization, capture, settlement, and payment state rules. |
| `docs/02-payment-domain/doc-10-payout-reconciliation.md` | Planned | Define payee payout process, reconciliation model, matching rules, settlement reporting, exception queues, manual review, and operational controls. |
| `docs/02-payment-domain/doc-11-refund-cancellation-chargeback.md` | Planned | Define refund, cancellation, failed payment, dispute, chargeback, reversal, and adjustment handling across payment and payout states. |
| `docs/03-bill-verification/doc-12-bill-category-document-ai-ocr-payee-verification-spec.md` | Planned | Define bill categories, accepted document types, document validation rules, OCR/AI extraction, payee verification, confidence scoring, and manual review rules. |
| `docs/04-growth-ecosystem/doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md` | Planned | Define promotion engine rules, coupons, vouchers, referral logic, membership benefits, eligibility checks, abuse controls, and accounting treatment. |
| `docs/05-risk-compliance-privacy/doc-14-aml-anti-cashout-fraud-dynamic-auth-risk-control-spec.md` | Planned | Define AML controls, anti-cashout safeguards, fraud detection, transaction monitoring, risk scoring, velocity controls, dynamic authentication, and escalation handling. |
| `docs/05-risk-compliance-privacy/doc-15-privacy-data-protection-record-retention-spec.md` | Planned | Define privacy principles, personal data handling, retention periods, deletion rules, consent records, data subject rights, data minimization, and cross-system data controls. |
| `docs/06-engineering/doc-16-technical-architecture-spec.md` | Planned | Define system architecture, service boundaries, deployment model, infrastructure assumptions, integration points, reliability goals, scalability model, and technology constraints. |
| `docs/06-engineering/doc-17-api-third-party-integration-spec.md` | Planned | Define internal APIs, external APIs, PSP integrations, acquirer integrations, biller/payee integrations, webhook handling, idempotency, retries, and integration security requirements. |
| `docs/06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md` | Planned | Define data model, transaction state machines, audit event taxonomy, ledger-like records, entity relationships, event sourcing assumptions, and reporting data structures. |
| `docs/06-engineering/api/openapi.yaml` | Planned | Provide OpenAPI specification for PayPlus APIs, including endpoints, schemas, authentication, error responses, idempotency behavior, and webhook definitions. |
| `docs/07-security-access-control /doc-19-security-tokenization-authentication-admin-control-spec.md` | Planned | Define security controls, tokenization, authentication, authorization, admin access, privileged actions, session control, secrets handling, and security monitoring dependencies. |
| `docs/08-qa-release-operations/doc-20-testing-uat-golive-checklist.md` | Planned | Define test strategy, UAT plan, release readiness checklist, go-live criteria, rollback criteria, test evidence, defect triage, and launch approval requirements. |
| `docs/08-qa-release-operations/doc-21-monitoring-incident-response-operational-sops.md` | Planned | Define monitoring, alerting, incident response, operational SOPs, escalation paths, service levels, reconciliation operations, daily checks, and post-incident review process. |
| `docs/99-isms-policies/99-01-information-security-policy.md` | Planned | Define the high-level information security policy, security objectives, governance model, responsibilities, and management commitment. |
| `docs/99-isms-policies/99-02-acceptable-use-policy.md` | Planned | Define acceptable use rules for company systems, devices, accounts, networks, data, and third-party services. |
| `docs/99-isms-policies/99-03-access-control-policy.md` | Planned | Define access control principles, identity lifecycle, role-based access, least privilege, privileged access, reviews, and revocation. |
| `docs/99-isms-policies/99-04-cryptography-policy.md` | Planned | Define encryption, key management, cryptographic standards, certificate handling, hashing, tokenization dependencies, and prohibited cryptographic practices. |
| `docs/99-isms-policies/99-05-data-classification-handling-policy.md` | Planned | Define data classification levels, handling requirements, storage rules, transmission rules, labeling, sharing, and disposal requirements. |
| `docs/99-isms-policies/99-06-asset-management-policy.md` | Planned | Define asset inventory, ownership, acceptable asset use, asset lifecycle, return of assets, and protection requirements. |
| `docs/99-isms-policies/99-07-supplier-vendor-security-policy.md` | Planned | Define vendor risk assessment, supplier onboarding, due diligence, contractual controls, ongoing monitoring, and offboarding. |
| `docs/99-isms-policies/99-08-hr-security-policy.md` | Planned | Define HR security controls before employment, during employment, and after termination, including screening, training, confidentiality, and access changes. |
| `docs/99-isms-policies/99-09-physical-environmental-security-policy.md` | Planned | Define physical access, office security, visitor controls, environmental safeguards, equipment protection, and secure areas. |
| `docs/99-isms-policies/99-10-change-management-policy.md` | Planned | Define change request, review, approval, testing, deployment, rollback, emergency change, and change evidence requirements. |
| `docs/99-isms-policies/99-11-vulnerability-management-policy.md` | Planned | Define vulnerability scanning, triage, remediation timelines, penetration testing, dependency monitoring, and exception handling. |
| `docs/99-isms-policies/99-12-secure-development-policy.md` | Planned | Define secure SDLC, code review, security testing, threat modeling, dependency management, secrets control, and release security gates. |
| `docs/99-isms-policies/99-13-incident-management-policy.md` | Planned | Define security incident identification, classification, reporting, containment, investigation, escalation, communication, and post-incident review. |
| `docs/99-isms-policies/99-14-business-continuity-disaster-recovery-policy.md` | Planned | Define business continuity, disaster recovery, recovery objectives, backup dependencies, crisis roles, scenario testing, and recovery validation. |
| `docs/99-isms-policies/99-15-logging-monitoring-policy.md` | Planned | Define logging requirements, event monitoring, alerting, retention, log protection, review processes, and detection responsibilities. |
| `docs/99-isms-policies/99-16-backup-restore-policy.md` | Planned | Define backup scope, frequency, retention, encryption, restoration testing, backup access, and failure handling. |
| `docs/99-isms-policies/99-17-risk-assessment-methodology.md` | Planned | Define risk assessment methodology, likelihood and impact scoring, risk treatment options, ownership, review cadence, and residual risk acceptance. |
| `docs/99-isms-policies/99-18-statement-of-applicability.md` | Planned | Define the ISO-style statement of applicability, control applicability, inclusion or exclusion rationale, implementation status, and evidence references. |
| `docs/99-isms-policies/99-19-internal-audit-programme.md` | Planned | Define internal audit scope, audit schedule, audit criteria, auditor independence, reporting, findings, corrective actions, and follow-up. |
| `docs/99-isms-policies/99-20-management-review-procedure.md` | Planned | Define management review inputs, outputs, cadence, participants, decisions, actions, and continual improvement process. |

---

## 7. Known Progress Summary

Current known progress:

```text
Drafted:
- doc-00-documentation-governance.md
- doc-01-project-charter-product-positioning.md
- doc-02-business-model-unit-economics.md

Planned:
- doc-03 through doc-21
- openapi.yaml
- all docs/99-isms-policies documents
- supporting README/context/traceability/changelog files unless separately updated
```

Current completion state:

| Area | Status |
|---|---|
| Documentation governance | Drafted |
| Product charter and positioning | Drafted |
| Business model and unit economics | Drafted |
| Regulatory / PSP / acquirer assessment | Planned |
| Compliance roadmap and control framework | Planned |
| Product requirements | Planned |
| Payment domain specifications | Planned |
| Bill verification specification | Planned |
| Promotion engine specification | Planned |
| Risk, compliance, and privacy specifications | Planned |
| Engineering specifications | Planned |
| Security and access control specification | Planned |
| QA, release, and operations specifications | Planned |
| ISMS policies | Planned |

---

## 8. Recommended Next Step

The next recommended document to draft is:

```text
docs/00-foundation/doc-03-regulatory-psp-acquirer-assessment.md
```

Reason:

- It is the next foundation document after `doc-00`, `doc-01`, and `doc-02`.
- It affects the feasible payment model.
- It affects PSP and acquirer selection.
- It affects supported funding methods.
- It affects settlement and payout design.
- It affects compliance obligations.
- It affects risk controls.
- It affects later product and engineering specifications.
- It should be drafted before detailed payment-domain specs.

After `doc-03`, the recommended next document is:

```text
docs/00-foundation/doc-04-compliance-certification-roadmap-control-framework.md
```

Reason:

- It establishes compliance-readiness direction.
- It informs ISMS policy sequencing.
- It informs security control requirements.
- It informs audit evidence planning.
- It informs testing, monitoring, and operational readiness.

---

## 9. Recommended Drafting Order

The recommended drafting order from the current state is:

1. `docs/00-foundation/doc-03-regulatory-psp-acquirer-assessment.md`
2. `docs/00-foundation/doc-04-compliance-certification-roadmap-control-framework.md`
3. `docs/01-product/doc-05-master-prd-feature-requirement-index.md`
4. `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md`
5. `docs/01-product/doc-07-content-disclosure-user-authorization-spec.md`
6. `docs/01-product/doc-08-notification-receipt-communication-spec.md`
7. `docs/02-payment-domain/doc-09-payment-request-multi-funding-source-settlement.md`
8. `docs/02-payment-domain/doc-10-payout-reconciliation.md`
9. `docs/02-payment-domain/doc-11-refund-cancellation-chargeback.md`
10. `docs/03-bill-verification/doc-12-bill-category-document-ai-ocr-payee-verification-spec.md`
11. `docs/04-growth-ecosystem/doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md`
12. `docs/05-risk-compliance-privacy/doc-14-aml-anti-cashout-fraud-dynamic-auth-risk-control-spec.md`
13. `docs/05-risk-compliance-privacy/doc-15-privacy-data-protection-record-retention-spec.md`
14. `docs/06-engineering/doc-16-technical-architecture-spec.md`
15. `docs/06-engineering/doc-17-api-third-party-integration-spec.md`
16. `docs/06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md`
17. `docs/06-engineering/api/openapi.yaml`
18. `docs/07-security-access-control /doc-19-security-tokenization-authentication-admin-control-spec.md`
19. `docs/08-qa-release-operations/doc-20-testing-uat-golive-checklist.md`
20. `docs/08-qa-release-operations/doc-21-monitoring-incident-response-operational-sops.md`
21. `docs/99-isms-policies/99-01-information-security-policy.md`
22. `docs/99-isms-policies/99-02-acceptable-use-policy.md`
23. `docs/99-isms-policies/99-03-access-control-policy.md`
24. `docs/99-isms-policies/99-04-cryptography-policy.md`
25. `docs/99-isms-policies/99-05-data-classification-handling-policy.md`
26. `docs/99-isms-policies/99-06-asset-management-policy.md`
27. `docs/99-isms-policies/99-07-supplier-vendor-security-policy.md`
28. `docs/99-isms-policies/99-08-hr-security-policy.md`
29. `docs/99-isms-policies/99-09-physical-environmental-security-policy.md`
30. `docs/99-isms-policies/99-10-change-management-policy.md`
31. `docs/99-isms-policies/99-11-vulnerability-management-policy.md`
32. `docs/99-isms-policies/99-12-secure-development-policy.md`
33. `docs/99-isms-policies/99-13-incident-management-policy.md`
34. `docs/99-isms-policies/99-14-business-continuity-disaster-recovery-policy.md`
35. `docs/99-isms-policies/99-15-logging-monitoring-policy.md`
36. `docs/99-isms-policies/99-16-backup-restore-policy.md`
37. `docs/99-isms-policies/99-17-risk-assessment-methodology.md`
38. `docs/99-isms-policies/99-18-statement-of-applicability.md`
39. `docs/99-isms-policies/99-19-internal-audit-programme.md`
40. `docs/99-isms-policies/99-20-management-review-procedure.md`

---

## 10. Dependency Rules

### 10.1 Foundation Dependencies

Do not draft detailed product, payment, engineering, security, or ISMS documents before the foundation layer is complete, unless explicitly instructed.

Foundation layer:

```text
doc-00
doc-01
doc-02
doc-03
doc-04
```

Current foundation status:

| Document | Status |
|---|---|
| `doc-00` | Drafted |
| `doc-01` | Drafted |
| `doc-02` | Drafted |
| `doc-03` | Planned |
| `doc-04` | Planned |

### 10.2 Product Dependencies

Product documents should follow foundation documents.

Product layer:

```text
doc-05
doc-06
doc-07
doc-08
```

### 10.3 Payment Dependencies

Payment-domain documents should follow foundation and master PRD documents.

Payment layer:

```text
doc-09
doc-10
doc-11
```

Payment-domain documents depend especially on:

- `doc-03`
- `doc-05`
- `doc-06`
- `doc-07`
- `doc-08`

### 10.4 Risk and Privacy Dependencies

Risk and privacy documents depend on:

- `doc-03`
- `doc-04`
- `doc-09`
- `doc-10`
- `doc-11`
- `doc-12`

### 10.5 Engineering Dependencies

Engineering documents should follow enough product, payment, risk, and privacy specification detail to avoid architectural drift.

Engineering documents depend especially on:

- `doc-05`
- `doc-09`
- `doc-10`
- `doc-11`
- `doc-12`
- `doc-14`
- `doc-15`

### 10.6 Security Dependencies

Security and access-control work depends on:

- `doc-04`
- `doc-14`
- `doc-15`
- `doc-16`
- `doc-18`

### 10.7 ISMS Policy Dependencies

ISMS policies should be drafted after enough foundation, compliance, risk, privacy, security, and operational context exists.

ISMS policies depend especially on:

- `doc-04`
- `doc-14`
- `doc-15`
- `doc-19`
- `doc-20`
- `doc-21`

---

## 11. AI Working Rules

Future AI sessions must follow these rules.

### 11.1 Context Rules

- Use this continuation context as the starting point.
- Use `doc-00` as the documentation governance source of truth.
- Use `doc-01` as the product positioning source of truth.
- Use `doc-02` as the business model source of truth.
- Do not rely on memory from earlier conversations.
- If the content of a drafted document is not provided, do not invent its detailed contents.
- If needed information is missing, create assumptions or open questions instead of guessing.

### 11.2 Status Rules

- Treat `doc-00`, `doc-01`, and `doc-02` as **Drafted**.
- Treat all other listed documents as **Planned** unless the user states otherwise.
- Do not mark any document as **Drafted**, **Reviewed**, **Approved**, or **Deprecated** unless explicitly instructed.
- Do not suggest drafting a document that is already marked as **Drafted**, unless the task is to revise or reconcile it.

### 11.3 Repo Rules

- Use exact repo paths from this context.
- Do not invent folders.
- Do not invent files.
- Do not silently correct repo spelling.
- Do not rename `docs/desicion-log/` unless explicitly instructed.
- Confirm the actual path before scripting against `docs/07-security-access-control /` because it may contain a trailing space.

### 11.4 Drafting Rules

When drafting any document:

- Follow the governance rules from `doc-00`.
- Align with the product boundaries from `doc-01`.
- Align with the business model from `doc-02`.
- Preserve the bill-backed nature of PayPlus.
- Avoid positioning PayPlus as a wallet, bank, cashout tool, lending product, crypto product, or unrestricted remittance product.
- Include assumptions where needed.
- Include open questions where facts are not confirmed.
- Include dependencies on upstream and downstream documents.
- Include acceptance criteria.
- Include traceability references where possible.
- Include changelog entries when applicable.
- Avoid legal conclusions unless provided by qualified counsel.
- Avoid claiming regulatory approval, licensing status, certification status, or PSP approval unless explicitly confirmed.

### 11.5 Regulatory and Compliance Rules

For regulatory, PSP, acquirer, compliance, privacy, security, AML, or financial-risk content:

- Do not provide final legal advice.
- Use “to be confirmed by counsel,” “subject to PSP/acquirer review,” or “requires jurisdiction-specific confirmation” where appropriate.
- Identify assumptions clearly.
- Identify decision points.
- Identify evidence requirements.
- Identify operational controls.
- Identify dependencies on licensed partners, PSPs, acquirers, or regulated service providers where applicable.

### 11.6 Product Scope Rules

The following are in scope unless later changed by formal decision:

- Bill-backed payments.
- Approved bill categories.
- Payee verification.
- User authorization.
- Supported funding methods.
- PSP/acquirer integration.
- Settlement and payout coordination.
- Refund and chargeback handling.
- Reconciliation.
- Promotions with abuse controls.
- Fraud and AML controls.
- Privacy and data retention controls.
- Security and access control.
- Monitoring and incident response.

The following are out of scope unless later changed by formal decision:

- General wallet functionality.
- Stored value accounts.
- User-to-user money transfer.
- Cash withdrawal.
- Open-loop remittance.
- Banking services.
- Credit issuance.
- Crypto custody or crypto payment rails.
- Unverified bill payment.
- Unrestricted payee payout.

### 11.7 Output Rules

When producing documentation:

- Use CommonMark Markdown.
- Use clear headings.
- Use tables where useful.
- Use requirement-style language where appropriate.
- Prefer explicit statuses over vague language.
- Keep document status consistent with the continuation context.
- Do not use unsupported Mermaid or diagram syntax unless specifically requested.
- Do not generate implementation code unless the task asks for engineering or API content.
- If web research is required for current regulatory or PSP details, state that external verification is needed before finalizing.

---

## 12. Recommended Prompt For Next Session

Use this prompt when starting a new session:

```text
We are continuing the PayPlus documentation repo.

Use this continuation context as the current source of project progress.
Do not rely on memory from earlier sessions.

Known drafted documents:
- docs/00-foundation/doc-00-documentation-governance.md
- docs/00-foundation/doc-01-project-charter-product-positioning.md
- docs/00-foundation/doc-02-business-model-unit-economics.md

All other listed documents are Planned unless I state otherwise.

Current task:
- Draft docs/00-foundation/doc-03-regulatory-psp-acquirer-assessment.md

Use these source documents:
- docs/ai-context/project-continuation-context.md
- docs/00-foundation/doc-00-documentation-governance.md
- docs/00-foundation/doc-01-project-charter-product-positioning.md
- docs/00-foundation/doc-02-business-model-unit-economics.md

Rules:
- Follow doc-00 governance.
- Preserve PayPlus as bill-backed.
- Do not position PayPlus as a wallet, bank, cashout product, remittance product, lending product, or crypto product.
- Do not invent repo paths.
- Do not invent legal conclusions.
- Mark unresolved items as assumptions or open questions.
- Treat regulatory and PSP details as subject to counsel, PSP, and acquirer confirmation.
```

---

## 13. Next Task Packet

For the next drafting task, provide:

```text
Target file:
docs/00-foundation/doc-03-regulatory-psp-acquirer-assessment.md

Required context:
- docs/ai-context/project-continuation-context.md
- docs/00-foundation/doc-00-documentation-governance.md
- docs/00-foundation/doc-01-project-charter-product-positioning.md
- docs/00-foundation/doc-02-business-model-unit-economics.md

Expected output:
- Full Markdown draft for doc-03
- Aligned with doc-00 to doc-02
- Includes assumptions
- Includes open questions
- Includes decision points
- Includes dependencies
- Includes acceptance criteria
- Includes traceability
- Includes changelog
```

---

## 14. Change Log For This Context

| Date | Change | Reason |
|---|---|---|
| `2026-05-14` | Updated continuation context to mark `doc-00` through `doc-02` as Drafted and all remaining documents as Planned. | Corrected project progress and replaced unknown status with planned status. |

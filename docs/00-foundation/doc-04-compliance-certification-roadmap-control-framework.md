---
document_id: DOC-04
title: Compliance Certification Roadmap & Control Framework
version: 0.1.0
status: Draft
last_updated: 2026-05-26
classification: Internal
owner: Legal / Compliance
reviewers:
  - Project Owner
  - Product Owner
  - Legal / Compliance
  - Risk Lead
  - Security Lead
  - Payments Lead
  - Engineering Lead
  - Operations Lead
  - Finance
approvers:
  - Project Owner
  - Legal / Compliance Lead
  - Risk Lead
  - Security Lead
  - Payments Lead
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Project Charter & Product Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-17 API & Third-party Integration
  - DOC-19 Security, Tokenization & Authentication
---

# DOC-04 — Compliance Certification Roadmap & Control Framework

## 1. Purpose

This document defines the compliance roadmap and control framework for PayPlus.

It provides a structured approach for identifying, planning, assigning, validating, and maintaining compliance controls required for MVP launch and future scaling.

This document is intended to guide the drafting and review of downstream product, payment, risk, privacy, security, operational, and integration documents.

It answers:

- Which compliance domains must be considered for MVP.
- Which certifications, reviews, approvals, or control validations may be required.
- Which documents are responsible for detailed control design.
- Which launch-readiness gates must be completed before production release.
- How compliance evidence should be organized and maintained.

This document does not provide final legal advice, certification evidence, technical implementation details, or operational SOPs.

---

## 2. Scope

This document covers:

- Compliance control domains.
- Certification and approval roadmap.
- MVP control framework.
- Ownership and evidence expectations.
- Launch readiness controls.
- Change governance expectations.
- Dependencies, risks, assumptions, and open questions.

This document does not define detailed requirements for:

| Area | Primary Document |
|---|---|
| Regulatory classification, PSP/acquirer approval, and payment partner assessment | `DOC-03` |
| Product requirements and feature-level acceptance criteria | `DOC-05` |
| Payment request lifecycle, funding, settlement, and payment state logic | `DOC-09` |
| Payout processing, finance reconciliation, and payout exceptions | `DOC-10` |
| Refunds, cancellations, disputes, and chargebacks | `DOC-11` |
| Bill category rules, OCR, document AI, and payee verification | `DOC-12` |
| AML, fraud, anti-cashout, velocity rules, and risk monitoring | `DOC-14` |
| Privacy, data protection, record retention, and data subject handling | `DOC-15` |
| API contracts, webhook handling, and third-party integration details | `DOC-17` |
| Security architecture, authentication, tokenization, encryption, and PCI implementation | `DOC-19` |
| Engineering repository structure, codebase layout, and deployment design | Engineering architecture documentation |

---

## 3. Compliance Framework Principles

PayPlus compliance planning should follow these principles.

| Principle | Requirement |
|---|---|
| Risk-based controls | Controls should be proportionate to product risk, payment method, bill category, payee type, transaction value, and regulatory exposure. |
| Documented accountability | Each compliance area must have a named owner, reviewer, approver, and evidence source. |
| Launch-gate discipline | MVP launch should not proceed until required legal, compliance, partner, security, privacy, risk, and operations gates are complete. |
| No hidden implementation | Compliance requirements should be traceable from policy to product requirements, technical controls, operational procedures, and evidence. |
| Least-overlap documentation | DOC-04 defines the framework and roadmap; downstream documents define detailed requirements and procedures. |
| Evidence retention | Compliance decisions, approvals, control validations, exceptions, and risk acceptances must be retained. |
| Change control | Material changes to payment methods, bill categories, payee types, risk rules, data handling, or partners must trigger compliance review. |

---

## 4. Compliance Domains

The following compliance domains must be assessed for MVP.

| Domain | Objective | Detailed Control Document |
|---|---|---|
| Regulatory model | Confirm PayPlus operating model, licensing position, and product boundaries. | `DOC-03` |
| PSP/acquirer and partner approval | Confirm partner acceptance of payment methods, categories, settlement, and risk model. | `DOC-03`, `DOC-17` |
| Payment controls | Ensure funding, authorization, settlement, and payment status behavior follow approved rules. | `DOC-09` |
| Payout and reconciliation controls | Ensure payouts are authorized, traceable, reconciled, and exception-managed. | `DOC-10` |
| Refund and dispute controls | Ensure refunds, cancellations, chargebacks, and disputes follow approved rules. | `DOC-11` |
| Bill and payee controls | Ensure eligible bills and payees are verified according to category risk. | `DOC-12` |
| AML / CTF controls | Define customer, payee, transaction, monitoring, escalation, and recordkeeping controls. | `DOC-14` |
| Anti-cashout and fraud controls | Prevent fake bills, self-payment, collusion, refund abuse, and unauthorized use. | `DOC-14` |
| Privacy and data protection | Protect personal data, bill documents, retention, consent, access, and deletion rights. | `DOC-15` |
| Security and PCI | Protect systems, payment credentials, authentication, encryption, secrets, logs, and card data scope. | `DOC-19` |
| Third-party integration controls | Ensure APIs, webhooks, partner credentials, environments, and integration monitoring are controlled. | `DOC-17` |
| Operational readiness | Ensure support, escalation, manual review, incident handling, and evidence handling are launch-ready. | Operations SOPs / relevant DOCs |
| Finance and accounting controls | Ensure fee, settlement, payout, refund, reserve, and reconciliation records are accurate. | `DOC-02`, `DOC-10`, `DOC-11` |

---

## 5. Certification and Approval Roadmap

PayPlus may require a combination of legal reviews, partner approvals, internal control sign-offs, and external certifications.

The exact requirements depend on the final operating model, PSP/acquirer setup, payment methods, data handling, and security architecture.

### 5.1 Roadmap Stages

| Stage | Objective | Output |
|---|---|---|
| Stage 1 — Model assessment | Confirm regulatory positioning, product boundaries, and partner feasibility. | Legal/compliance assessment, partner due diligence outputs. |
| Stage 2 — Control design | Define required controls across product, payment, payout, risk, privacy, security, and operations. | Approved downstream requirements documents. |
| Stage 3 — Implementation readiness | Confirm controls are implemented or planned for MVP release scope. | Requirements traceability, test coverage, launch checklist. |
| Stage 4 — Evidence validation | Confirm evidence exists for approvals, controls, testing, partner setup, and exceptions. | Compliance evidence pack. |
| Stage 5 — Launch approval | Confirm all required gates are approved, conditionally approved, or risk-accepted. | Launch approval decision. |
| Stage 6 — Post-launch monitoring | Monitor incidents, exceptions, disputes, fraud signals, reconciliation issues, and regulatory changes. | Periodic compliance review reports. |

### 5.2 Potential Certifications / Reviews

The following reviews or certifications may be required or recommended depending on final scope.

| Area | Type | Applicability |
|---|---|---|
| Legal operating model review | Legal / compliance review | Required before MVP launch. |
| PSP/acquirer underwriting approval | Partner approval | Required before enabling payment processing. |
| Payment method approval | Partner approval | Required for each supported funding or payout method. |
| Category approval | Internal + partner approval | Required before enabling each bill category. |
| Personal payee approval | Legal / risk / partner approval | Required if personal payees are supported. |
| AML / CTF control review | Compliance / risk review | Required based on final operating model and risk exposure. |
| Privacy impact assessment | Legal / privacy review | Required if sensitive bill documents, OCR, identity data, or payee data are processed. |
| Security review | Security review | Required before production launch. |
| PCI scope assessment | Security / payment review | Required if card payments are supported. |
| Penetration testing | Security validation | Recommended or required based on launch risk and partner expectations. |
| Incident response readiness | Security / operations review | Required before launch. |
| Reconciliation readiness review | Finance / operations review | Required before launch. |
| Support and complaint readiness review | Operations review | Required before launch. |

DOC-04 does not determine whether a formal external certification is mandatory. That determination must be made by Legal / Compliance, Security, PSP/acquirer partners, and other applicable reviewers.

---

## 6. MVP Control Framework

The following table defines the MVP control framework at a summary level.

Detailed control requirements belong in the referenced documents.

| Control ID | Control Area | Control Objective | Owner | Evidence Source |
|---|---|---|---|---|
| `CTRL-DOC04-001` | Regulatory model | Confirm legal and regulatory viability of MVP operating model. | Legal / Compliance | Legal review memo, DOC-03 approval. |
| `CTRL-DOC04-002` | Product boundary | Confirm PayPlus is not implemented or described as wallet, remittance, cashout, payroll, lending, or crypto product. | Product / Legal | Product copy review, DOC-01, DOC-03. |
| `CTRL-DOC04-003` | PSP/acquirer approval | Confirm processing partner approval for MVP use cases. | Payments Lead | Partner approval record, underwriting confirmation. |
| `CTRL-DOC04-004` | Payment method approval | Confirm each MVP funding method is approved and documented. | Payments Lead | Partner docs, DOC-09, DOC-17. |
| `CTRL-DOC04-005` | Payout method approval | Confirm payout methods are approved and operationally ready. | Payments / Operations | DOC-10, bank/partner records. |
| `CTRL-DOC04-006` | Category governance | Confirm MVP bill categories are approved, limited, deferred, or prohibited. | Product / Risk | Category approval matrix, DOC-12. |
| `CTRL-DOC04-007` | Payee governance | Confirm payee types and personal payee policy are approved. | Risk / Compliance | Payee policy, DOC-12, DOC-14. |
| `CTRL-DOC04-008` | AML / CTF controls | Confirm required risk-based AML controls are defined. | Compliance / Risk | DOC-14. |
| `CTRL-DOC04-009` | Fraud / anti-cashout controls | Confirm controls exist to prevent cashout, fake bills, self-payment, and collusion. | Risk Lead | DOC-14. |
| `CTRL-DOC04-010` | Refund / chargeback controls | Confirm refund, cancellation, dispute, and chargeback rules are defined. | Payments / Operations | DOC-11. |
| `CTRL-DOC04-011` | Reconciliation controls | Confirm payment, settlement, payout, and fee reconciliation requirements are defined. | Finance / Operations | DOC-10. |
| `CTRL-DOC04-012` | Privacy controls | Confirm personal data, document handling, consent, retention, and deletion controls are defined. | Legal / Privacy | DOC-15. |
| `CTRL-DOC04-013` | Security controls | Confirm access control, encryption, logging, secrets, incident response, and infrastructure security controls are defined. | Security Lead | DOC-19. |
| `CTRL-DOC04-014` | PCI/tokenization controls | Confirm card data scope and tokenization approach are approved. | Security / Payments | PCI scope assessment, DOC-19. |
| `CTRL-DOC04-015` | Third-party integration controls | Confirm API, webhook, credential, environment, and partner monitoring controls are defined. | Engineering / Payments | DOC-17. |
| `CTRL-DOC04-016` | Operational readiness | Confirm support, escalation, manual review, and exception-handling readiness. | Operations Lead | SOPs, launch checklist. |
| `CTRL-DOC04-017` | Evidence retention | Confirm approval records, audit logs, transaction evidence, and control evidence are retained. | Compliance / Operations | Evidence register, DOC-15. |
| `CTRL-DOC04-018` | Change governance | Confirm material changes trigger compliance review and approval. | Project Owner | Change log, DOC-00. |

---

## 7. Evidence Framework

Compliance evidence should be organized so that approvals, decisions, controls, and exceptions can be reviewed later.

### 7.1 Evidence Categories

| Evidence Category | Examples |
|---|---|
| Legal / compliance evidence | Legal review memo, licensing assessment, regulatory position notes, risk acceptance records. |
| Partner evidence | PSP/acquirer approval, underwriting records, payment method enablement, category approval, settlement terms. |
| Product evidence | Approved product positioning, disclosures, user terms, feature requirements, category restrictions. |
| Risk evidence | AML controls, fraud controls, anti-cashout rules, manual review criteria, risk decisions. |
| Privacy evidence | Data inventory, privacy impact assessment, retention schedule, consent language, deletion handling. |
| Security evidence | Security review, PCI scope assessment, penetration test report, incident response plan, access review. |
| Operational evidence | SOPs, support workflows, escalation paths, training materials, exception logs. |
| Finance evidence | Settlement reports, reconciliation procedures, fee schedules, reserve terms, refund and chargeback records. |
| Change governance evidence | Change requests, approval records, release notes, risk acceptance, incident follow-up. |

### 7.2 Evidence Ownership

Each evidence item should have:

- Owner.
- Reviewer.
- Approval status.
- Version or date.
- Storage location.
- Retention requirement.
- Related control ID.
- Related document ID.
- Exception status, if any.

Detailed retention schedules belong in `DOC-15`.

---

## 8. Launch Readiness Gates

The following gates should be completed before MVP launch.

| Gate ID | Gate | Required Evidence | Owner |
|---|---|---|---|
| `GATE-DOC04-001` | Regulatory model approved | Legal/compliance approval or risk acceptance. | Legal / Compliance |
| `GATE-DOC04-002` | PSP/acquirer approval completed | Partner approval record and underwriting confirmation. | Payments Lead |
| `GATE-DOC04-003` | Payment method readiness approved | Approved funding-method scope and partner configuration. | Payments Lead |
| `GATE-DOC04-004` | Payout and reconciliation readiness approved | Payout method approval and reconciliation readiness confirmation. | Finance / Operations |
| `GATE-DOC04-005` | Category and payee governance approved | MVP category/payee policy and restrictions. | Product / Risk |
| `GATE-DOC04-006` | AML/fraud/anti-cashout controls approved | Control sign-off from Risk / Compliance. | Risk / Compliance |
| `GATE-DOC04-007` | Privacy and data protection approved | Privacy review, retention approach, and document-handling approval. | Legal / Privacy |
| `GATE-DOC04-008` | Security and PCI readiness approved | Security review and PCI/tokenization scope assessment. | Security Lead |
| `GATE-DOC04-009` | Operational readiness approved | Support, escalation, manual review, exception, and incident readiness. | Operations Lead |
| `GATE-DOC04-010` | Downstream documentation approved | Required downstream documents approved or risk-accepted for MVP. | Project Owner |
| `GATE-DOC04-011` | Final launch decision completed | Final MVP go/no-go decision. | Project Owner |

---

## 9. Change Governance

Material changes must trigger compliance review before release.

### 9.1 Material Change Examples

A change should be considered material if it affects:

- Operating model.
- Launch geography.
- Payment methods.
- Payout methods.
- Bill categories.
- Payee types.
- Personal payee support.
- Domestic helper salary support.
- Fees, rewards, cashback, or promotions.
- Refund or chargeback rules.
- AML, fraud, or risk controls.
- Privacy, data collection, retention, or OCR/document processing.
- Card data handling, tokenization, authentication, or PCI scope.
- PSP, acquirer, bank, wallet, or payment partner.
- Settlement, reconciliation, or reserve process.
- User terms, disclosures, or product positioning.

### 9.2 Change Review Requirements

Material changes should have:

| Requirement | Description |
|---|---|
| Change owner | Person accountable for the change. |
| Impact assessment | Summary of product, legal, payment, risk, privacy, security, operations, and finance impact. |
| Document updates | Required updates to relevant docs. |
| Approval path | Required reviewers and approvers. |
| Evidence | Approval record, testing evidence, partner confirmation, or risk acceptance. |
| Release condition | Whether change is approved, conditionally approved, deferred, or rejected. |

Detailed document governance belongs in `DOC-00`.

---

## 10. Exceptions and Risk Acceptance

Some controls may not be fully implemented before a target release.

Any exception must be documented, reviewed, approved, time-bound, and tracked.

### 10.1 Exception Requirements

Each exception should include:

- Exception ID.
- Control ID.
- Description.
- Reason for exception.
- Risk impact.
- Compensating controls.
- Owner.
- Approver.
- Expiry date.
- Remediation plan.
- Status.

### 10.2 Risk Acceptance

Risk acceptance may be appropriate only where:

- The risk is clearly described.
- Business justification is documented.
- Legal / compliance impact is reviewed.
- Compensating controls exist where needed.
- The acceptance is time-bound.
- The acceptance has an accountable owner.
- Final approval is recorded.

High-risk legal, regulatory, PSP/acquirer, payment, AML, privacy, or security exceptions should not be accepted informally.

---

## 11. Post-Launch Monitoring

After launch, PayPlus should maintain periodic monitoring of compliance and control effectiveness.

### 11.1 Monitoring Areas

| Area | Monitoring Focus |
|---|---|
| Regulatory / legal | Changes in applicable laws, rules, partner requirements, or operating assumptions. |
| PSP/acquirer / partner | Processing issues, reserves, category restrictions, chargebacks, disputes, settlement changes. |
| Payment operations | Payment success rates, failures, retries, pending states, delayed confirmations. |
| Payout / reconciliation | Payout failures, unmatched settlements, reconciliation breaks, bank exceptions. |
| AML / fraud | Suspicious patterns, cashout attempts, fake bills, self-payment, collusion, velocity alerts. |
| Privacy | Data access, retention, deletion requests, document handling incidents. |
| Security | Vulnerabilities, access reviews, incidents, secrets handling, authentication issues. |
| Customer operations | Complaints, support escalations, rejected payments, refund disputes. |
| Finance | Fee accuracy, settlement timing, reserves, chargeback losses, reconciliation aging. |

### 11.2 Review Cadence

| Review Type | Suggested Cadence | Owner |
|---|---:|---|
| Launch hypercare review | Weekly during initial launch period | Project Owner |
| Compliance control review | Monthly during MVP, then quarterly | Legal / Compliance |
| Fraud and risk review | Monthly or risk-triggered | Risk Lead |
| Reconciliation review | Monthly | Finance / Operations |
| Security review | Quarterly or incident-triggered | Security Lead |
| Partner performance review | Quarterly or issue-triggered | Payments Lead |
| Document review | Per governance schedule | Document Owners |

Cadence may be adjusted based on transaction volume, incident history, partner requirements, and risk profile.

---

## 12. Assumptions

| Assumption ID | Assumption | Owner | Status |
|---|---|---|---|
| `ASM-DOC04-001` | PayPlus MVP will launch in Hong Kong only. | Project Owner | Assumed |
| `ASM-DOC04-002` | PayPlus will maintain a bill-backed model and avoid wallet/cashout/remittance positioning. | Product / Legal | Requires validation |
| `ASM-DOC04-003` | PSP/acquirer and payment partner approvals are required before production payment processing. | Payments Lead | Assumed |
| `ASM-DOC04-004` | Card data handling will rely on PSP tokenization or equivalent compliant approach. | Security / Payments | Requires validation |
| `ASM-DOC04-005` | Detailed controls will be defined in downstream domain documents rather than DOC-04. | Project Owner | Assumed |
| `ASM-DOC04-006` | Compliance evidence will be retained in a controlled internal repository. | Compliance | Requires setup |
| `ASM-DOC04-007` | Material changes will follow document and change governance processes. | Project Owner | Assumed |

---

## 13. Risks

| Risk ID | Risk | Impact | Primary Mitigation |
|---|---|---:|---|
| `RISK-DOC04-001` | Compliance controls are incomplete before launch. | High | Use launch gates and evidence checklist. |
| `RISK-DOC04-002` | Required partner approval is missing or conditional. | High | Track partner approvals and launch restrictions. |
| `RISK-DOC04-003` | Legal, PSP/acquirer, risk, privacy, or security requirements conflict. | High | Escalate to Project Owner and obtain written decision. |
| `RISK-DOC04-004` | Controls are documented but not implemented or tested. | High | Require traceability from documents to implementation and validation evidence. |
| `RISK-DOC04-005` | Documentation overlaps or becomes inconsistent across documents. | Medium | Maintain clear ownership and cross-reference rather than duplicate detail. |
| `RISK-DOC04-006` | Material changes bypass compliance review. | High | Enforce change governance and release gates. |
| `RISK-DOC04-007` | Evidence is incomplete or difficult to retrieve. | Medium | Maintain evidence register with ownership and retention requirements. |
| `RISK-DOC04-008` | Post-launch monitoring does not detect emerging risks. | Medium | Define review cadence and escalation process. |

---

## 14. Dependencies

| Dependency ID | Dependency | Owner | Related Document |
|---|---|---|---|
| `DEP-DOC04-001` | Regulatory and partner assessment. | Legal / Payments | `DOC-03` |
| `DEP-DOC04-002` | Product requirement baseline. | Product Owner | `DOC-05` |
| `DEP-DOC04-003` | Payment method and settlement requirements. | Payments / Product | `DOC-09` |
| `DEP-DOC04-004` | Payout and reconciliation requirements. | Finance / Operations | `DOC-10` |
| `DEP-DOC04-005` | Refund and chargeback requirements. | Payments / Operations | `DOC-11` |
| `DEP-DOC04-006` | Bill category and payee controls. | Product / Risk | `DOC-12` |
| `DEP-DOC04-007` | AML, fraud, and anti-cashout controls. | Risk / Compliance | `DOC-14` |
| `DEP-DOC04-008` | Privacy and retention controls. | Legal / Privacy | `DOC-15` |
| `DEP-DOC04-009` | Integration requirements. | Engineering / Payments | `DOC-17` |
| `DEP-DOC04-010` | Security, authentication, tokenization, and PCI controls. | Security / Engineering | `DOC-19` |

---

## 15. Open Questions

| Question ID | Question | Owner | Status |
|---|---|---|---|
| `OQ-DOC04-001` | Which external certifications, if any, are mandatory before MVP launch? | Legal / Security | Open |
| `OQ-DOC04-002` | What formal PCI validation level or scope applies to the selected card integration model? | Security / Payments | Open |
| `OQ-DOC04-003` | Which PSP/acquirer evidence is required for launch approval? | Payments Lead | Open |
| `OQ-DOC04-004` | Is a formal privacy impact assessment required before launch? | Legal / Privacy | Open |
| `OQ-DOC04-005` | What minimum penetration testing or security validation is required before launch? | Security Lead | Open |
| `OQ-DOC04-006` | What compliance evidence repository and retention process will be used? | Compliance / Operations | Open |
| `OQ-DOC04-007` | What launch risks, if any, may be accepted with compensating controls? | Project Owner | Open |
| `OQ-DOC04-008` | What post-launch compliance reporting format and cadence should be adopted? | Legal / Compliance | Open |

---

## 16. MVP Readiness Checklist

| Checklist Item | Owner | Status |
|---|---|---|
| Regulatory model assessment completed. | Legal / Compliance | Not started |
| PSP/acquirer approval evidence obtained. | Payments Lead | Not started |
| Payment method approvals completed. | Payments Lead | Not started |
| Category and payee governance approved. | Product / Risk | Not started |
| AML/fraud/anti-cashout control framework approved. | Risk / Compliance | Not started |
| Privacy and data protection review completed. | Legal / Privacy | Not started |
| Security and PCI scope assessment completed. | Security / Payments | Not started |
| Payout and reconciliation readiness confirmed. | Finance / Operations | Not started |
| Refund and chargeback readiness confirmed. | Payments / Operations | Not started |
| Operational SOP readiness confirmed. | Operations Lead | Not started |
| Compliance evidence register created. | Compliance | Not started |
| Material change process confirmed. | Project Owner | Not started |
| Exceptions and risk acceptances documented. | Project Owner | Not started |
| Final compliance launch sign-off completed. | Project Owner | Not started |

---

## 17. Version History

| Version | Date | Author | Notes |
|---|---|---|---|
| 0.1.0 | 2026-05-26 | Legal / Compliance Draft | Initial draft of compliance certification roadmap and control framework. |

---
document_id: DOC-04
title: Compliance Certification Roadmap & Control Framework
version: 0.2.0
status: Draft
owner: Compliance Lead
reviewers:
  - Legal Lead
  - Risk Lead
  - Security Lead
  - Privacy Lead
  - Payments Lead
  - Product Lead
  - Engineering Lead
  - Operations Lead
approvers:
  - Project Owner
  - Legal Lead
  - Compliance Lead
  - Security Lead
  - Risk Lead
last_updated: 2026-05-26
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Project Charter & Product Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User, Biller, Payee & Partner Onboarding
  - DOC-07 Content, Disclosure & User Communication
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-13 Admin, Risk & Operations Console
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Customer Support, Complaints & Disputes
  - DOC-16 Security, Privacy & Data Protection
  - DOC-17 Infrastructure, Reliability & Observability
  - DOC-18 Data Model, Transaction Ledger & Reporting
  - DOC-20 Launch Readiness, QA & Go-Live Checklist
  - DOC-21 Operating Runbooks & Incident Response
---

# DOC-04 — Compliance Certification Roadmap & Control Framework

## 1. Purpose

This document defines PayPlus’s compliance certification roadmap and control framework for launching, operating, and scaling the product.

It translates regulatory, partner, card network, security, privacy, AML, sanctions, fraud, consumer protection, operational, and audit obligations into a structured set of readiness gates, control domains, evidence requirements, ownership expectations, and certification milestones.

`DOC-04` is not a standalone legal opinion, compliance policy, risk policy, security policy, audit report, or certification attestation.

Instead, it is the coordinating framework used to ensure that compliance obligations identified in `DOC-03` and other foundation documents are implemented, tested, evidenced, approved, and monitored.

---

## 2. Scope

This document covers:

- Compliance certification roadmap.
- Control framework structure.
- Control domains.
- Launch readiness control gates.
- Certification and attestation planning.
- Evidence collection requirements.
- Control ownership and accountability.
- Regulatory, PSP, acquirer, and payout provider readiness.
- AML, sanctions, fraud, and anti-cashout controls.
- Consumer protection and disclosure controls.
- Security, privacy, and PCI-related controls.
- Data retention, reporting, and recordkeeping controls.
- Operational controls.
- Incident, complaint, dispute, and escalation controls.
- Change management controls.
- Vendor and partner oversight controls.
- Monitoring, testing, audit, remediation, and governance.
- Assumptions, constraints, dependencies, risks, open questions, and acceptance criteria.

---

## 3. Out of Scope

This document does not define:

- Final legal conclusions.
- Regulatory licensing strategy.
- Full AML policy.
- Full sanctions policy.
- Full fraud rule logic.
- Complete PCI DSS implementation plan.
- Complete SOC 2 readiness plan.
- Complete privacy program.
- Complete information security policy.
- Technical implementation specifications.
- Product feature requirements.
- Partner contract terms.
- Detailed customer support SOPs.
- Detailed incident response procedures.
- QA test cases.
- Final launch sign-off checklist.

Those details must be maintained in downstream legal, compliance, security, risk, product, engineering, operations, and vendor documents.

---

## 4. Guiding Principles

PayPlus’s compliance control framework should follow these principles:

| Principle | Description |
|---|---|
| Risk-based | Controls should be proportionate to product, jurisdiction, category, payment method, and transaction risk. |
| Evidence-first | Compliance readiness should be supported by documented evidence, not verbal confirmation. |
| Owner-accountable | Every material control should have a named function owner. |
| Partner-aligned | Controls should satisfy PSP, acquirer, payout provider, card network, and other partner requirements. |
| User-transparent | Fees, timing, role, risk, refunds, cancellations, disputes, and privacy practices should be clearly disclosed. |
| Audit-ready | Policies, approvals, records, logs, reports, and decisions should be retained and retrievable. |
| Change-aware | Material changes should trigger reassessment and control updates. |
| Defense-in-depth | Preventive, detective, and corrective controls should be layered across product, risk, operations, and engineering. |
| Scalable | Controls should work for MVP while enabling future jurisdiction, category, and volume expansion. |
| Testable | Controls should have measurable design and operating effectiveness criteria. |

---

## 5. Compliance Roadmap Overview

The roadmap should be managed across phases.

| Phase | Name | Objective | Exit Criteria |
|---|---|---|---|
| `PH-DOC04-001` | Discovery | Identify obligations, risks, partners, jurisdictions, flows, and categories. | Initial obligation inventory and risk assessment completed. |
| `PH-DOC04-002` | Design | Define control domains, owners, policies, procedures, and evidence requirements. | Control matrix and readiness gates approved. |
| `PH-DOC04-003` | Build | Implement product, technical, operational, and partner controls. | Controls implemented in product, systems, workflows, and documentation. |
| `PH-DOC04-004` | Test | Validate control design and operating readiness. | Test results, exceptions, and remediation plans documented. |
| `PH-DOC04-005` | Certify | Obtain internal approvals and required external/partner attestations. | Launch certification package approved. |
| `PH-DOC04-006` | Launch | Operate under defined controls and monitoring. | Launch completed with no unresolved critical compliance gaps. |
| `PH-DOC04-007` | Monitor | Conduct ongoing monitoring, periodic reviews, and control testing. | Ongoing evidence, issues, and remediation tracked. |
| `PH-DOC04-008` | Scale | Reassess controls for new jurisdictions, categories, partners, and volume. | Expansion certification completed before material change. |

---

## 6. Control Framework Structure

Each control should be documented using a standard structure.

| Field | Description |
|---|---|
| Control ID | Unique identifier. |
| Control Domain | Category of control. |
| Control Name | Short control title. |
| Control Objective | What risk or obligation the control addresses. |
| Control Type | Preventive, detective, corrective, directive, or compensating. |
| Frequency | Real-time, per transaction, daily, weekly, monthly, quarterly, annual, event-driven. |
| Owner | Function responsible for operating the control. |
| Reviewer | Function responsible for review or approval. |
| System of Record | Tool, database, repository, partner portal, or process record. |
| Evidence | Evidence required to prove operation. |
| Related Risk | Risk ID or risk category addressed. |
| Related Requirement | Regulation, policy, partner rule, contract, or product requirement. |
| Design Status | Not started, designed, implemented, tested, approved. |
| Operating Status | Not operating, operating with exceptions, operating effectively. |
| Exceptions | Known gaps or deviations. |
| Remediation | Required remediation action and owner. |

---

## 7. Control Domains

PayPlus controls should be organized into the following domains.

| Domain ID | Domain | Primary Owner | Related Documents |
|---|---|---|---|
| `CD-DOC04-001` | Governance, accountability, and approvals | Compliance | DOC-00, DOC-20 |
| `CD-DOC04-002` | Regulatory role, licensing, and legal obligations | Legal / Compliance | DOC-03 |
| `CD-DOC04-003` | PSP, acquirer, card network, and payout provider readiness | Payments | DOC-03, DOC-09, DOC-10 |
| `CD-DOC04-004` | Product eligibility, categories, and payee controls | Product / Compliance | DOC-05, DOC-06 |
| `CD-DOC04-005` | User onboarding, identity, and verification | Compliance / Product | DOC-06 |
| `CD-DOC04-006` | AML, sanctions, anti-cashout, and financial crime | Compliance / Risk | DOC-14 |
| `CD-DOC04-007` | Fraud, abuse, velocity, and transaction risk | Risk | DOC-14 |
| `CD-DOC04-008` | Consumer protection, disclosures, and consent | Legal / Product | DOC-07, DOC-08 |
| `CD-DOC04-009` | Fees, pricing, and commercial controls | Finance / Product | DOC-02, DOC-07 |
| `CD-DOC04-010` | Payment authorization, capture, settlement, and funding | Payments / Engineering | DOC-09 |
| `CD-DOC04-011` | Payout, reconciliation, and ledger controls | Finance / Payments | DOC-10, DOC-18 |
| `CD-DOC04-012` | Refunds, cancellations, chargebacks, and disputes | Operations / Payments | DOC-11, DOC-15 |
| `CD-DOC04-013` | Customer support, complaints, and escalation | Operations | DOC-15 |
| `CD-DOC04-014` | Security, PCI, access, and infrastructure controls | Security / Engineering | DOC-16, DOC-17 |
| `CD-DOC04-015` | Privacy, data protection, and retention | Privacy / Legal | DOC-16 |
| `CD-DOC04-016` | Reporting, recordkeeping, and audit evidence | Compliance / Finance | DOC-18 |
| `CD-DOC04-017` | Vendor and partner oversight | Compliance / Legal / Payments | DOC-03 |
| `CD-DOC04-018` | Incident response, business continuity, and resilience | Security / Operations | DOC-17, DOC-21 |
| `CD-DOC04-019` | Change management and release governance | Engineering / Compliance | DOC-20 |
| `CD-DOC04-020` | Training, awareness, and access certification | Compliance / People Ops | DOC-16, DOC-21 |

---

## 8. Control Matrix

The following starter control matrix should be expanded as product, jurisdiction, partner, and regulatory requirements mature.

| Control ID | Domain | Control Objective | Type | Frequency | Owner | Evidence |
|---|---|---|---|---|---|---|
| `CTRL-DOC04-001` | Governance | Maintain approved document governance and control ownership. | Directive | Quarterly | Compliance | Document register, owner list, approvals. |
| `CTRL-DOC04-002` | Regulatory | Confirm regulatory role and licensing path before launch. | Preventive | Event-driven | Legal / Compliance | DOC-03 assessment, legal memo, approval record. |
| `CTRL-DOC04-003` | Partner readiness | Confirm PSP/acquirer support for use case, categories, and funds flow. | Preventive | Event-driven | Payments | Partner written confirmation, contract, onboarding approval. |
| `CTRL-DOC04-004` | Category eligibility | Maintain approved, restricted, and prohibited category lists. | Preventive | Monthly / Event-driven | Compliance / Product | Category list, approval log, change history. |
| `CTRL-DOC04-005` | Payee verification | Verify payee eligibility before enabling payout. | Preventive | Per payee | Compliance / Operations | Payee verification record, screening result. |
| `CTRL-DOC04-006` | User onboarding | Capture required user information and consent. | Preventive | Per user | Product / Compliance | User profile, consent logs, terms acceptance. |
| `CTRL-DOC04-007` | Sanctions screening | Screen relevant users, payees, and partners against required sanctions lists. | Preventive / Detective | Per onboarding / Ongoing | Compliance | Screening logs, match disposition records. |
| `CTRL-DOC04-008` | Fraud monitoring | Apply transaction risk rules and velocity limits. | Preventive / Detective | Real-time | Risk | Rule configuration, decision logs, alerts. |
| `CTRL-DOC04-009` | Anti-cashout controls | Detect self-payments, circular payments, suspicious refunds, and abuse patterns. | Detective | Real-time / Daily | Risk / Compliance | Alerts, investigation notes, case outcomes. |
| `CTRL-DOC04-010` | Fee disclosure | Display service fee, total amount, and key terms before payment authorization. | Preventive | Per transaction | Product / Legal | UI screenshots, consent logs, test evidence. |
| `CTRL-DOC04-011` | Payment authorization | Capture user authorization and transaction details. | Preventive | Per transaction | Product / Engineering | Authorization logs, transaction record. |
| `CTRL-DOC04-012` | Settlement reconciliation | Reconcile PSP settlement, payout, ledger, and bank records. | Detective | Daily | Finance / Payments | Reconciliation reports, exception log. |
| `CTRL-DOC04-013` | Refund controls | Process refunds according to approved rules and partner capabilities. | Preventive / Corrective | Per refund | Operations / Payments | Refund record, approval log, ledger entry. |
| `CTRL-DOC04-014` | Chargeback controls | Track, evidence, and respond to chargebacks within required deadlines. | Corrective | Per dispute | Operations / Payments | Dispute case, evidence package, outcome. |
| `CTRL-DOC04-015` | Complaint handling | Log, classify, investigate, and resolve complaints. | Corrective | Per complaint | Operations | Complaint register, response records. |
| `CTRL-DOC04-016` | PCI scope control | Keep card data handling within approved PCI scope. | Preventive | Continuous / Annual | Security | PCI scope document, SAQ/AOC, architecture diagram. |
| `CTRL-DOC04-017` | Access control | Restrict admin and sensitive data access based on role. | Preventive | Continuous / Quarterly | Security / Engineering | Access review, role matrix, audit logs. |
| `CTRL-DOC04-018` | Privacy notice and consent | Provide privacy notice and capture required consents. | Preventive | Per user / Event-driven | Privacy / Product | Notice version, consent logs. |
| `CTRL-DOC04-019` | Data retention | Retain and delete records according to approved schedule. | Preventive / Corrective | Continuous / Periodic | Privacy / Engineering | Retention policy, deletion logs. |
| `CTRL-DOC04-020` | Vendor due diligence | Review material vendors and payment partners before production use. | Preventive | Event-driven / Annual | Compliance / Security / Legal | Due diligence checklist, SOC reports, contracts. |
| `CTRL-DOC04-021` | Incident response | Detect, escalate, investigate, and document material incidents. | Corrective | Per incident | Security / Operations | Incident ticket, RCA, notification log. |
| `CTRL-DOC04-022` | Change management | Review product, risk, compliance, and technical changes before release. | Preventive | Per release | Engineering / Compliance | Change tickets, approvals, release notes. |
| `CTRL-DOC04-023` | Regulatory change monitoring | Monitor applicable regulatory, partner, and network changes. | Detective | Monthly / Event-driven | Legal / Compliance | Monitoring log, impact assessment. |
| `CTRL-DOC04-024` | Training | Provide role-based compliance and security training. | Directive | On hire / Annual | Compliance / Security | Training completion records. |
| `CTRL-DOC04-025` | Control testing | Test design and operating effectiveness of key controls. | Detective | Quarterly / Annual | Compliance / Internal Audit | Test plan, samples, results, remediation log. |

---

## 9. Certification and Attestation Roadmap

The required certification and attestation path depends on final product design, partner model, jurisdiction, payment methods, data handling, and customer segments.

Potential certification and attestation areas include:

| Area | Potential Requirement | Owner | Timing |
|---|---|---|---|
| Legal launch approval | Legal memo or legal sign-off for jurisdiction and funds flow. | Legal | Before launch |
| Compliance launch approval | Compliance readiness certification. | Compliance | Before launch |
| PSP/acquirer approval | Underwriting approval, merchant approval, category approval. | Payments | Before production processing |
| Payout provider approval | Payout account approval and rail readiness. | Payments | Before production payouts |
| PCI DSS | SAQ, AOC, ROC, or partner-managed scope depending on card data handling. | Security | Before card processing / Annual |
| SOC 2 readiness | Internal readiness or formal audit planning. | Security | Pre-scale / Annual if pursued |
| Privacy readiness | Privacy notice, data map, DPA, consent and retention controls. | Privacy / Legal | Before launch |
| AML program readiness | AML, sanctions, monitoring, escalation, recordkeeping controls. | Compliance | Before launch |
| Fraud/risk readiness | Fraud rules, velocity limits, review workflows, monitoring dashboards. | Risk | Before launch |
| Consumer disclosure readiness | Terms, checkout disclosures, receipt content, support content. | Legal / Product | Before launch |
| Operational readiness | Support, complaints, disputes, refunds, chargebacks, payout exceptions. | Operations | Before launch |
| Business continuity readiness | Incident response and continuity procedures. | Security / Operations | Before launch or pre-scale |
| Vendor due diligence | Due diligence and contract approval for material vendors. | Compliance / Legal / Security | Before production use |

---

## 10. Launch Certification Package

Before MVP launch, Compliance should assemble a launch certification package.

The package should include:

- Product overview.
- Jurisdiction scope.
- Bill category scope.
- User and payee scope.
- Payment method scope.
- Payout method scope.
- Funds flow diagram.
- Regulatory role assessment.
- Licensing or exemption assessment.
- PSP/acquirer approval evidence.
- Payout provider approval evidence.
- Category approval evidence.
- MCC or classification evidence.
- Fee model approval.
- Consumer disclosure evidence.
- Terms and privacy evidence.
- AML and sanctions control evidence.
- Fraud and anti-cashout control evidence.
- Security and PCI evidence.
- Privacy and data protection evidence.
- Partner due diligence evidence.
- Contract approval evidence.
- Settlement, reserve, and liquidity evidence.
- Reconciliation and ledger readiness evidence.
- Refund and chargeback readiness evidence.
- Support and complaint handling readiness evidence.
- Incident response readiness evidence.
- QA and UAT evidence for compliance-critical flows.
- Open issues and remediation plan.
- Formal approvals.

---

## 11. Launch Readiness Gates

| Gate ID | Gate | Acceptance Condition | Owner |
|---|---|---|---|
| `GATE-DOC04-001` | Obligation inventory complete | Applicable obligations are identified from legal, partner, product, risk, privacy, and security reviews. | Compliance |
| `GATE-DOC04-002` | Regulatory role approved | Regulatory role and licensing path are approved or documented with accepted risk. | Legal / Compliance |
| `GATE-DOC04-003` | Partner approvals obtained | PSP, acquirer, payout provider, and material vendor approvals are obtained. | Payments |
| `GATE-DOC04-004` | Control matrix approved | Required launch controls are documented with owners, evidence, and status. | Compliance |
| `GATE-DOC04-005` | Category controls approved | Approved, restricted, and prohibited category framework is implemented. | Compliance / Product |
| `GATE-DOC04-006` | User and payee controls ready | Onboarding, verification, screening, consent, and eligibility controls are implemented. | Product / Compliance |
| `GATE-DOC04-007` | AML/sanctions controls ready | Required screening, monitoring, escalation, and recordkeeping controls are implemented. | Compliance |
| `GATE-DOC04-008` | Fraud/risk controls ready | Fraud, velocity, anti-cashout, and manual review controls are implemented and tested. | Risk |
| `GATE-DOC04-009` | Fee and disclosure controls ready | Checkout, receipt, terms, privacy, and fee disclosures are approved and tested. | Legal / Product |
| `GATE-DOC04-010` | Payment and settlement controls ready | Authorization, capture, settlement, payout, refund, and reconciliation controls are implemented. | Payments / Finance |
| `GATE-DOC04-011` | Security and PCI controls ready | Security review, PCI scope, access controls, and vulnerability remediation are complete. | Security |
| `GATE-DOC04-012` | Privacy controls ready | Data map, privacy notice, consent, DPA, retention, and deletion controls are ready. | Privacy / Legal |
| `GATE-DOC04-013` | Support and complaints ready | Support, complaint, dispute, and escalation procedures are ready. | Operations |
| `GATE-DOC04-014` | Incident response ready | Incident runbooks, escalation paths, and notification criteria are documented. | Security / Operations |
| `GATE-DOC04-015` | Evidence repository complete | Required evidence is stored in approved repository with version control. | Compliance |
| `GATE-DOC04-016` | Open risks accepted | Critical risks are resolved; remaining risks are formally accepted by authorized approvers. | Compliance / Project Owner |
| `GATE-DOC04-017` | Launch certification approved | Launch certification package is approved by required approvers. | Compliance |

---

## 12. Evidence Repository

Compliance evidence should be stored in an approved repository with:

- Document owner.
- Version history.
- Approval history.
- Access control.
- Retention period.
- Evidence type.
- Related control ID.
- Related gate ID.
- Related risk ID.
- Date collected.
- Source system.
- Reviewer.
- Expiration date, where applicable.

Example evidence categories:

| Evidence Category | Examples |
|---|---|
| Legal | Legal memo, licensing assessment, jurisdiction review, contract review. |
| Partner | Underwriting approval, category approval, MCC confirmation, settlement terms. |
| Product | Screenshots, user flows, PRDs, disclosure screens, consent records. |
| Engineering | Architecture diagrams, release notes, test results, audit logs. |
| Security | PCI scope, vulnerability scan, penetration test, access review, SOC report. |
| Privacy | Data map, DPIA, privacy notice, DPA, consent logs, retention schedule. |
| Compliance | Control matrix, risk assessment, policy approval, monitoring records. |
| Risk | Fraud rules, risk dashboards, alert logs, case reviews. |
| Finance | Reconciliation reports, reserve calculations, settlement files. |
| Operations | SOPs, complaint logs, dispute files, support macros, escalation records. |
| Audit | Control testing plan, sample results, exception log, remediation evidence. |

---

## 13. Control Ownership Model

Control ownership should distinguish between accountable owner, operating owner, reviewer, and approver.

| Role | Responsibility |
|---|---|
| Accountable Owner | Owns control design, operation, remediation, and acceptance of residual risk. |
| Operating Owner | Performs the control activity. |
| Reviewer | Reviews evidence and determines whether the control operated effectively. |
| Approver | Approves control readiness, exceptions, risk acceptance, or launch certification. |
| System Owner | Maintains systems and data supporting the control. |
| Evidence Owner | Ensures evidence is complete, accurate, retained, and retrievable. |

No critical control should lack an accountable owner.

---

## 14. Control Testing

Control testing should evaluate both design effectiveness and operating effectiveness.

| Test Type | Objective | Example |
|---|---|---|
| Design effectiveness | Determine whether control is suitably designed to address the risk. | Review whether fee disclosure appears before authorization. |
| Operating effectiveness | Determine whether control operated consistently over time. | Sample transactions to confirm fee consent logs exist. |
| Technical validation | Confirm system behavior matches requirement. | Test sanctions screening block logic. |
| Evidence review | Confirm evidence is complete and reliable. | Verify reconciliation reports match source files. |
| Walkthrough | Confirm process is understood and executable. | Walk through complaint escalation process. |
| Exception testing | Confirm failures are handled correctly. | Simulate payout failure or chargeback. |
| Access review | Confirm only authorized users have access. | Review admin console role assignments. |

Critical launch controls should be tested before production launch.

---

## 15. Exception and Remediation Management

Control exceptions should be logged and tracked.

| Field | Description |
|---|---|
| Exception ID | Unique exception identifier. |
| Control ID | Related control. |
| Severity | Critical, high, medium, low. |
| Description | Exception details. |
| Detection Date | When issue was found. |
| Owner | Responsible remediation owner. |
| Root Cause | Cause of exception. |
| Impact | Compliance, financial, operational, user, or partner impact. |
| Temporary Mitigation | Interim control or workaround. |
| Remediation Plan | Corrective action. |
| Target Date | Due date. |
| Status | Open, in progress, remediated, accepted risk, closed. |
| Approver | Required approver for closure or risk acceptance. |
| Evidence | Proof of remediation. |

Critical exceptions should block launch unless formally accepted by authorized approvers.

---

## 16. Regulatory and Partner Change Management

PayPlus should monitor and assess changes from:

- Laws and regulations.
- Regulatory guidance.
- Card network rules.
- PSP requirements.
- Acquirer requirements.
- Payout provider requirements.
- Bank partner requirements.
- Privacy requirements.
- Security standards.
- Sanctions lists and financial crime guidance.
- Product feature changes.
- Jurisdiction expansion.
- Category expansion.
- Payment method expansion.
- Payout rail expansion.
- Pricing and fee changes.
- Contract changes.

Each material change should trigger impact assessment and, where needed, updated controls, disclosures, testing, and approvals.

---

## 17. Vendor and Partner Oversight

Material vendors and partners should be subject to risk-based oversight.

Oversight should include:

- Due diligence before engagement.
- Contract review and approval.
- Data protection review.
- Security review.
- Regulatory status review.
- Business continuity review.
- Financial stability review, where relevant.
- Sub-processor review.
- Category and use-case approval.
- Annual or periodic reassessment.
- Monitoring of incidents and service degradation.
- Review of SOC reports or equivalent controls.
- Review of compliance attestations.
- Tracking of contractual obligations.
- Termination and contingency planning.

Payment partners should receive enhanced review due to direct operational, regulatory, settlement, and card network dependency.

---

## 18. Training and Awareness

Role-based training should be provided to relevant employees and contractors.

Training topics may include:

- Product compliance overview.
- User fee and disclosure rules.
- AML and sanctions escalation.
- Fraud and anti-cashout typologies.
- Restricted and prohibited categories.
- Privacy and data handling.
- Security and access control.
- PCI awareness.
- Complaint handling.
- Dispute and chargeback handling.
- Incident escalation.
- Vendor management.
- Change management.
- Recordkeeping.

Training completion should be tracked and retained.

---

## 19. Monitoring and Reporting

Compliance, Risk, Finance, Payments, Security, and Operations should define monitoring dashboards and reports.

Candidate metrics include:

| Area | Example Metrics |
|---|---|
| Compliance | Open control exceptions, overdue remediation, pending approvals, training completion. |
| AML/sanctions | Screening volume, true matches, false positives, escalations, investigation aging. |
| Fraud | Decline rate, manual review rate, confirmed fraud rate, loss rate, velocity triggers. |
| Anti-cashout | Self-payment alerts, circular payment alerts, refund abuse alerts, suspicious payee concentration. |
| Payments | Authorization rate, capture failures, settlement delays, payout failures, refund failures. |
| Chargebacks | Chargeback rate, win rate, reason codes, aging, loss amount. |
| Complaints | Complaint volume, categories, response SLA, escalation rate. |
| Reconciliation | Unmatched transactions, unresolved settlement exceptions, ledger breaks. |
| Security | Vulnerabilities, access review exceptions, incidents, mean time to resolve. |
| Privacy | Data requests, deletion requests, consent exceptions, retention exceptions. |
| Vendors | Open due diligence items, incidents, SLA breaches, contract renewals. |

Material issues should be escalated through governance forums.

---

## 20. Governance Forums

PayPlus should establish governance forums appropriate to product maturity.

| Forum | Frequency | Purpose | Participants |
|---|---|---|---|
| Launch Readiness Review | Weekly during pre-launch | Track readiness gates, blockers, risks, and evidence. | Product, Compliance, Legal, Payments, Risk, Security, Finance, Operations. |
| Risk and Compliance Review | Monthly | Review compliance metrics, incidents, exceptions, and remediation. | Compliance, Legal, Risk, Operations, Security. |
| Payments Operations Review | Weekly / Monthly | Review settlement, payout, chargeback, reconciliation, and partner issues. | Payments, Finance, Operations, Engineering. |
| Security and Privacy Review | Monthly / Quarterly | Review security posture, access, privacy, incidents, vendor risks. | Security, Privacy, Engineering, Legal. |
| Vendor Review | Quarterly / Annual | Review material vendor performance, attestations, incidents, and renewals. | Compliance, Legal, Security, Payments, Procurement. |
| Executive Risk Committee | Quarterly / Event-driven | Approve risk appetite, launch risk acceptance, major remediation, and expansion. | Executive sponsors and control owners. |

---

## 21. Relationship to Launch Readiness

`DOC-04` provides the compliance control framework.

`DOC-20 Launch Readiness, QA & Go-Live Checklist` should convert the gates and evidence requirements in this document into a tactical launch checklist.

No MVP launch should proceed until:

- Required `DOC-04` gates are satisfied.
- Critical controls are implemented and tested.
- Evidence package is complete.
- Critical exceptions are closed or accepted.
- Required approvals are obtained.

---

## 22. Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
|---|---|---|---|
| `ASM-DOC04-001` | PayPlus will operate under a documented control framework before launch. | Compliance | Open |
| `ASM-DOC04-002` | Legal and regulatory conclusions from `DOC-03` will inform control requirements. | Legal / Compliance | Open |
| `ASM-DOC04-003` | PSP, acquirer, payout provider, and vendor obligations will be incorporated into controls. | Payments / Compliance | Open |
| `ASM-DOC04-004` | Key controls will be evidence-based and testable. | Compliance / Audit | Open |
| `ASM-DOC04-005` | Compliance evidence will be stored in a central repository. | Compliance | Open |
| `ASM-DOC04-006` | MVP launch can occur before formal external certifications only if required controls and partner approvals are satisfied. | Project Owner / Compliance | Open |
| `ASM-DOC04-007` | PCI scope will depend on final card data handling architecture. | Security | Open |
| `ASM-DOC04-008` | AML and sanctions requirements will depend on legal role, jurisdiction, and partner obligations. | Legal / Compliance | Open |
| `ASM-DOC04-009` | Fraud and anti-cashout controls are required even if formal AML obligations are limited. | Risk / Compliance | Open |
| `ASM-DOC04-010` | Ongoing monitoring will be required after launch. | Compliance / Risk | Open |

---

## 23. Constraints

| Constraint ID | Constraint | Impact | Owner |
|---|---|---|---|
| `CON-DOC04-001` | No launch without documented regulatory and partner readiness. | Blocks unapproved flows. | Legal / Compliance / Payments |
| `CON-DOC04-002` | No launch without critical control owners assigned. | Blocks unmanaged compliance risk. | Compliance |
| `CON-DOC04-003` | No launch with unresolved critical control exceptions unless formally accepted. | Requires remediation or risk acceptance. | Project Owner / Compliance |
| `CON-DOC04-004` | No production card processing without approved PCI scope and required security controls. | Blocks card payments. | Security |
| `CON-DOC04-005` | No restricted category launch without category approval. | Blocks high-risk unsupported categories. | Compliance / Product |
| `CON-DOC04-006` | No material vendor production use without due diligence and contract approval. | Blocks vendor dependency. | Legal / Compliance / Security |
| `CON-DOC04-007` | No user fee launch without disclosure and fee review. | Blocks pricing implementation. | Legal / Product |
| `CON-DOC04-008` | No production payout flow without reconciliation and exception controls. | Blocks payout launch. | Payments / Finance |
| `CON-DOC04-009` | Control evidence must be retained and retrievable. | Enables audit and partner review. | Compliance |
| `CON-DOC04-010` | Material changes require reassessment. | Prevents stale approvals and control gaps. | Compliance / Engineering |

---

## 24. Dependencies

| Dependency ID | Dependency | Required For | Owner | Status |
|---|---|---|---|---|
| `DEP-DOC04-001` | Completed `DOC-03` regulatory, PSP, and acquirer assessment. | Control requirements and launch gates. | Legal / Compliance / Payments | Open |
| `DEP-DOC04-002` | Product scope and MVP feature list. | Control scoping and testing. | Product | Open |
| `DEP-DOC04-003` | Jurisdiction scope. | Legal, privacy, AML, disclosure, and recordkeeping controls. | Legal / Project Owner | Open |
| `DEP-DOC04-004` | Bill category scope. | Category, risk, partner, and fraud controls. | Product / Compliance | Open |
| `DEP-DOC04-005` | User and payee onboarding model. | KYC/KYB, verification, consent, and screening controls. | Product / Compliance | Open |
| `DEP-DOC04-006` | Payment and payout provider selection. | Partner, settlement, payout, and reconciliation controls. | Payments | Open |
| `DEP-DOC04-007` | Card data architecture. | PCI scope and security controls. | Security / Engineering | Open |
| `DEP-DOC04-008` | Risk rules and fraud tooling. | Fraud, AML, and anti-cashout readiness. | Risk / Engineering | Open |
| `DEP-DOC04-009` | Terms, privacy notice, and disclosure drafts. | Consumer protection and consent controls. | Legal / Product | Open |
| `DEP-DOC04-010` | Ledger and reporting design. | Recordkeeping, reconciliation, and monitoring evidence. | Finance / Engineering | Open |
| `DEP-DOC04-011` | Operations SOPs. | Complaint, dispute, refund, chargeback, and incident readiness. | Operations | Open |
| `DEP-DOC04-012` | Evidence repository and access model. | Control evidence retention and review. | Compliance / Security | Open |
| `DEP-DOC04-013` | QA/UAT test results. | Launch certification package. | Product / Engineering / QA | Open |
| `DEP-DOC04-014` | Partner contracts and due diligence records. | Vendor and partner oversight controls. | Legal / Payments | Open |

---

## 25. Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
|---|---|---|---|---|---|
| `RISK-DOC04-001` | Compliance obligations are incomplete or misunderstood. | Launch with control gaps or regulatory/partner breach. | Maintain obligation inventory and legal/partner review. | Compliance / Legal | Open |
| `RISK-DOC04-002` | Controls are documented but not implemented. | False readiness and audit failure. | Require evidence and testing before launch approval. | Compliance | Open |
| `RISK-DOC04-003` | Controls lack clear ownership. | Operational failures and remediation delays. | Assign accountable owners and reviewers for each control. | Compliance | Open |
| `RISK-DOC04-004` | Evidence is incomplete or not retrievable. | Audit, partner, and incident response failure. | Central evidence repository with retention and access rules. | Compliance | Open |
| `RISK-DOC04-005` | PSP/acquirer requirements are not reflected in controls. | Partner termination, fines, or processing disruption. | Partner readiness confirmation and contract obligation mapping. | Payments / Compliance | Open |
| `RISK-DOC04-006` | Security or PCI scope is underestimated. | Data security incident, compliance failure, costly remediation. | PCI scope review, security architecture review, vendor tokenization. | Security | Open |
| `RISK-DOC04-007` | AML, sanctions, or fraud controls are insufficient. | Financial crime exposure, losses, partner action. | Risk-based AML/fraud control design and monitoring. | Compliance / Risk | Open |
| `RISK-DOC04-008` | User disclosures are incomplete or misleading. | Complaints, disputes, regulatory risk. | Legal review and UI evidence testing. | Legal / Product | Open |
| `RISK-DOC04-009` | Reconciliation controls fail to detect settlement or payout breaks. | Financial loss and inaccurate reporting. | Daily reconciliation, exception logs, ledger controls. | Finance / Payments | Open |
| `RISK-DOC04-010` | Critical exceptions are waived without proper approval. | Unaccepted residual risk. | Formal exception and risk acceptance process. | Compliance / Project Owner | Open |
| `RISK-DOC04-011` | Regulatory, partner, or network rules change after launch. | Controls become outdated. | Change monitoring and periodic reassessment. | Legal / Compliance / Payments | Open |
| `RISK-DOC04-012` | Vendor control failures affect PayPlus compliance obligations. | Operational, privacy, security, or settlement failure. | Vendor oversight and contractual obligations tracking. | Compliance / Legal / Security | Open |

---

## 26. Downstream Document Impact

`DOC-04` should guide downstream documents as follows:

| Downstream Document | Impact |
|---|---|
| `DOC-05` | Product requirements should include compliance-critical requirements and acceptance criteria from the control framework. |
| `DOC-06` | Onboarding requirements should incorporate verification, consent, category, and screening controls. |
| `DOC-07` | Content and disclosure requirements should map to consumer protection and fee disclosure controls. |
| `DOC-08` | Notification and receipt rules should support evidence, timing, failure, and dispute disclosure controls. |
| `DOC-09` | Payment and settlement requirements should support authorization, capture, consent, fee, risk, and recordkeeping controls. |
| `DOC-10` | Payout and reconciliation requirements should support settlement, exception, reserve, and ledger controls. |
| `DOC-11` | Refund, cancellation, and chargeback requirements should support dispute evidence, reversals, and liability controls. |
| `DOC-13` | Admin and risk console requirements should support review queues, audit logs, access controls, and escalation workflows. |
| `DOC-14` | AML, fraud, sanctions, velocity, and anti-cashout rules should implement control requirements. |
| `DOC-15` | Support and complaints SOPs should support complaint, dispute, escalation, and evidence controls. |
| `DOC-16` | Security, privacy, PCI, access, and data retention requirements should implement relevant control domains. |
| `DOC-17` | Infrastructure and observability requirements should support uptime, monitoring, incident detection, and resilience controls. |
| `DOC-18` | Data model and reporting should capture fields required for evidence, audit, reconciliation, compliance reporting, and monitoring. |
| `DOC-20` | Launch readiness checklist should include all applicable compliance gates and evidence items. |
| `DOC-21` | Runbooks should operationalize incident, exception, escalation, vendor, and monitoring controls. |

---

## 27. Open Questions

| Question ID | Question | Owner | Priority | Status |
|---|---|---|---|---|
| `OQ-DOC04-001` | What exact regulatory obligations apply to the MVP jurisdiction and funds flow? | Legal / Compliance | Critical | Open |
| `OQ-DOC04-002` | What partner obligations must be mapped into controls? | Payments / Legal | Critical | Open |
| `OQ-DOC04-003` | What external certifications or attestations are required before launch versus post-launch? | Compliance / Security | Critical | Open |
| `OQ-DOC04-004` | What PCI DSS scope applies based on the final card data architecture? | Security | Critical | Open |
| `OQ-DOC04-005` | What AML, sanctions, and transaction monitoring controls are required for MVP? | Compliance / Risk | Critical | Open |
| `OQ-DOC04-006` | What fraud tooling and manual review capabilities are available at launch? | Risk / Engineering | High | Open |
| `OQ-DOC04-007` | What disclosures are legally required at checkout, receipt, and support surfaces? | Legal / Product | Critical | Open |
| `OQ-DOC04-008` | What evidence repository will be used and who can access it? | Compliance / Security | High | Open |
| `OQ-DOC04-009` | What daily reconciliation reports and exception processes are required? | Finance / Payments | High | Open |
| `OQ-DOC04-010` | What control testing must be completed before launch? | Compliance / QA | High | Open |
| `OQ-DOC04-011` | Who has authority to accept unresolved risks before launch? | Project Owner / Compliance | Critical | Open |
| `OQ-DOC04-012` | What launch controls are blockers versus post-launch remediation items? | Compliance / Project Owner | Critical | Open |
| `OQ-DOC04-013` | What ongoing monitoring metrics must be reviewed after launch? | Compliance / Risk / Payments | Medium | Open |
| `OQ-DOC04-014` | What vendor and partner reassessment cadence is required? | Compliance / Legal / Security | Medium | Open |
| `OQ-DOC04-015` | What training must be completed before launch by each function? | Compliance / People Ops | Medium | Open |

---

## 28. Acceptance Criteria

`DOC-04` is acceptable when it clearly defines:

- Purpose and scope of the compliance certification roadmap.
- Compliance control framework structure.
- Control domains and ownership.
- Compliance roadmap phases.
- Starter control matrix.
- Certification and attestation planning.
- Launch certification package requirements.
- Launch readiness gates.
- Evidence repository requirements.
- Control ownership model.
- Control testing approach.
- Exception and remediation management.
- Regulatory and partner change management.
- Vendor and partner oversight.
- Training and awareness expectations.
- Monitoring and reporting expectations.
- Governance forums.
- Relationship to launch readiness.
- Assumptions.
- Constraints.
- Dependencies.
- Risks.
- Downstream document impact.
- Open questions.

This document should remain a roadmap and control framework, not a replacement for legal advice, compliance policies, certification audits, security procedures, or product requirements.

---

## 29. Version History

| Version | Date | Author | Change Summary |
|---|---|---|---|
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of `DOC-04` Compliance Certification Roadmap & Control Framework. |
| `0.2.0` | `2026-05-26` | Product Documentation Team | Expanded into compliance roadmap and control framework with control domains, starter matrix, launch gates, evidence requirements, testing, remediation, governance, assumptions, constraints, dependencies, risks, downstream impact, and acceptance criteria. |

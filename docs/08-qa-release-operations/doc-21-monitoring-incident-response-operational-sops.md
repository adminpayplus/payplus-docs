---
document_id: DOC-21
title: Monitoring, Incident Response & Operational SOPs
version: 0.2.0
status: Founder Working Baseline
owner: Operations / Support
reviewers:
  - Operations Lead
  - Product Lead
  - QA Lead
  - Risk / Compliance Lead
  - Privacy Lead
  - Security Lead
approvers:
  - Project Owner
  - Operations Lead
last_updated: 2026-08-14
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation, Chargeback & Case
  - DOC-12 Bill Category, Document AI, OCR & Payee Verification
  - DOC-14 AML, Anti-Cashout, Fraud & Dynamic Risk Control
  - DOC-15 Privacy, Data Protection, Record & Retention
  - DOC-16 Technical Architecture Specification
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization, Authentication & Admin Control Specification
  - DOC-20 Testing, UAT & Go-Live Checklist
  - DOC-22 Admin Management & Operations Workflow
---

# DOC-21 - Monitoring, Incident Response & Operational SOPs

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-21` |
| **Title** | Monitoring, Incident Response & Operational SOPs |
| **Version** | `0.2.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Operations / Support |
| **Reviewers** | Operations Lead<br>Product Lead<br>QA Lead<br>Risk / Compliance Lead<br>Privacy Lead<br>Security Lead |
| **Approvers** | Project Owner<br>Operations Lead |
| **Last Updated** | `2026-08-14` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation, Chargeback & Case<br>DOC-12 Bill Category, Document AI, OCR & Payee Verification<br>DOC-14 AML, Anti-Cashout, Fraud & Dynamic Risk Control<br>DOC-15 Privacy, Data Protection, Record & Retention<br>DOC-16 Technical Architecture Specification<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization, Authentication & Admin Control Specification<br>DOC-20 Testing, UAT & Go-Live Checklist<br>DOC-22 Admin Management & Operations Workflow |

---

## 1. Purpose and scope

DOC-21 defines the human-readable operating baseline for observing concerns, receiving incident or support reports, routing them to the correct owner, recording permitted operational action, and closing with evidence. It covers the accepted Payer-only product and control baseline without inventing monitoring architecture, alert values, incident severity, staffing, service levels, provider runbooks, security mechanisms, dashboards, queues, or implementation workflows.

Operations may observe and route a concern; it does not become the owner of product truth, Payment facts, Evidence decisions, payout or case policy, privacy/retention policy, security controls, notification policy, or Admin permissions.

## 2. Ownership and non-erasure boundaries

DOC-21 owns monitoring/support/incident intake, owner routing, operational coordination, escalation evidence, and closure evidence. DOC-16 owns architecture, trust-boundary, reliability, recovery, reconciliation, observability, and technical evidence obligations; DOC-09 owns Payment and Payment Instruction meaning; DOC-10 owns Payout/reconciliation; DOC-11 owns refund/cancellation/dispute/chargeback/case; DOC-12 owns Evidence; DOC-14 owns risk; DOC-15 owns privacy/access/masking and indefinite retention; DOC-08 owns notification policy; DOC-18 owns data/event/audit/lineage representation; DOC-19 remains the future security-detail owner; DOC-22 performs only expressly owner-permitted operations.

Every PayPlus record is retained indefinitely. Monitoring, incident handling, Archive, account closure, Save outcome, Payment/Checkout terminal treatment, case closure, or notification delivery must not erase, purge, destroy, anonymise, or de-identify the underlying record merely because time or purpose has passed. Source Archive is a non-erasing visibility projection.

## 3. Observable concern families

| Concern family | Required operational observation and routing | Primary owner handoff |
| --- | --- | --- |
| Architecture boundary and durable handoff | Preserve the owning local authoritative fact when a provider observation, cross-boundary handoff, projection, or operational signal is late, duplicated, missing, contradictory, or unavailable; route retry, recovery, reconciliation, support, and incident evidence without treating the signal as authority. Escalate any possible raw PAN or card-verification exposure under the provider-controlled boundary without copying the value into operational records. | DOC-16 / DOC-17 / DOC-18 / DOC-19 |
| Source, Setup and projections | Distinguish temporary capture, authoritative Bill/Rent source, deliberate Setup, immediate pay-now, Payment Result, Save outcome, Active/history-only/established-but-unprojected, Activity/Receipt, and source Archive. | DOC-05 / DOC-06C / DOC-09 / DOC-15 |
| Checkout and Payment Instruction | Distinguish incomplete or partially funded Checkout Close/Expiry/continuation from deliberate Payment Instruction cancellation/expiry; do not treat either as source Archive. | DOC-09 / DOC-06B |
| Payment topology | Preserve source -> Payable Basis -> obligations -> one-basis Checkout -> allocations/Funding Legs -> immutable Payment -> Applications. A controlled late-confirmation Payment may temporarily have zero Applications, and any confirmed Payment with insufficient valid Applications is likewise not ordinary Payout-ready; do not fabricate an Application, negative or fictional coverage, or payout value. Any adjustment impact is bounded by valid Application coverage, with excess adjustment routed as an owner-controlled fact outside coverage arithmetic and downstream treatment remaining within the DOC-09/DOC-10/DOC-11 boundary. | DOC-09 / DOC-10 / DOC-11 |
| Payout and reconciliation | Route destination, settlement, readiness, hold, reconciliation, batch, and non-erasure concerns with the applicable Payment/Application facts. | DOC-10 / DOC-09 |
| Refund, adjustment, dispute and case | Preserve immutable Payment/Application facts, ensure adjustment impact cannot create fictional coverage, and route case truth, Archive blockers, reconciliation treatment, and owner outcomes without inventing a return/refund mechanism. | DOC-11 / DOC-10 / DOC-09 |
| Evidence and readiness | Separate Evidence extraction/verification and intended-Payee facts from source truth and payment readiness; label-only review cannot bypass concrete gates. | DOC-12 / DOC-09 / DOC-14 |
| Risk and prohibited product boundary | Route AML, anti-cashout, fraud, sanctions, suspicious activity, wallet, remittance, cashout, marketplace, and unrestricted P2P concerns to the risk and product owners. | DOC-14 / DOC-03 / DOC-04 |
| Privacy, access and retention | Route masking, approved-purpose access, correction/export/privacy requests, legal hold, and access concerns while preserving indefinite retention and non-erasure. | DOC-15 / DOC-18 / DOC-19 |
| Notification delivery | Route eligibility, recipient, channel, template, preference, fallback, retry, delivery evidence, and support concerns to DOC-08; operational execution remains owner-permitted. | DOC-08 / DOC-07 / DOC-22 |
| Archive and retained history | Treat Archive as source visibility only; preserve retained source, Evidence, Payment, Payout, case, notification, audit, and revision facts. | DOC-05 / DOC-06C / DOC-15 |
| Retired runtime | Treat Request, Linking, Receive, Receiving Info, Consumer-Payee, Payee-user, reader, adapter, fallback, and deep-link observations as negative regression or historical-lineage concerns, not active workflows. | DOC-06A / DOC-06B / DOC-06C |

## 4. Intake, triage and escalation

An operational report should capture the observed concern, affected product/domain context, source or record reference where permitted, user-visible effect, time of observation, evidence available, immediate safe handling, and proposed owner handoff. The report must preserve authoritative facts and must not overwrite or infer a new status, event, permission, schema, retention period, legal conclusion, or product rule.

Triage routes the report to the primary formal owner and identifies dependent owners. A concern may be held for owner review, support resolution, risk/privacy handling, or later lifecycle work. If the report indicates a possible safety, privacy, financial-integrity, or prohibited-product issue, operations records the concern and escalates to the applicable owner without inventing a local workaround.

## 5. Incident, support and closure evidence

Support and incident handling should show intake, owner acknowledgement, facts checked, permitted action taken, unresolved dependency, user-safe communication handoff, and closure rationale. Closure does not erase the underlying record and does not convert an operational observation into a product status or domain event. DOC-20 consumes operational evidence for UAT and go-live decisions; DOC-22 executes only workflows expressly permitted by the relevant owner.

The following situations require explicit owner routing rather than silent closure:

- a confirmed Payment with zero or insufficient Applications under the DOC-09 exception or applicable owner-controlled boundary;
- incomplete or partially funded Checkout, Payment Instruction cancellation/expiry, or failed authorization;
- payout, reconciliation, adjustment, refund, dispute, chargeback, or case hold;
- Evidence/readiness, risk, privacy/access, retention, legal-hold, or notification-delivery concern;
- Archive or account-closure concern where non-erasure must be preserved;
- any observation of retired Request/Linking/Receive/Receiving Info runtime or prohibited wallet/P2P/remittance/cashout behavior.

## 6. Operational readiness handoff

Before a scope is treated as operationally ready, the owning teams should have identified the observable concern families, owner routing, permitted support and escalation outcomes, evidence responsibilities, known dependencies, and non-erasure boundaries. DOC-20 records test/UAT/go-live evidence; DOC-21 records monitoring/support/incident evidence against DOC-16 architecture obligations; the two documents do not replace DOC-18 representation or DOC-19 security specifications.

## 7. Open questions and deferred detail

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-21-001 | Which human-readable operational evidence form should be used for each concern family? | Operations / QA | Open |
| OQ-21-002 | Which monitoring signals are supported by the current DOC-18 representation baseline, and which security-dependent signals remain blocked until DOC-19 is substantively specified? | Operations / DOC-18 / DOC-19 | Open |
| OQ-21-003 | Which support procedures and owner handoff details are required for each later release scope? | Operations / Product / Support | Open |
| OQ-21-004 | Which incident and release evidence relationship is required at each later lifecycle gate? | Operations / QA / Product | Open |

These questions do not authorize a severity taxonomy, numerical threshold, SLA, staffing model, dashboard, queue, provider runbook, security control, deletion exception, or implementation mechanism.

## 8. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.2.0 | 2026-08-14 | Aligned operational evidence and owner routing with the Stage 9-passed DOC-16 architecture, including local authoritative facts, durable cross-boundary handoffs, provider-controlled card-data escalation, current DOC-18 representation ownership, and future DOC-19 security detail. |
| 0.1.2 | 2026-08-13 | Added explicit operational routing for zero- and insufficient-Application Payout control, no-fabrication/no-bypass treatment, and owner-controlled downstream resolution without defining signals, statuses, thresholds, queues or mechanisms. |
| 0.1.0 | 2026-08-12 | Created the first substantive human-level monitoring, incident, support, escalation and operational-handoff baseline for the accepted Wave 1-4 product and control requirements. |

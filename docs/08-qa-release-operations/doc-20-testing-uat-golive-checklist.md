---
document_id: DOC-20
title: Testing, UAT & Go-Live Checklist
version: 1.1.2
status: Founder Working Baseline
owner: QA / Product / Operations
reviewers:
  - Product Lead
  - QA Lead
  - Engineering Lead
  - Compliance Lead
  - Security Lead
  - Operations Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-08-27
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation, Chargeback & Case
  - DOC-12 Bill Category, Document AI, OCR & Payee Verification
  - DOC-14 AML, Anti-Cashout, Fraud & Dynamic Risk Control
  - DOC-15 Privacy, Data Protection, Record & Retention
  - DOC-16 Technical Architecture Specification
  - DOC-17 API & Third-party Integration Specification
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization, Authentication & Admin Control Specification
  - DOC-20 Testing, UAT & Go-Live Checklist
  - DOC-21 Monitoring, Incident Response & Operational SOPs
  - DOC-22 Admin Management & Operations Workflow
  - DOC-99 ISMS Policy Library
---

# DOC-20 - Testing, UAT & Go-Live Checklist

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-20` |
| **Title** | Testing, UAT & Go-Live Checklist |
| **Version** | `1.1.2` |
| **Status** | Founder Working Baseline |
| **Owner** | QA / Product / Operations |
| **Reviewers** | Product Lead<br>QA Lead<br>Engineering Lead<br>Compliance Lead<br>Security Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-08-27` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation, Chargeback & Case<br>DOC-12 Bill Category, Document AI, OCR & Payee Verification<br>DOC-14 AML, Anti-Cashout, Fraud & Dynamic Risk Control<br>DOC-15 Privacy, Data Protection, Record & Retention<br>DOC-16 Technical Architecture Specification<br>DOC-17 API & Third-party Integration Specification<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization, Authentication & Admin Control Specification<br>DOC-20 Testing, UAT & Go-Live Checklist<br>DOC-21 Monitoring, Incident Response & Operational SOPs<br>DOC-22 Admin Management & Operations Workflow<br>DOC-99 ISMS Policy Library |

---

## 1. Purpose and scope

DOC-20 defines the human-readable governance for requirement acceptance, test evidence, User Acceptance Testing (UAT), and go-live readiness. It converts accepted product and control requirements into observable evidence and decision gates without becoming the owner of product truth, payment architecture, data representation, security mechanisms, operations policy, or implementation design.

This document applies to the accepted Payer-only Consumer User baseline, the economic Payee model, the twelve controlled Bill Categories and separate Rent, the source-to-Payment topology, Evidence and readiness boundaries, Archive non-erasure, notification, risk, privacy, Admin execution, and the negative product boundaries described by the formal owners.

## 2. Ownership and evidence boundaries

DOC-20 owns the acceptance evidence contract and the human-level readiness decision record. The relevant product or control owner remains authoritative for the requirement being tested. DOC-06D maps UX requirements to acceptance criteria; DOC-16 owns architecture requirements and evidence obligations; DOC-18 owns the reviewed business-recording, explainability, history, lineage, audit-meaning and owner-handoff contract; DOC-21 owns monitoring, incident, support, and operational escalation; and the reviewed DOC-19 Draft owns mechanism-neutral security-control requirements and verification handoffs. Exact DOC-18 technical representation, security mechanisms, tests, implementation and operating evidence remain unresolved.

An acceptance item should identify its source requirement, expected human-observable outcome, applicable preconditions, observed result, evidence owner, exception or limitation, and downstream handoff. The representation must not invent a schema, event, API, status taxonomy, automation architecture, provider behavior, alert value, SLA, deployment mechanism, security control, legal conclusion, or final Copy.

## 3. Test and acceptance evidence families

| Family | Purpose | Minimum human-level evidence |
| --- | --- | --- |
| Positive | Demonstrate an accepted path succeeds under applicable owner gates. | Source requirement, scenario, expected outcome, observed outcome, owner and evidence reference. |
| Negative | Demonstrate prohibited, retired, unauthorized, or unsafe paths do not proceed. | Boundary under test, attempted path, blocked outcome, safe resolution and owner confirmation. |
| Exception | Demonstrate controlled failure, late confirmation, incomplete work, owner hold, or recovery behavior. | Trigger context, preserved authoritative facts, permitted resolution/deferral and escalation handoff. |
| Regression | Demonstrate earlier accepted decisions and corrections remain true after change. | Prior requirement/correction reference, comparison outcome and evidence owner. |

Testing may be manual, assisted, automated, or otherwise evidenced by a later technical owner. DOC-20 does not choose the mechanism. Evidence must be sufficient for the named gate and traceable to the source owner.

## 4. Wave 1-4 acceptance coverage

| Requirement family | Normative owner | DOC-20 evidence expectation | Handoff / dependency |
| --- | --- | --- | --- |
| Technical architecture and cross-boundary integrity | DOC-16 | Architecture review and later implementation evidence must cover risk-isolated modular boundaries, provider-controlled card-data handling, local authoritative transaction tests, durable handoff retry/idempotency/correlation/failure/recovery/reconciliation, non-authoritative projections, least privilege, and Security & Compliance by Design without claiming certification from documentation alone. | DOC-17, DOC-18, DOC-19, DOC-21, DOC-22 |
| Provider-neutral External Interaction Contract | DOC-17 `PNIC-01` to `PNIC-22`, `FSC-01` to `FSC-19`, and `D17-AC-01` to `D17-AC-08` | Later evidence must trace External Observation non-authority, owner evaluation and handoff, uncertainty and duplicate-effect controls, complete Functional-Surface Coverage, Bill/Rent owner consumption, candidate/generic separation, replacement/exit evidence, and every explicit non-decision without treating the Draft as provider selection, API/backend/adapter design, representation, security mechanism, implementation, acceptance, enablement, assurance, or readiness. | DOC-05, DOC-06C, DOC-07, DOC-08, DOC-09 to DOC-16, DOC-18, DOC-19, DOC-21, and DOC-22 as applicable |
| Business recording, explainability, history, lineage, audit meaning, and owner handoffs | DOC-18 `REQ-18-BR-001` to `REQ-18-BR-013` and `AC-18-001` to `AC-18-013` | Later evidence must trace the complete business-recording contract: source fact/processing/assessment/effective-fact/consequence separation; complete Bill/Rent material facts; same-Bill Category amendment and prior history; four Declaration contexts; Evidence/financial/case/risk separation; time, supersession and historical action basis; External Observation non-authority; exact DOC-15/19/21/22 history-retrieval split; and technical non-approval. This row records a future evidence obligation only and makes no acceptance, implementation, enablement, readiness, or launch claim. | Applicable domain owners, DOC-15, DOC-16, DOC-17, DOC-19, DOC-21, and DOC-22 |
| Security-control contract | DOC-19 `CTRL-19-001` to `CTRL-19-007` and `SEC19-AC-001` to `SEC19-AC-010` | Later evidence must trace each applicable source owner, invariant, prohibited behavior, non-sensitive verification obligation, negative path, handoff, and unresolved enablement gate without treating the Draft as implementation, operating effectiveness, certification, compliance, provider approval, production readiness, or launch readiness. | DOC-06B, DOC-09, DOC-10, DOC-14, DOC-15, DOC-16, DOC-17, DOC-18, DOC-21, DOC-22, DOC-99 |
| Payer-only actor, economic Payee, Categories and separate Rent | DOC-01 / DOC-05 / DOC-06C | Positive and negative acceptance of actor, exact inventory, Category-bound self-provision, Directory discovery and separate Rent. | DOC-06D, DOC-12, DOC-14 |
| Evidence and readiness | DOC-12 | Evidence supports verification; Evidence is not source, Payable Basis, Obligation, Checkout or Payment; label-only review cannot bypass concrete gates. | DOC-09, DOC-14, DOC-15 |
| Tiered Bill presentation and return | DOC-05 / DOC-06B / DOC-06C / DOC-07 / DOC-09 / DOC-10 | Evidence must show that Tier 3 owner-recorded approval keeps the current Bill context and requires deliberate `Pay` plus current resolver revalidation, with no automatic navigation, notification, authorization, Provider Submission, or generic status. It must show Tier 2 confirmed Payment, current Evidence, and Payout-held/release truth separately; no automatic Refund or ordinary Evidence Activity; Add-Bill Declaration confirmation distinct from Save; and the separate Rent accepted-Evidence gate. | DOC-06D, DOC-08, DOC-11, DOC-12, DOC-14; later implementation evidence remains owner-defined |
| Source identity and projections | DOC-05 / DOC-06C | Setup, immediate pay-now, Payment Result then optional same-ID Save, Saved/current, Saved/Archived, history-only, established-but-unprojected and Activity/History/Receipt independence. | DOC-09, DOC-15, DOC-21 |
| Payment topology and late confirmation | DOC-09 | Source -> Payable Basis -> applicable Payment Obligations -> one-basis Checkout -> allocations/Funding Legs -> immutable Payment -> Applications; controlled zero- or insufficient-Application cases are explicitly tested as not ordinary Payout-ready, with no Application, negative coverage, fictional coverage or payout value fabricated, and any downstream treatment remaining owner-controlled. Adjustment impact is bounded by valid Payment Application coverage; excess adjustment remains an owner-controlled fact outside coverage arithmetic. | DOC-10, DOC-11, DOC-21 |
| Checkout and Payment Instruction | DOC-09 / DOC-06B | Incomplete/partially funded Checkout follows Close/Expiry/continuation; it is not Payment Instruction or source Archive. Deliberate Payment Instruction cancellation/expiry remains distinct. | DOC-06D, DOC-21 |
| Payout and reconciliation | DOC-10 | Confirmed Payment, Application lineage, destination snapshot, readiness, holds, reconciliation and non-erasure are preserved. | DOC-09, DOC-11, DOC-15, DOC-21 |
| Refund, cancellation, dispute, chargeback and case | DOC-11 | Immutable Payment/Application facts, case ownership, Archive blockers and controlled owner outcomes are evidenced without inventing a mechanism. | DOC-10, DOC-21 |
| Archive and retention | DOC-05 / DOC-06C / DOC-15 | Archive is visibility-only/non-erasing; indefinite retention remains the accepted direction subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries. | DOC-15, DOC-18, DOC-21 |
| Notification | DOC-08 | Eligibility, recipient, channel, template, preference, fallback/retry, delivery evidence and DOC-22 execution handoff are evidenced against DOC-08 policy. | DOC-07, DOC-21, DOC-22 |
| Risk and prohibited product boundary | DOC-14 / DOC-03 / DOC-04 | Anti-cashout, fraud, sanctions, risk holds and prohibited wallet/P2P/remittance/marketplace paths are tested at requirement level. | DOC-09, DOC-15, DOC-21 |
| Privacy and access | DOC-15 | Masking, approved-purpose access, correction/export/privacy-request handling and lawful-scope-qualified indefinite retention are evidenced; no finite duration is selected here. | DOC-18, DOC-19, DOC-21 |
| Admin execution-only | DOC-22 | Owner-permitted execution is evidenced without granting Admin authority to define product, payment, risk, privacy, notification, security or retention policy. | All affected owners, DOC-21 |
| Retired runtime | DOC-06A / DOC-06B / DOC-06C | Negative regression proves no active Request, Linking, Receive, Receiving Info, Consumer-Payee, Payee-user runtime, reader, adapter, fallback or deep link. | DOC-06D, DOC-21 |
| Accessibility and content | DOC-06D / DOC-07 | Human-level accessibility, disclosure and outcome/message mapping evidence; exact Copy and implementation evidence remain with their owners. | DOC-06D, DOC-07 |

## 5. UAT readiness and completion

UAT is ready when the applicable source requirements, acceptance criteria, owners, expected outcomes, known dependencies, evidence responsibilities, and permitted exceptions are identified. UAT completion requires recorded evidence for the in-scope positive, negative, exception, and regression families, disposition of failed or incomplete items by the owning authority, and an explicit handoff for evidence that remains deferred to a later owner or implementation stage.

UAT must not be treated as legal approval, security certification, production validation, or proof of a technical mechanism not yet owned and specified. An unresolved owner decision or blocked dependency is recorded as such rather than hidden by a pass label.

## 6. Go-live readiness evidence

The go-live decision should identify the accepted scope, evidence reviewed, open exceptions, owner approvals required by DOC-00, operational/support handoffs, and any explicit exclusion. It must show that the negative product boundaries, DOC-16 architecture and card-data boundaries, local-authority/durable-handoff evidence, retention rule, payment/application exception, Archive blockers, notification ownership, privacy access, and Admin execution boundary remain intact.

DOC-20 does not define deployment, rollback, monitoring thresholds, staffing, incident severity, provider operation, security controls, or implementation release mechanics. Those details require their formal owner and later lifecycle authorization.

## 7. Open questions and deferred evidence

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-20-001 | Which human-readable evidence template and field vocabulary should be adopted for each acceptance family? | QA / Product | Open |
| OQ-20-002 | Which implementation-level test mapping and evidence storage approach will be approved after technical owners are ready? | QA / Engineering / DOC-18 | Open |
| OQ-20-003 | Which release-readiness evidence package is required for each later lifecycle gate? | QA / Product / Operations | Open |
| OQ-20-004 | Which UAT participants and owner sign-offs are applicable to each future release scope? | Product / Operations | Open |

These questions do not reopen settled product meaning and do not authorize implementation detail.

## 8. Version History
| Version | Date | Summary |
| --- | --- | --- |
| 1.1.2 | 2026-08-27 | Added traceability for all 13 DOC-18 business-recording requirements and 13 Acceptance Criteria as later evidence obligations without making an acceptance, implementation, enablement, readiness, or launch claim. |
| 1.1.1 | 2026-08-25 | Added reference-only acceptance coverage for the reviewed DOC-17 provider-neutral External Interaction Contract, Functional-Surface Coverage, owner handoffs, and explicit non-decisions without defining tests, providers, APIs, mechanisms, implementation, acceptance, enablement, assurance, or readiness. |
| 1.1.0 | 2026-08-22 | Added human-level evidence expectations for the approved Tier 3 return, Tier 2 financial-truth separation, Declaration/Save boundary, and Rent negative control without selecting implementation tests, mechanisms, statuses, or readiness claims. |
| 1.0.1 | 2026-08-21 | Replaced the future DOC-19 marker and mapped the reviewed security Control Cards and acceptance handoffs without inventing tests, mechanisms, evidence, readiness, compliance, or certification claims. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. |
| 0.2.0 | 2026-08-14 | Aligned acceptance and go-live evidence with the Stage 9-passed DOC-16 architecture, current DOC-18 representation ownership, and DOC-21 operational evidence handoffs without defining implementation mechanisms or claiming certification. |
| 0.1.2 | 2026-08-13 | Added explicit acceptance evidence for zero- and insufficient-Application Payout control, no-fabrication/no-bypass treatment, and owner-controlled downstream resolution without defining an implementation mechanism. |
| 0.1.0 | 2026-08-12 | Created the first substantive human-level testing, UAT and go-live acceptance baseline for the accepted Wave 1-4 product and control requirements. |

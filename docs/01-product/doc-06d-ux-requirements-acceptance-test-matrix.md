---
document_id: DOC-06D
title: UX Requirements, Acceptance Criteria & Test Matrix
version: 0.1.3
status: Founder Working Baseline
owner: Product / Founder
reviewers:
  - Product Lead
  - Design Lead
  - Engineering Lead
  - QA Lead
  - Compliance Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-07-06
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-20 Testing, UAT & Go-Live Checklist
---

# DOC-06D - UX Requirements, Acceptance Criteria & Test Matrix

## 1. Purpose

DOC-06D governs UX requirement IDs, acceptance criteria, route/action/state/event/test mapping, and test-readiness tracking for the DOC-06 family.

## 2. Scope Boundary

DOC-06D owns the mapping between human-readable UX requirements and testable acceptance criteria. It does not create product scope, technical implementation tasks, database schemas, endpoint contracts, or detailed automated tests.

DOC-06D should expand progressively as DOC-06A, DOC-06B, and DOC-06C become more stable.

## 3. Completion Markers

| Area | Status | Notes |
| --- | --- | --- |
| Non-functional UX baseline | Working baseline | Stable UXREQ IDs should be assigned progressively. |
| MVP/baseline acceptance criteria | Working baseline | Needs route/action/state/test mapping. |
| Route/action/state/event/test matrix | Skeleton | Start with settled Bills-route requirements, then expand to other routes. |
| Open-question/test-readiness mapping | Skeleton | Incomplete routes must remain visible as not test-ready. |

## 4. Mapping Standard

DOC-06D should use this relationship when expanding detailed testability:

```text
UXREQ -> ROUTE / SCREEN / COMPONENT -> ACTION -> STATE / EVENT -> TEST
```

Example pattern:

| Field | Example |
| --- | --- |
| UX Requirement | UXREQ-06C-014 |
| Requirement Text | Payer-side Bills cards must show Pay only when the record is eligible for payment. |
| Route | ROUTE-06C-BILLS-PAY |
| Component | COMP-06C-BILL-CARD |
| Action | ACT-06C-PAY-001 |
| State Dependency | STATE-06A-REQUEST-APPROVED-FOR-PAYMENT |
| Event Dependency | EVT-06C-BILL-PAY-TAPPED |
| Owning Docs | DOC-06C, DOC-09, DOC-12, DOC-14, DOC-15 |
| Test | TC-06D-014 |

## 5. Initial Test-Readiness Matrix

| Area | Source Doc | Test Readiness | Notes |
| --- | --- | --- | --- |
| Prohibited wallet/stored-value/cashout journeys | DOC-06 / DOC-06A | Ready for high-level blocked-flow criteria | Detailed tests later in DOC-20. |
| Home dashboard layout | DOC-06B | Partial | Needs exact card behavior and UI detail. |
| Pay+ action sheet | DOC-06B | Partial | Needs final visual order, disabled state, and action eligibility. |
| BILLS-PAY / BILLS-RECEIVE role separation | DOC-06C | Partial to strong | Core role distinction is testable; visual detail remains open. |
| Bills evidence sub-flow | DOC-06C / DOC-12 | Partial | UX flow is testable; verification logic depends on DOC-12/DOC-18. |
| Bills reminder route | DOC-06C / DOC-08 | Partial | Reminder list/detail behavior is testable; payment-instruction placement remains open. |
| Payment checkout handoff | DOC-06A / DOC-06C / DOC-09 | Partial | DOC-06 can test route handoff; DOC-09 owns checkout tests. |
| Payment Profile route | DOC-06B / DOC-09 / DOC-15 / DOC-19 | Partial | Route shell is testable for card/profile management, max 6-card profile/payment cap, return context, masking, and non-checkout boundary; final UI and tokenization behavior remain open. |
| Offers route | DOC-06B / DOC-13 | Not Ready | Route IA pending. |
| Me route | DOC-06B / DOC-15 / DOC-19 | Not Ready | Route IA pending. |

---

## 6. Non-Functional UX Requirements

| Area | Requirement |
| --- | --- |
| Clarity | Users must understand what they are requesting, paying, accepting, or authorizing. |
| Evidence visibility | Payer must be able to review evidence before payment authorization. |
| Evidence correction | Users must be able to review and correct autofilled evidence fields before submission where OCR/autofill is enabled. |
| Sensitive field display control | UI must apply DOC-15 role-based display, masking, approved-purpose access, and controlled detail views; broader extractable data may be stored without broad display. |
| Status transparency | Users must see clear request and linked payment status for pending, processing, completed, failed, rejected, cancelled, expired, and exception/support cases. |
| Permissioning | Users must only see data appropriate to their role. |
| Auditability | Key actions must generate audit events. |
| Error handling | Failed, blocked, or incomplete actions must show clear next steps. |
| Accessibility | MVP UX should follow basic accessibility principles. |
| Mobile readiness | Core flows should be usable on common mobile screen sizes. |
| Security | Sensitive payment, identity, evidence, and payout details must be protected. |
| Compliance readiness | UX must support evidence, authorization, review, dispute, and traceability requirements. |

## 7. MVP Acceptance Criteria

The DOC-06 user journey scope is satisfied when:

- payers can register and log in;
- payees can register and log in;
- phone verification, new-device 2FA, dormant-login reauthentication, and material-change confirmation touchpoints are represented;
- payers have a dashboard;
- payees have a dashboard;
- payees can create evidence-backed payment requests;
- payees can send payment requests to payers;
- payers can receive and review payee-created requests;
- payers can create evidence-backed payments or obligation records;
- payers can link or invite payees;
- payees can review payer-created records;
- payees can optionally accept/adopt payer-created records for linking where applicable;
- users can upload evidence;
- OCR/document AI can process evidence where enabled;
- users can review and correct autofilled evidence fields where applicable;
- evidence is linked to the request or obligation;
- evidence verification outcomes can route to payment eligibility, user clarification, or admin review;
- payer can review evidence before payment;
- payer can accept or reject a request, with rejection reason where required;
- users can raise or respond to linked query, dispute, support, or exception cases where enabled;
- payer can explicitly authorize payment;
- payer must enter payment passcode before payment authorization proceeds;
- users can manage tokenized cards and saved split-card profiles through `PAYMENT-PROFILE-ROOT` without creating wallet, stored-value, cashout, or payment authorization behavior;
- saved split-card profiles and split-card checkout must observe the MVP maximum of 6 cards;
- single-card checkout may preselect a default card while split-card checkout requires user selection of a payment profile;
- payment status can be tracked;
- payout or settlement status can be tracked where applicable;
- payer-side Bills routes do not show payee-side request actions as payment actions;
- payee-side Bills routes do not show payer-side `Pay` actions;
- payer and payee can view the same linked request/payment context subject to permissions;
- admin can review users, requests, evidence, disputes, and exceptions;
- key status changes are audit logged;
- receipts or confirmations are available for completed payments;
- failed, rejected, cancelled, expired, and exception/support cases are handled clearly;
- wallet, stored balance, cashout, self-cashout, and unsupported P2P journeys are blocked.

## 8. Local Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06D-001 | Which stable UXREQ IDs should be assigned before AI build-execution conversion? | Product / QA / Engineering | Open |
| OQ-06D-002 | Which route/action/state/event mappings are required before the first AI implementation prompt set? | Product / QA / Engineering | Open |
| OQ-06D-003 | Which incomplete routes should remain placeholder-only until detailed UI drafting is complete? | Product / Design | Open |
| OQ-06D-004 | Which acceptance criteria should remain at human-review level versus becoming implementation-level tests in DOC-20? | Product / QA | Open |

## 9. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.1.3 | 2026-07-06 | Added Payment Profile route test-readiness and MVP acceptance coverage for card/profile management, max 6-card cap, default single-card behavior, split-profile selection, default confirmation behavior, and non-checkout boundary. |
| 0.1.2 | 2026-07-02 | Aligned UX acceptance criteria with DOC-06B request-route model by separating accept/reject request actions from support, query, dispute, and exception cases. |
| 0.1.1 | 2026-06-25 | Removed temporary source-section heading wording and corrected the UX mapping code fence for official DOC-06D baseline use. |
| 0.1.0 | 2026-06-25 | Created as DOC-06D child document for non-functional UX requirements, acceptance criteria, and initial test-readiness mapping. |

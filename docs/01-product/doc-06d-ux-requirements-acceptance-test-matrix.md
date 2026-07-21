---
document_id: DOC-06D
title: UX Requirements, Acceptance Criteria & Test Matrix
version: 0.1.9
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
last_updated: 2026-07-21
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-08 Notification, Receipt & Communication Rules
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
| Payment Profile route | DOC-06B / DOC-09 / DOC-15 / DOC-19 | Partial to strong | Two-tab `Cards` / `Profiles` baseline, card/profile management, max 6-card profile/payment cap, return context, masking, and non-checkout boundary are testable; final styling and tokenization behavior remain open. |
| Receipts & Statements route | DOC-06B / DOC-08 / DOC-15 | Partial to strong | `RECEIPTS-ROOT` views, search, list, `Paid` / `Received` role indicator, empty-state behavior, direct download, shared PDF preview, notification entry, and return behavior are testable; final PDF design and re-issue operations remain open. |
| Offers and Rewards routes | DOC-06B / DOC-09 / DOC-13 / DOC-15 | Strong human-readable baseline | Section limits, child collection behavior, source/action/destination/return transitions, multi-collection membership, duplicate suppression, ordering, full-screen detail, checkout handoff, and issued-reward management are testable. External vouchers and miles are launch-supported; final visual design, label taxonomy, personalization, equal-priority tie-break, partner selection, fulfilment method, and operational readiness remain open. |
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
- users can search, view, and directly download available receipts and statements through `RECEIPTS-ROOT`, with `RECEIPT-DETAIL` and `STATEMENT-DETAIL` providing a minimal in-app PDF preview;
- users can discover promotions through `OFFERS-ROOT`, review material conditions in `OFFER-DETAIL`, and manage issued rewards separately through `REWARDS-ROOT` and `REWARD-DETAIL`;
- `REWARDS-ROOT` uses route-local Active and History views, route-local search, instrument filters that are not statuses, defined ordering, and loading, empty, no-match, error, and permitted cached read-only states;
- reward cards expose approved summary fields and open `REWARD-DETAIL` without revealing redemption credentials, internal references, internal risk reasons, referral-party information, or partner payloads;
- `REWARD-DETAIL` shows the full benefit, eligibility, restrictions, usage method, expiry, and complete terms and conditions, and exposes only a meaningful contextual action;
- checkout-applied rewards are selected in DOC-09 checkout after card/profile selection; viewing reward detail returns to the same checkout without selection, reservation, or consumption;
- credential reveal, copy, or external-partner open does not mark a reward Used; authoritative outcomes, duplicate retries, unknown results, and terminal display follow DOC-13 and the status-display reference matrix;
- issued reward records preserve instrument type, earning source, participant role where applicable, program, campaign/offer/entitlement source, and fulfilment method without presenting My Rewards as a wallet or stored balance;
- users can open complete Card, Pay+, and Partner offer collections through `OFFERS-CARD-LIST`, `OFFERS-PAYPLUS-LIST`, and `OFFERS-PARTNER-LIST` without treating category labels as routes;
- one Offer ID may belong to multiple discovery collections, appears once within each child list, and is suppressed from unintended repeated display on `OFFERS-ROOT` while remaining available in every relevant child list;
- Offers child lists apply mandatory display gates and stable collection-specific admin priority without random reshuffling or MVP user sorting;
- one payment card may qualify for multiple distinct offers without those offers being treated as duplicates;
- checkout automatically applies the single eligible payment-method-sensitive Card Offer with the highest user value per selected payment card or split-payment funding leg and displays the applied result;
- payment-card/profile selection, automatic Card Offer result, separate eligible coupon/voucher/discount selection, recalculated quote, and payer review occur in the same checkout screen or step before authorization;
- changing a payment card, profile, funding allocation, amount, or other material eligibility input re-evaluates the promotion result and blocks authorization until the revised quote is reviewed;
- navigation tests cover source, user action, destination, and return behavior without requiring a permanent ID for every entry action;
- successful redemption changes the offer action to `Redeemed` and exposes `View My Reward`, while failed or ineligible redemption creates no reward instrument;
- referral participation remains separate from Offers through `REFERRAL-ROOT`, `REFERRAL-REWARDS-LIST`, `REFERRAL-ENTITLEMENT-DETAIL`, and `REFERRAL-REWARD-CLAIM`, and `BILLS-PAY` remains an external handoff rather than an Offers sub-route;
- opening a referral share sheet, copying a link, or showing a QR creates no known recipient, invitation card, or invitation status;
- referral deeplink/QR registration displays a valid code prefilled and not editable, while ordinary registration permits optional manual entry, retry, or clearing an invalid code;
- completed valid registration creates normal-user-immutable referral attribution without creating payer/payee linking, a Request, payment authority, or shared financial visibility;
- referral qualification displays `In Progress`, `Qualified`, `Not Qualified`, or `Under Review` without exposing private financial, evidence, KYC, card, payee, or internal risk data;
- corresponding referrer and referee entitlements appear in `REFERRAL-REWARDS-LIST`, preserve beneficiary role, and use `Available to Claim` and `History` route-local tabs without creating additional routes;
- referral reward cards expose only approved reward/campaign/status/date fields, open `REFERRAL-ENTITLEMENT-DETAIL`, and do not expose referral-party identity or private qualification data;
- claim is initiated from entitlement detail, prevents duplicate submission, and creates at most one canonical issued reward; success offers `View Reward` to `REWARD-DETAIL` and `Done` to the Referral Rewards `History` tab with the issued card visible;
- campaign end, claim deadline, and reward usage expiry remain separate; valid earned entitlements survive campaign end according to DOC-13;
- normal Referral reward presentation uses `Available to Claim`, `Issued`, `Expired`, and `Reversed`; an administrator-held claimed item remains inactive in `History` with exceptional `Under Review` presentation until resolved;
- direct checkout discounts do not appear as issued rewards unless DOC-13 creates a separate entitlement or instrument;
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
| 0.1.9 | 2026-07-21 | Added Rewards acceptance coverage for Active/History views, search/filter/order and route states, safe reward cards, complete detail/T&C, checkout selection and return, credential-versus-use behavior, canonical statuses, and separate reward-data dimensions. |
| 0.1.8 | 2026-07-21 | Added Referral child-screen acceptance coverage for role-sensitive rewards, two tabs, card/privacy boundaries, detail-first claim, idempotent issuance, lifecycle-date separation, and exceptional admin-held History presentation. |
| 0.1.7 | 2026-07-21 | Added Referral route, sharing, registration-attribution, qualification-display, privacy-boundary, role-sensitive entitlement, claim, and canonical reward-handoff acceptance coverage. |
| 0.1.6 | 2026-07-20 | Added Offers child-list, multi-collection, duplicate-suppression, stable-ordering, distinct-offer, same-screen checkout, highest-user-value Card Offer, separate coupon/voucher, and promotion-recalculation acceptance coverage; removed stale entry-point-ID wording. |
| 0.1.5 | 2026-07-17 | Added Offers and Rewards test-readiness for stable product destinations, source/action/destination/return transitions, section limits, child collection screens, full-screen detail behavior, redemption state, issued-reward management, partial Referral routing, and external Bills/checkout handoffs. |
| 0.1.4 | 2026-07-14 | Added test-readiness and MVP acceptance coverage for `RECEIPTS-ROOT` search, role-aware list behavior, direct document download, and shared PDF preview behavior through `RECEIPT-DETAIL` and `STATEMENT-DETAIL`. |
| 0.1.3 | 2026-07-06 | Added Payment Profile route test-readiness and MVP acceptance coverage for two-tab card/profile management, max 6-card cap, default single-card behavior, split-profile selection, default confirmation behavior, return context, and non-checkout boundary. |
| 0.1.2 | 2026-07-02 | Aligned UX acceptance criteria with DOC-06B request-route model by separating accept/reject request actions from support, query, dispute, and exception cases. |
| 0.1.1 | 2026-06-25 | Removed temporary source-section heading wording and corrected the UX mapping code fence for official DOC-06D baseline use. |
| 0.1.0 | 2026-06-25 | Created as DOC-06D child document for non-functional UX requirements, acceptance criteria, and initial test-readiness mapping. |

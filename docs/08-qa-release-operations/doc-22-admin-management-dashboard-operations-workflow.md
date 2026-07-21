# DOC-22 ??Admin Management Dashboard and Operations Workflow

## 1. Purpose

## 2. Scope

## 3. Out of Scope

## 4. Admin User Roles

## 5. Admin Permission Model Summary

## 6. Admin Dashboard Overview

## 7. Operations Queues

### 7.1 Account Review Queue
### 7.2 Payee Review Queue
### 7.3 Evidence Review Queue

Future full DOC-22 drafting must define admin queue behavior for DOC-06C Bills evidence routes.

Required items to be updated include:

- review evidence submitted from `BILLS-EVIDENCE-UPLOAD`;
- view the current active evidence set from `BILLS-EVIDENCE-DETAIL`;
- assign or override evidence status, including `Pending Review`, `Accepted`, `Correction Needed`, `Update Needed`, `Rejected`, `Duplicate Suspected`, and `Archived`;
- capture reason codes, reviewer identity, timestamp, and affected bill/rent readiness status;
- manage archive-not-delete behavior and controlled access to prior evidence versions;
- route status changes to DOC-08 notifications or dashboard-only action items where applicable;
- audit all evidence view, status-change, archive, override, and sensitive-field reveal actions.

Detailed schema and event taxonomy belong in DOC-18. User-facing evidence routes belong in DOC-06. Evidence verification rules belong in DOC-12. Risk escalation rules belong in DOC-14.

### 7.4 Payment Request Review Queue
### 7.5 Risk Review Queue
### 7.6 Duplicate Detection Queue
### 7.7 Dispute Queue
### 7.8 Clarification Queue
### 7.9 Failed Payment Queue
### 7.10 Payout Exception Queue
### 7.11 Refund/Reversal Queue
### 7.12 Compliance Escalation Queue
### 7.13 Campaign and Promotion Review Queue
### 7.14 Reward Entitlement and Voucher Exception Queue

## 8. Admin Review Workflows

## 9. User Management Workflows

## 10. Evidence and Bill Verification Workflows

## 11. Payment Operations Workflows

Admin dashboard must support DOC-09 user payment instruction review at operations level.

Required capabilities should include:

- view payment instruction status;
- view single-card or split-card funding leg progress;
- view deferred funding date, selected payee transfer date, payment instruction action-alert status, partial funding, remaining unpaid amount, and partial payout linkage;
- view payment quote, promotion quote, reservation status, revalidation result, changed-term acknowledgement, and expiry where applicable;
- distinguish partially funded instruction from completed payment;
- trigger permitted action alert, user action, hold, cancellation, expiry, or escalation workflow according to approved policy.

## 12. Payout and Reconciliation Workflows

## 13. Refund, Cancellation, and Chargeback Operations

## 14. Risk, Fraud, AML, and Anti-Cashout Operations

## 15. Dispute and Clarification Management

## 16. Internal Notes and Case Management

## 17. Admin Actions and Status Changes

## 18. Campaign, Promotion, Coupon, Voucher, Reward, and Referral Operations

Detailed promotion-engine rules belong in DOC-13. Admin workflows should support campaign setup, offer setup, eligibility rule configuration, qualification and entitlement review, coupon/voucher issuance, miles fulfilment status, external voucher exception handling, reward reversal, and approval/audit workflow where promotions are enabled.

### 18.1 Dashboard Shortcut and Placement Configuration

Admin dashboard must support configuration hooks for the DOC-06B designated Home Dashboard flow where enabled.

Required capabilities should include:

- configure default dashboard shortcut set;
- configure default dashboard shortcut order;
- add, disable, hide, or restore shortcuts by feature, module, category, user type, eligibility, or launch phase;
- preserve user-managed shortcut order and visibility preferences where allowed;
- allow user restore-to-default behavior;
- configure Important Notice / Action Required items, including priority, expiry, collapse behavior, route target, audience, approval status, and audit log;
- configure Featured / What's New / Hot Offer carousel placements, including priority, start/end date, targeting, offer or announcement linkage, route target, approval status, enable/disable, and audit log;
- distinguish dashboard placement from notification delivery, inbox entry, campaign eligibility, and promotion entitlement;
- record admin changes to shortcut defaults, dashboard placements, carousel configuration, and notice/action items.

Detailed final admin screens, permission matrix, approval workflow, and implementation fields will be drafted in full DOC-22 and DOC-18.

### 18.2 Reminder Default Configuration

Admin dashboard must support configuration hooks for DOC-06C bill/rent reminder defaults where enabled.

Required capabilities should include:

- configure default reminder timing for rent, monthly bills, and one-off invoices;
- configure allowed reminder cycles, offsets, and custom-date availability by category or module;
- enable, disable, or gate reminder features by feature, category, user type, eligibility, risk state, launch phase, or compliance restriction;
- configure whether system/default reminders may be disabled, reset, or replaced by user custom override;
- configure reminder notification channel availability in coordination with DOC-08;
- audit changes to reminder defaults, eligibility, channel linkage, and feature gating.

Detailed reminder data structures belong in DOC-18. User-facing reminder route behavior belongs in DOC-06.

### 18.3 Request Creation and Delivery Configuration

Admin dashboard must support future configuration hooks for DOC-06B `REQUESTS-NEW`, `REQUESTS-DETAIL`, and request-delivery controls where enabled.

Required capabilities should include:

- configure request feature/module availability by user type, category, risk state, launch phase, or compliance restriction;
- configure request expiry, resend eligibility, reminder cooldown, maximum reminders per period, and cancellation rules;
- configure whether specific categories require admin review or approved exception before evidence-gated request delivery;
- configure approved request delivery and sharing channels, including in-app, app link, WhatsApp deeplink, QR code, or other approved channels;
- distinguish request reminders from new request creation;
- audit request creation, evidence-gated send, resend, reminder, cancellation, share-link generation, and channel-configuration changes.

### 18.4 Payment Profile and Tokenized Card Configuration

Admin dashboard must support future configuration and operations hooks for DOC-06B `PAYMENT-PROFILE-ROOT`, DOC-09 payment profile use, and DOC-19 tokenization controls where enabled.

Required items to be updated include:

- configure controls for the MVP maximum of 6 cards per payment profile and checkout split;
- configure default confirmation behavior, optional user-enabled payment-passcode confirmation, and risk/PSP/security step-up rules for card removal/update;
- view masked tokenized card and payment profile status without exposing raw card data, CVV, sensitive authentication data, or full token secrets;
- view profile action-required reasons such as removed, expired, suspended, invalid, or unavailable card;
- support permitted suspend/reactivate/flag workflows for risk, support, or partner requirements;
- audit card add, tokenization return, card removal/archive, default-card change, profile create/edit/remove, profile star/unstar, and profile action-required resolution.

Detailed Payment Profile route behavior belongs in DOC-06B. Checkout use belongs in DOC-09. Tokenization and card-security controls belong in DOC-19. Notification routing belongs in DOC-08. Data, state, and audit-event taxonomy belongs in DOC-18.

### 18.5 Offers Collection, Placement, and Application Configuration

Future full DOC-22 drafting must support the confirmed DOC-06B, DOC-09, and DOC-13 Offers behavior without redefining promotion logic.

Required capabilities include:

- assign one Offer ID to one or more discovery collections;
- configure Featured / Hot placement separately from collection membership;
- configure the primary `OFFERS-ROOT` placement and suppress unintended repeated root display of the same Offer ID by default;
- allow an approved, audited override for intentional repeated root placement;
- configure pinning and display priority separately for each collection;
- configure offer enablement, display dates, targeting, labels, and publication approval;
- configure whether an offer is payment-method-sensitive and automatically applied or belongs to the separate user-selected coupon/voucher/discount family;
- configure the approved user-value amount/method and deterministic equal-value or non-comparable tie-break used to auto-select the best eligible Card Offer;
- audit collection assignment, placement, priority, override, value-comparison, and application-mode changes.

Detailed eligibility, stacking, value comparison, and benefit calculation belong in DOC-13. Same-screen checkout behavior belongs in DOC-09. Final data objects and events belong in DOC-18.

### 18.6 Referral Program, Campaign, and Qualification Configuration

Future full DOC-22 drafting must support the confirmed DOC-06B and DOC-13 Referral baseline without redefining referral or reward logic.

Required capabilities include:

- enable or disable the PayPlus Referral Program and individual campaigns;
- support one MVP campaign and preserve support for multiple future campaigns;
- configure separate referrer and referee offers and beneficiary-role entitlements;
- configure qualifying conditions, source events, payment/risk finality, qualification periods, campaign end, claim deadlines, reward usage expiry, quotas, and per-user limits as separate controls;
- reserve quota/value when each role-sensitive entitlement is created and preserve the applicable campaign, offer, benefit, and terms snapshot;
- keep reusable user-linked referral codes non-expiring by default while preserving optional future validity controls;
- configure campaign availability, terms, share channels, and campaign-specific registration context;
- review privacy-safe attribution and qualification records without exposing unnecessary bills, evidence, payments, cards, KYC data, payees, or internal risk reasons;
- hold, release, reject, reverse, or claw back referral entitlements or issued rewards according to approved permissions, reason codes, and audit rules; an authorized hold on a claimed item must support the inactive `Under Review` History presentation defined by DOC-06B without exposing internal reasons;
- reconcile duplicate, concurrent, retried, or uncertain claim submissions against the existing entitlement-to-instrument issuance result without creating another reward;
- support controlled attribution correction only if later approved, with reason capture, authorization, and full audit history;
- audit campaign changes, rule changes, qualification decisions, manual overrides, entitlement actions, claim outcomes, and reward issuance linkages.

Detailed Referral route behavior belongs in DOC-06B. Referral, qualification, entitlement, and reward rules belong in DOC-13. Privacy and masking belong in DOC-15. Final objects, identifiers, statuses, events, and lineage belong in DOC-18.

### 18.7 Reward Instrument and Fulfilment Operations

Future full DOC-22 drafting must support the confirmed canonical reward lifecycle without redefining DOC-13 business rules.

Required capabilities include:

- manage activation and operational readiness for launch-supported external-voucher and miles fulfilment methods;
- view instrument type, earning source, participant role where applicable, program, campaign/offer/entitlement source, fulfilment method, and canonical status as separate dimensions;
- review Action Required, In Progress, Under Review, unknown-result, partner-failure, duplicate-use, and reconciliation exceptions;
- perform permitted hold, release, reverse, void, restore, reissue, or fulfilment-retry actions with permission, reason, user-notice, and audit controls;
- prevent duplicate issuance or use by reconciling repeated, concurrent, retried, and uncertain operations against the authoritative result;
- configure the seven-calendar-day expiring-soon default and later approved fixed-count usage where enabled;
- define hold-versus-expiry behavior after the open DOC-13 policy decision is resolved;
- restrict credential reveal, export, partner payload, and internal reason access according to DOC-15 and DOC-19.

Detailed reward logic and status meaning belong in DOC-13 and the status-display reference matrix. User-facing screens belong in DOC-06B, checkout selection in DOC-09, privacy in DOC-15, and final objects/events in DOC-18.

### 18.8 Me Route and Account-Control Configuration

Future full DOC-22 drafting must support the confirmed DOC-06B `ME-ROOT` baseline without turning the admin dashboard into the owner of user-facing route behavior.

Required controls include:

- preserve `ME-ROOT` as a permanent MVP bottom-navigation destination;
- prevent ordinary configuration from hiding core Account Information, Security & Privacy, Help & Support, About PayPlus, Terms and Policies, or Log Out controls;
- enable or disable optional module rows, including Membership and Receiving Details where the underlying capability is unavailable, while preserving permitted access to retained user records;
- manage account, identity-verification, security, and receiving-setup action-required cases without exposing internal reasons on the user root;
- support controlled review and approval of receiving/payout-destination changes under DOC-10, DOC-15, and DOC-19;
- support controlled archived/previous evidence access and audit under DOC-06C, DOC-12, DOC-15, and DOC-18;
- audit sensitive reveal, account/profile changes, privacy requests, receiving-destination changes, optional-row configuration, and account restriction or closure operations;
- preserve the separate More boundary for dashboard shortcut management, reorder/arrangement, restore-default, overflow, and secondary services.

Detailed `ME-ROOT` route behavior belongs in DOC-06B. Notification preferences belong in DOC-08, payout-destination rules in DOC-10, evidence in DOC-06C/DOC-12, privacy in DOC-15, and final objects/events in DOC-18.

## 19. Audit Logging Requirements

## 20. Notifications and Escalations

## 21. Dashboard Screen Inventory

## 22. Reporting and Export Requirements

## 23. Security and Access Control Requirements

Admin access must be role-based and aligned with DOC-15 and DOC-19. Sensitive identity, evidence, payment, payout, risk, promotion, support, and authentication/security data should use masking, controlled reveal, reason capture, and audit logging.

Admin users should not access raw card data, CVV, sensitive authentication data, full token secrets, or unrestricted identity/evidence files unless explicitly approved under the final security and privacy model.

## 24. Privacy and Data Handling Requirements

Admin screens must respect DOC-15 data classification and DOC-18 field metadata.

Required admin data-handling controls should include:

- field-level visibility by role, queue, and approved purpose;
- masking and reveal rules for sensitive fields;
- access reason capture for sensitive data views, exports, downloads, overrides, and corrections;
- audit logging for access, change, export, review, hold, release, override, and deletion actions;
- audit logging for dashboard shortcut configuration, dashboard placement configuration, notice/action configuration, carousel configuration, restore-default configuration, and reminder default configuration;
- privacy-safe duplicate/reused evidence warnings that do not reveal another user's private data;
- export controls for reports, bank files, payout batches, evidence packages, dispute files, and promotion/partner reports.

Detailed workflow, screen design, and permission matrix will be drafted in full DOC-22.

## 25. Monitoring and Incident Response Linkage

## 26. MVP Acceptance Criteria

## 27. Open Questions

## 28. Revision History

| Version | Date | Summary |
| --- | --- | --- |
| 0.9.0 | 2026-07-22 | Added future admin and operations markers for permanent `ME-ROOT`, protected core controls, optional-row enablement, account action-required handling, Receiving Details, archived-evidence access, reveal/privacy auditability, and the separate More shortcut-management boundary. |
| 0.8.0 | 2026-07-21 | Added future Reward operations markers for launch-supported partner/miles readiness, separate data dimensions, lifecycle and exception queues, authoritative/idempotent fulfilment, expiry configuration, hold-versus-expiry follow-up, and credential access controls. |
| 0.7.0 | 2026-07-21 | Added future Referral admin markers for entitlement-time quota reservation and terms snapshot, separate campaign/claim/use dates, idempotent claim oversight, and authorized hold/release handling for exceptional `Under Review` presentation. |
| 0.6.0 | 2026-07-21 | Added future Referral Program, campaign, role-sensitive offer, qualification, finality, quota, validity, privacy-safe review, entitlement hold/release/reversal, attribution-correction, and audit configuration markers. |
| 0.5.0 | 2026-07-20 | Added future admin markers for multi-collection Offers, primary root placement, duplicate suppression and override, per-collection priority, payment-method-sensitive application mode, highest-user-value comparison, and audit controls. |
| 0.1.0 | 2026-06-17 | Added DOC-06 reminder default configuration hooks for bill/rent reminder timing, category gating, channel linkage, and audit logging. |
| 0.2.0 | 2026-06-18 | Added future DOC-22 update markers for admin handling of DOC-06 Bills evidence detail/upload routes, evidence statuses, readiness impact, archive-not-delete behavior, prior evidence access, notifications, and audit logging. |
| 0.3.0 | 2026-07-02 | Added future DOC-22 configuration markers for DOC-06B request creation, evidence-gated request delivery, resend/reminder limits, sharing channels, and audit logging. |
| 0.4.0 | 2026-07-06 | Added future admin configuration and operations markers for DOC-06B Payment Profile route, tokenized card status, payment profile action-required handling, max 6-card payment/profile limit, default confirmation behavior, optional user-enabled payment-passcode confirmation, and audit logging. |

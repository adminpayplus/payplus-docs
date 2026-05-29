---
document_id: DOC-08
title: Notification, Receipt & Communication Rules
version: 0.1.0
status: Founder Working Baseline
owner: Product / Founder
reviewers:
  - Product Lead
  - Design Lead
  - Engineering Lead
  - Compliance Lead
  - Legal Lead
  - Operations Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-05-29
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction Ledger & Reporting
---

# DOC-08 - Notification, Receipt & Communication Rules

## 1. Purpose

This document defines PayPlus MVP rules for notifications, receipts, statements, proof-of-payment messages, and communication delivery.

It ensures users, payees, and admins receive clear, timely, role-appropriate communication without confusing status events with user notifications.

DOC-08 owns:

- notification event IDs;
- default channel rules;
- channel enablement and disablement;
- user notification preferences;
- receipt and statement content rules;
- delivery logging and retention expectations.

This document does not define final legal wording, payment processing logic, payout execution rules, refund operations, database schema, or API contracts.

---

## 2. Scope

### 2.1 In Scope

DOC-08 covers:

- app notifications;
- push notifications;
- email;
- SMS;
- WhatsApp;
- dashboard tasks;
- notification event registry;
- notification channel matrix;
- receipt content rules;
- proof-of-payment content rules;
- statement content rules;
- delivery retry and fallback rules;
- admin-configurable notification settings;
- audit, logging, and retention requirements.

### 2.2 Out of Scope

DOC-08 does not define:

- canonical payment state machine;
- payout state machine;
- refund, cancellation, dispute, chargeback, or reversal policy;
- final legal terms or privacy notice;
- data model fields beyond high-level logging requirements;
- provider-specific integration details;
- marketing campaign content.

Those topics belong in DOC-07, DOC-09, DOC-10, DOC-11, DOC-15, DOC-17, DOC-18, and DOC-21.

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Notification channels | App, push, email, SMS, and WhatsApp are candidate user channels. |
| Dashboard tasks | Admin and operational queues are required for review and exception work. |
| Payment status vs notification | Every important lifecycle event should be recorded as a status or system event, but not every event must notify the user. |
| Notification IDs | Every user-facing or admin-facing notification event should have a stable notification ID. |
| Channel configuration | Each notification event should support channel-level enablement or disablement. |
| Mandatory service messages | Critical account, security, payment, receipt, and compliance messages may be mandatory and not fully user-disableable. |
| Fee and payout wording | Fee, promotion, multi-card, refund, and payout timing wording should align with DOC-07. |
| Record retention | Receipt, payment, account, tax, and audit records are expected to be retained for 7 years, subject to final privacy and legal review. |

---

## 4. Ownership Boundaries

| Topic | Owning Document |
| --- | --- |
| User-facing disclosure and authorization wording | DOC-07 |
| Notification event registry and channel rules | DOC-08 |
| Payment status and processing rules | DOC-09 |
| Payout status and reconciliation rules | DOC-10 |
| Refund, cancellation, dispute, chargeback, and reversal operations | DOC-11 |
| Privacy, consent, retention, and data rights | DOC-15 |
| Notification data model and delivery logs | DOC-18 |
| Provider integrations | DOC-17 |
| Operational monitoring and incident handling | DOC-21 |

DOC-08 should reference these documents instead of duplicating their detailed rules.

---

## 5. Core Definitions

| Term | Meaning |
| --- | --- |
| System event | Internal event or state change that must be recorded. |
| Notification event | Configurable message trigger linked to a system event. |
| Notification ID | Stable identifier for a notification event. |
| Channel rule | Configuration defining which channels are used for a notification event. |
| Template | Channel-specific message content and variables. |
| Delivery log | Record of attempted delivery, result, timestamp, recipient, channel, and template version. |
| Receipt | User-facing confirmation record for a payment outcome. |
| Statement | Periodic or on-demand account/payment summary. |
| Dashboard task | Admin or user task shown inside the PayPlus app or admin dashboard. |

---

## 6. Communication Principles

| Principle | Requirement |
| --- | --- |
| Status first | The system must record the underlying event even if no notification is sent. |
| Configurable delivery | Notification events and channels should be configurable in admin. |
| No false certainty | Do not say payment, payout, refund, or settlement is complete before confirmed. |
| Role-specific | Payer, payee, and admin messages should show only role-appropriate information. |
| Minimal sensitive data | SMS, WhatsApp, and push should avoid sensitive payment, ID, evidence, or card details. |
| Clear action | If user action is required, the message should say what action is needed. |
| Auditability | Sent messages, failed messages, template versions, and delivery outcomes must be logged. |
| Legal control | Legally sensitive templates require approval before publication. |

---

## 7. Notification Architecture

PayPlus should use a four-layer notification model.

| Layer | Description | Example |
| --- | --- | --- |
| System event | Internal state change. Always logged. | `payment_completed` |
| Notification event | Message trigger linked to the system event. | `NOTIF-PAY-003` |
| Channel delivery | Enabled channels for the event. | App, email, WhatsApp |
| Template version | Approved wording used for that channel. | `TPL-PAY-COMPLETE-EMAIL-v1` |

This avoids forcing every status change to send a message.

Example:

| System Event | Notification Decision |
| --- | --- |
| Payment authorized | Status required; notification may be app-only or disabled externally. |
| Payment completed | Status required; app, email, SMS, or WhatsApp may be enabled. |
| Payout completed | Status required; notify payee through approved channels. |

---

## 8. Notification ID Standard

Notification IDs should follow this pattern:

```text
NOTIF-[DOMAIN]-[NUMBER]
```

Domains:

| Domain | Meaning |
| --- | --- |
| `ACCT` | Account, registration, login, security, and profile. |
| `KYC` | KYC, KYB, verification, and onboarding. |
| `REQ` | Payment request lifecycle. |
| `PAY` | Payment authorization, processing, success, and failure. |
| `POUT` | Payout and settlement visibility. |
| `REF` | Refund, reversal, cancellation, and chargeback. |
| `DISP` | Query, clarification, dispute, and case handling. |
| `RCPT` | Receipts, statements, and proof of payment. |
| `ADM` | Admin dashboard tasks and operational queues. |

IDs should remain stable once used in production.

---

## 9. Channel Rules

### 9.1 Channel Types

| Channel | Intended Use | Sensitive Data Rule |
| --- | --- | --- |
| App notification | In-app status, history, and task alerts. | May show more detail if authenticated. |
| Push notification | Short alert to return to app. | Avoid sensitive details. |
| Email | Receipts, statements, account notices, and longer messages. | Use appropriate masking and access links. |
| SMS | Short service alert or fallback. | Avoid detailed payment/evidence/card data. |
| WhatsApp | Short service alert, receipt prompt, or fallback where consented. | Avoid sensitive details; link back to app where practical. |
| Dashboard task | Admin or user task requiring action. | Show role-permitted operational details. |

### 9.2 Channel Configuration

Admin configuration should support:

- event enabled or disabled;
- channel enabled or disabled;
- mandatory or optional classification;
- default recipient role;
- template version;
- fallback channel;
- retry rule;
- user preference override where allowed;
- approval status for legally sensitive templates.

---

## 10. Mandatory, Optional, and Disabled Messages

| Classification | Meaning | User Preference |
| --- | --- | --- |
| Mandatory service | Required for security, account, payment, receipt, compliance, or legal reasons. | Cannot be fully disabled. |
| Important service | Strongly recommended, but channel mix may vary. | User may adjust non-core channels. |
| Optional service | Helpful lifecycle or reminder message. | User may disable where allowed. |
| Admin-only | Internal queue or task. | Not user-controlled. |
| Disabled | Event is logged, but no notification is sent. | Not applicable. |

Payment apps usually keep payment completion, failed payment, security, receipt, and compliance messages as mandatory or important service messages. Promotional messages should be optional and consent-based.

---

## 11. Notification Event Registry

### 11.1 Account and Verification Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-ACCT-001` | Account registration started | App, email | Important service |
| `NOTIF-ACCT-002` | Account registration completed | App, email | Important service |
| `NOTIF-ACCT-003` | Security or account change | App, email, SMS optional | Mandatory service |
| `NOTIF-KYC-001` | KYC/KYB submission started | App | Important service |
| `NOTIF-KYC-002` | KYC/KYB submission received | App, email optional | Important service |
| `NOTIF-KYC-003` | KYC/KYB approved | App, email optional | Important service |
| `NOTIF-KYC-004` | KYC/KYB requires action | App, push optional, email optional | Important service |
| `NOTIF-KYC-005` | KYC/KYB rejected or suspended | App, email | Mandatory service |

### 11.2 Request Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-REQ-001` | Payer-created request created | App | Important service |
| `NOTIF-REQ-002` | Payee-created request created | App | Important service |
| `NOTIF-REQ-003` | Payment request received | App, push optional, email optional, WhatsApp optional | Important service |
| `NOTIF-REQ-004` | Request viewed | App or disabled | Optional service |
| `NOTIF-REQ-005` | Clarification requested | App, push optional, email optional | Important service |
| `NOTIF-REQ-006` | Clarification response received | App, push optional | Important service |
| `NOTIF-REQ-007` | Request accepted | App | Important service |
| `NOTIF-REQ-008` | Request rejected | App, email optional | Important service |
| `NOTIF-REQ-009` | Request cancelled | App, email optional | Important service |
| `NOTIF-REQ-010` | Request expired | App, email optional | Optional service |

### 11.3 Payment Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-PAY-001` | Payment authorized | App or disabled external channels | Important service |
| `NOTIF-PAY-002` | Payment processing | App or disabled external channels | Optional service |
| `NOTIF-PAY-003` | Payment completed | App, email, SMS optional, WhatsApp optional | Mandatory service |
| `NOTIF-PAY-004` | Payment failed | App, push optional, email optional, SMS optional | Mandatory service |
| `NOTIF-PAY-005` | Multi-card partial failure | App, push optional, email optional | Mandatory service |
| `NOTIF-PAY-006` | Payment held for review | App, email optional | Important service |

Payment authorization may require a status update without an external notification. Payment completion usually requires a receipt or confirmation message.

### 11.4 Payout Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-POUT-001` | Payout pending | App | Optional service |
| `NOTIF-POUT-002` | Payout processing | App or disabled external channels | Optional service |
| `NOTIF-POUT-003` | Payout completed | App, email, WhatsApp optional, SMS optional | Important service |
| `NOTIF-POUT-004` | Payout failed | App, email, dashboard task | Mandatory service |
| `NOTIF-POUT-005` | Payout held for review | App, email optional, dashboard task | Important service |

Payout messages must not overpromise timing. They should align with the T+1 to T+3 upstream settlement and same-day-after-settlement payout baseline.

### 11.5 Refund, Reversal, Dispute, and Chargeback Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-REF-001` | Refund requested | App, email optional | Important service |
| `NOTIF-REF-002` | Refund approved | App, email optional | Important service |
| `NOTIF-REF-003` | Refund rejected | App, email optional | Important service |
| `NOTIF-REF-004` | Refund completed | App, email | Mandatory service |
| `NOTIF-REF-005` | Reversal completed | App, email | Mandatory service |
| `NOTIF-DISP-001` | Dispute or query opened | App, email optional | Important service |
| `NOTIF-DISP-002` | Dispute requires action | App, push optional, email optional | Important service |
| `NOTIF-DISP-003` | Dispute resolved | App, email optional | Important service |
| `NOTIF-DISP-004` | Chargeback received | App, email, dashboard task | Mandatory service |
| `NOTIF-DISP-005` | Chargeback outcome recorded | App, email, dashboard task | Mandatory service |

Detailed policy and operational handling belong in DOC-11 and DOC-21.

### 11.6 Receipt and Statement Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-RCPT-001` | Payment receipt available | App, email | Mandatory service |
| `NOTIF-RCPT-002` | Proof of payment available | App, email optional | Important service |
| `NOTIF-RCPT-003` | Payee statement available | App, email optional | Important service |
| `NOTIF-RCPT-004` | Payer statement available | App, email optional | Important service |
| `NOTIF-RCPT-005` | Receipt correction or replacement | App, email | Mandatory service |

### 11.7 Admin Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-ADM-001` | Request requires review | Dashboard task | Admin-only |
| `NOTIF-ADM-002` | High-risk request detected | Dashboard task | Admin-only |
| `NOTIF-ADM-003` | Missing or invalid evidence | Dashboard task | Admin-only |
| `NOTIF-ADM-004` | Duplicate suspected | Dashboard task | Admin-only |
| `NOTIF-ADM-005` | Payment failed and requires review | Dashboard task | Admin-only |
| `NOTIF-ADM-006` | Payout failed or returned | Dashboard task | Admin-only |
| `NOTIF-ADM-007` | Refund or reversal review required | Dashboard task | Admin-only |
| `NOTIF-ADM-008` | Dispute or chargeback review required | Dashboard task | Admin-only |
| `NOTIF-ADM-009` | Operational exception | Dashboard task | Admin-only |

---

## 12. Receipt Rules

### 12.1 Payment Receipt

A payment receipt should include:

- receipt ID;
- request ID;
- payment ID where available;
- payer display name or payer reference;
- payee display name or payee reference;
- payment amount;
- service fee where applicable;
- discount, coupon, promotion, or subsidy where applicable;
- total charged;
- payment status;
- payment date and time;
- masked payment method summary;
- multi-card split summary where applicable;
- bill, invoice, rent, or obligation reference;
- payout or settlement status where appropriate;
- support or dispute reference path.

### 12.2 Proof of Payment

Proof of payment should be available only when the relevant payment outcome is confirmed.

It should not imply payout is complete unless payout completion is separately confirmed.

### 12.3 Receipt Corrections

If receipt content is corrected or replaced:

- create a new receipt version;
- retain the prior version where required;
- log the correction reason;
- notify affected users where material.

---

## 13. Statement Rules

Statements may be available to payers and payees.

Statement content should include:

- statement period;
- payer or payee account reference;
- payment requests;
- completed payments;
- failed payments;
- refunds;
- reversals;
- chargebacks where applicable;
- fees;
- discounts or promotions;
- payout records where applicable;
- downloadable format where supported.

Final export formats remain to be confirmed.

---

## 14. Sensitive Data and Masking

Notifications must avoid unnecessary sensitive data.

| Data Type | Rule |
| --- | --- |
| Card details | Show masked card summary only. |
| ID documents | Do not send by SMS, WhatsApp, push, or ordinary email. |
| Evidence documents | Link to authenticated app view where possible. |
| Risk decisions | Use neutral user-facing wording. |
| Admin notes | Do not expose to users unless approved. |
| Payer/payee personal data | Show only role-appropriate information. |

---

## 15. User Preferences and Consent

Users should be able to manage optional notification preferences where permitted.

Preference controls may include:

- push enabled or disabled;
- email enabled or disabled for optional messages;
- SMS enabled or disabled for optional messages;
- WhatsApp enabled or disabled where consented;
- marketing messages enabled or disabled;
- language preference where supported.

Mandatory service messages may remain enabled even if optional channels are disabled.

WhatsApp, SMS, email, and marketing communications must follow consent, privacy, direct marketing, and provider requirements.

---

## 16. Retry, Fallback, and Duplicate Control

Notification delivery should support:

- retry after temporary provider failure;
- fallback channel where configured;
- duplicate suppression;
- rate limits;
- quiet-hour rules where appropriate;
- failure logging;
- admin visibility for important failed service messages.

Do not repeatedly send the same message if the user already acted on the underlying request.

---

## 17. Admin Configuration

The admin dashboard or configuration layer should support:

- notification event enablement;
- per-channel enablement;
- mandatory, important, optional, admin-only, or disabled classification;
- template version selection;
- provider selection where applicable;
- fallback rules;
- retry settings;
- user preference override rules;
- quiet-hour settings where applicable;
- message preview;
- approval workflow for sensitive templates;
- audit log for configuration changes.

Admin changes to legal, payment, privacy, fee, refund, chargeback, or payout timing wording should require approval.

---

## 18. Delivery Logging and Retention

PayPlus should log:

- notification ID;
- system event ID where available;
- recipient user or role;
- channel;
- template ID and version;
- message category;
- delivery status;
- provider reference where available;
- sent timestamp;
- failure reason where available;
- retry count;
- related request, payment, payout, receipt, dispute, or account ID.

Receipt, payment, account, tax, and audit records are expected to be retained for 7 years, subject to final privacy and legal review.

Detailed schema belongs in DOC-18.

---

## 19. Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-08-001 | Which notification provider will be used for email, SMS, push, and WhatsApp? | Engineering / Product | Open |
| OQ-08-002 | Which notification events are mandatory service messages and cannot be fully disabled? | Legal / Product / Compliance | Open |
| OQ-08-003 | What exact templates are required for each notification event and channel? | Product / Design / Legal | Open |
| OQ-08-004 | What WhatsApp consent and opt-out flow is required? | Legal / Product | Open |
| OQ-08-005 | What SMS consent, fallback, and cost controls are required? | Product / Operations | Open |
| OQ-08-006 | What statement export formats are required at MVP? | Product / Finance | Open |
| OQ-08-007 | What notification delivery failure threshold should create an admin alert? | Operations / Engineering | Open |
| OQ-08-008 | What retention exceptions, deletion rules, and masking rules apply beyond the 7-year baseline? | Legal / Privacy | Open |

---

## 20. Acceptance Criteria

DOC-08 is acceptable when:

- notification events are separated from system statuses;
- every notification event has a stable ID;
- default channels are defined without forcing every status to notify users;
- admin configurability is defined;
- mandatory, optional, disabled, and admin-only messages are distinguished;
- sensitive data rules are clear;
- receipt and statement rules are defined;
- delivery logging and retention expectations are defined;
- detailed payment, payout, refund, dispute, and data-model logic is left to owning documents.

---

## 21. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.1.0 | 2026-05-29 | Initial founder working baseline for notification event IDs, channel rules, receipts, statements, admin configurability, and delivery logging. |

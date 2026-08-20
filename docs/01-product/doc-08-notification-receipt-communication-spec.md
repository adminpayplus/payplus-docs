---
document_id: DOC-08
title: Notification, Receipt & Communication Rules
version: 2.0.0
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
last_updated: 2026-08-19
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-08 - Notification, Receipt & Communication Rules

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-08` |
| **Title** | Notification, Receipt & Communication Rules |
| **Version** | `2.0.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Compliance Lead<br>Legal Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-08-19` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This document defines PayPlus MVP rules for notifications, receipts, statements, proof-of-payment messages, and communication delivery.

It ensures users, payees, and admins receive clear, timely, role-appropriate communication without confusing status events with user notifications.

DOC-08 owns:

- notification event IDs;
- notification category, message eligibility, and Inbox-record rules;
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
- admin/operational task notification triggers;
- notification event registry;
- notification channel matrix;
- receipt content rules;
- proof-of-payment content rules;
- statement content rules;
- evidence verification, correction, duplicate warning, and admin review communication triggers;
- promotion, coupon, voucher, reward, referral, membership, miles, and entitlement communication triggers;
- delivery retry and fallback rules;
- notification parameters that a formal owner may expressly permit for operational configuration;
- audit, logging, and retention requirements.

### 2.2 Out of Scope

DOC-08 does not define:

- canonical payment state machine;
- payout state machine;
- refund, cancellation, dispute, chargeback, or reversal policy;
- OCR/document AI, evidence verification, duplicate detection, and risk rule logic;
- promotion eligibility, entitlement, redemption, fulfilment, and calculation logic;
- final legal terms or privacy notice;
- data model fields beyond high-level logging requirements;
- provider-specific integration details;
- marketing campaign content.

Those topics belong in DOC-07, DOC-09, DOC-10, DOC-11, DOC-12, DOC-13, DOC-14, DOC-15, DOC-17, DOC-18, DOC-19, DOC-21, and DOC-22.

---

## 3. Current Decision Baseline

DOC-08 owns notification identity, recipient eligibility consumption, channels, templates, preferences, delivery, retry and delivery evidence. It consumes — but does not decide — source, payment, risk, privacy, support and route outcomes. The Consumer User is Payer-only. An economic Payee may be an individual or institution/company and need not be a User.

The only accepted Payee-directed concept in this Draft is an optional, one-way Individual notification when upstream owner-governed eligibility permits it. This does not create a Payee account, Request, Linking, To Receive, Receiving Info, route, event contract, reciprocal visibility, channel, template or runtime relationship. No production Request/Payee-role legacy data, reader, adapter, fallback or deep-link exists.

| Area | Baseline |
| --- | --- |
| Notification channels | App, push, email, SMS, and WhatsApp are candidate user channels. |
| Admin/operational task notifications | Owner-governed review and exception notifications may be emitted; DOC-22 may execute only expressly owner-permitted workflows. |
| Payment status vs notification | Every important lifecycle event should be recorded as a status or system event, but not every event must notify the user. |
| Notification IDs | Every user-facing or admin-facing notification event should have a stable notification ID. |
| Channel configuration | Each notification event should support channel-level enablement or disablement. |
| Evidence verification | Evidence correction, review, duplicate/reused evidence, and verification outcome events should support user or admin messages where action is required. |
| Promotion communication | Reward, coupon, voucher, miles, referral, membership, and entitlement messages should be event-driven and consent-aware. |
| Mandatory service messages | Critical account, security, payment, receipt, and compliance messages may be mandatory and not fully user-disableable. |
| Fee and payout wording | Fee, promotion, multi-card, refund, and payout timing wording should align with DOC-07. |
| Record retention | Indefinite retention remains the accepted product/governance direction for notification, receipt, statement, Payment, account, tax and audit records, subject to DOC-15 and Legal/Privacy confirmation of lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries. DOC-08 does not define storage or disposition mechanics. |

---

## 4. Ownership Boundaries

| Topic | Owning Document |
| --- | --- |
| User-facing disclosure and authorization wording | DOC-07 |
| Notification event registry and channel rules | DOC-08 |
| Payment status and processing rules | DOC-09 |
| Payout status and reconciliation rules | DOC-10 |
| Refund, cancellation, dispute, chargeback, and reversal operations | DOC-11 |
| Evidence verification, OCR/autofill, duplicate/reused evidence | DOC-12 |
| Promotion, coupon, voucher, reward, referral, membership, miles, entitlement | DOC-13 |
| Risk scoring and anti-cashout rules | DOC-14 |
| Privacy, consent, retention, and data rights | DOC-15 |
| Notification data model and delivery logs | DOC-18 |
| Security, masking, and access control | DOC-19 |
| Provider integrations | DOC-17 |
| Operational monitoring and incident handling | DOC-21 |
| Admin dashboard workflow and configuration | DOC-22 executes only expressly owner-permitted operational workflows; DOC-08 and applicable owners retain policy authority. |

DOC-08 should reference these documents instead of duplicating their detailed rules.

---

## 5. Core Definitions

| Term | Meaning |
| --- | --- |
| System event | Internal event or state change that must be recorded. |
| Notification event | Configurable message trigger linked to a system event. |
| Notification ID | Stable identifier for a notification event. |
| Notification message | One recipient-specific communication record created from a notification event. |
| Notification category | Approved Inbox presentation grouping: `System`, `Service`, `Transaction`, or `Promotion`. It is not a domain status. |
| Inbox presentation state | Recipient-specific `Unread`, `Read`, or `Archived` state. It does not change the owning domain object. |
| Channel rule | Configuration defining which channels are used for a notification event. |
| Template | Channel-specific message content and variables. |
| Delivery log | Record of attempted delivery, result, timestamp, recipient, channel, and template version. |
| Receipt | User-facing transaction confirmation record for a completed transaction. It may be viewed, downloaded, shared where allowed, or re-issued/replaced according to approved rules. |
| Statement | Periodic or on-demand Payer account/payment summary. It should not include unrelated system events. |
| Dashboard task | Notification representation for an owner-governed Admin or user task; DOC-08 does not define the dashboard or task workflow. |
| Important Notice / Action Required | DOC-06B logged-in dashboard section that consumes existing Inbox-backed notification records and DOC-08-published values. It does not create a duplicate Home notification record and is not itself a notification status, business status, or domain event. |
| Hot Offer | DOC-06B Home carousel placement for canonical Offers selected by Admin. It is a placement surface, not a notification event or Inbox record by itself. |

---

## 6. Communication Principles

| Principle | Requirement |
| --- | --- |
| Status first | The system must record the underlying event even if no notification is sent. |
| Configurable delivery | Notification events and channels may identify parameters expressly permitted for operational configuration by the applicable formal owner. |
| No false certainty | Do not say payment, payout, refund, or settlement is complete before confirmed. |
| Role-specific | Payer, payee, and admin messages should show only role-appropriate information. |
| Minimal sensitive data | SMS, WhatsApp, and push should avoid sensitive payment, ID, evidence, or card details. |
| Clear action | If user action is required, the message should say what action is needed. |
| Auditability | Sent messages, failed messages, template versions, and delivery outcomes must be logged. |
| Legal control | Legally sensitive templates require approval before publication. |
| Placement separation | Dashboard placement, notification delivery, inbox entry, and promotion display are related but separate decisions. A dashboard item does not automatically require push, SMS, email, or WhatsApp delivery. |

Where notifications, receipts, statements, proof messages, or in-app communication display payment lifecycle status to users, user-facing status labels should follow `docs/traceability/status-display-reference-matrix.md`. This document controls communication rules and templates, but it should not redefine status-display mapping.

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
| Payout completed | Status required; any recipient notification is owner-governed and does not imply a Payee account or route. |

For DOC-06B dashboard placements:

| Dashboard Surface | Communication Rule |
| --- | --- |
| Important Notice / Action Required | Consumes an existing Inbox-backed notification record without creating a duplicate record. DOC-08 owns notification identity, recipient, lifecycle, Inbox eligibility and categorization, delivery, and preserved source signals; DOC-06B owns Home selection, presentation, dismissal, routing, and return behavior. |
| Hot Offer | Home presentation does not create a notification event or Inbox record. Canonical Offer content and truth belong in DOC-13; Home placement configuration and publication quality controls belong in DOC-22; notification delivery remains a separate DOC-08 decision. |
| Inbox icon | Opens `NOTIFICATION-INBOX`, which may show notification-backed messages, announcements, support replies, and user action items according to configured rules. |

The user-facing notification family is `NOTIFICATION-ROOT`, with `NOTIFICATION-INBOX` as its default child screen, `NOTIFICATION-DETAIL` for one message, and `NOTIFICATION-SETTINGS` for preferences. `NOTIFICATION-LIST` and `NOTIFICATION-CARD` are components, and Archived is an Inbox filter rather than a separate route. DOC-06B owns screen behavior, entry points, and return rules; DOC-08 owns which records exist and how they are categorized, delivered, retained, and controlled.

### 7.1 HOME-ROOT Important Notice Notification Contract

DOC-08 publishes an existing Inbox-backed notification record and its canonical notification values for consumption by the DOC-06B HOME-ROOT Important Notice contract. This handoff does not create a second Home notification record.

DOC-08 owns or preserves, without deriving or reinterpreting:

- notification identity, recipient, Inbox eligibility, record category, and current lifecycle state;
- the issued timestamp;
- source-event linkage and the source-provided destination linkage, where one is currently available;
- the notification-detail identity and data presented through canonical `NOTIFICATION-DETAIL`;
- Severity;
- Home category of `System`, `Payment`, `Account`, or `Other Important`;
- Business Priority Rank;
- `Unread`, `Read`, `Archived`, expired, withdrawn, and other notification-owned states; and
- applicable due timestamp and canonical timezone for an eligible Bill/Rent reminder.

The Home category is a source-preserved selection signal and does not replace DOC-08 Inbox presentation grouping or create a domain status. Missing or invalid source values remain upstream contract matters.

DOC-06B is the sole normative owner of HOME-ROOT selection, one-at-a-time presentation, ordering, visibility and zero state, dismissal, body/action interaction, Details-close return branches, and the Rent-reminder Home display window. DOC-08 supplies the canonical notification record and values above and does not restate or derive that Home algorithm.

Where a formal route owner defines an eligible destination, a notification may reference that owner-approved destination and must revalidate current state and permission before action. Active examples are account/identity/security, Evidence, Bill/Rent reminder, Payer Bills, payment-profile, Archive root or archived Bills, receipt, statement and Activity destinations. DOC-08 must not route to retired Request/Linking/Receive/Receiving Info or provisional Archived Documents identities, and it must not decide an action, return, preview, route state or eligibility.

Promotion-discovery notifications should route to the relevant `OFFER-DETAIL`, or to `OFFERS-ROOT` only when no specific offer exists. Issued-reward notifications should route to `REWARDS-ROOT` or the relevant `REWARD-DETAIL`, using user-facing labels from the status-display reference matrix. Notifications must not contain a redeemable QR, full partner/redemption code, secret, internal reference, or internal risk reason. Referral attribution or qualification notifications should route to `REFERRAL-ROOT`; a referrer or referee entitlement-availability notification should route to `REFERRAL-REWARDS-LIST` or the relevant `REFERRAL-ENTITLEMENT-DETAIL`; an issued, reversed, or administrator-held reward notification should route to the canonical `REWARD-DETAIL` where a specific instrument exists. Notifications must not open `REFERRAL-REWARD-CLAIM` directly. Claim-deadline reminders are not required for MVP. A share-sheet action, copied link, or displayed QR is not an invitation delivery event and must not notify an unknown recipient. The notification record should preserve its source and target context without requiring a DOC-06B entry-point ID. Notification routing must not turn `BILLS-PAY` into an Offers sub-route.

A Payer's ordinary Bill/Rent Archive visibility action does not create a counterparty notification. Existing payment, Payout, Evidence, risk or legal events notify only under their own owner-governed rules.

DOC-06B `ACTIVITY-ROOT` may expose direct receipt/proof download actions from an expanded activity card where the file is available and the user has permission. DOC-06B `ACTIVITY-DETAIL` may also expose direct receipt/proof download actions. If receipt/proof is unavailable, the button should be hidden by default or disabled only where useful with clear, non-sensitive wording. Invoice/evidence buttons should be hidden where access is not permitted. DOC-08 owns the communication, delivery, file-availability, and receipt/proof wording rules; DOC-15 owns masking and access boundaries.

### 7.2 Inbox Signal Separation

Every Inbox record must keep these concepts separate:

| Signal | Rule |
| --- | --- |
| Category | Use the approved `System`, `Service`, `Transaction`, or `Promotion` presentation group associated with the notification event. |
| Presentation state | Store recipient-specific `Unread`, `Read`, or `Archived`; `All` excludes Archived. |
| Domain status | Resolve the current user-facing label from the owning domain and `status-display-reference-matrix.md`. |
| Action Required | Derive from the owning domain's current user task or resolution need. Inbox must not invent or clear it. |

Opening a notification must revalidate the target, permission, domain status, and action availability. The message may retain status/action-at-send snapshots for audit, while the current UI uses the latest authorized state. Marking a message read or archived changes only the recipient's Inbox presentation.

---

## 8. Notification ID Standard

Notification IDs should follow this pattern:

```text
NOTIF-[DOMAIN]-[NUMBER]
```

Domains:

| Domain | Meaning |
| --- | --- |
| `SYS` | System announcements, service availability, and general platform notices. |
| `SUP` | General support messages and replies that are not formal dispute/case lifecycle events. |
| `ACCT` | Account, registration, login, security, and profile. |
| `KYC` | KYC, KYB, verification, and onboarding. |
| `EVD` | Evidence upload, OCR/autofill, evidence correction, and verification. |
| `PROM` | Promotion, coupon, voucher, reward, referral, membership, miles, and entitlement. |
| `PAY` | Payment authorization, processing, success, and failure. |
| `PINS` | Deliberate Payment Instruction owner-supplied alert. |
| `REM` | Ordinary bill, fee, rent, tenancy, or applicable Bill/Rent Payment Obligation reminders. |
| `POUT` | Payout and settlement visibility. |
| `REF` | Refund, reversal, cancellation, and chargeback. |
| `DISP` | Query, clarification, dispute, and case handling. |
| `RCPT` | Receipts, statements, and proof of payment. |
| `ADM` | Admin dashboard tasks and operational queues. |

IDs should remain stable once used in production.

### 8.1 Message and Trace Identifiers

`NOTIF-[DOMAIN]-[NUMBER]` identifies a stable notification event type; it is not the unique ID of a message sent to one user. The final data model must distinguish:

| Identifier / Reference | Requirement |
| --- | --- |
| `notification_event_id` | Stable event type, such as `NOTIF-PAY-003`. |
| `notification_message_id` | Unique recipient-specific Inbox/message record. |
| `notification_batch_id` | Optional batch, campaign, manual-send, scheduled-job, or support-send grouping. |
| Source event | Source type plus source event ID. |
| Source object | Source object type and ID, such as source, payment, Payout, reward or support case. |
| Recipient | Owner-governed eligible recipient reference; it does not create a role projection. |
| Template | Template ID and version. |
| Destination | Registered route and permitted target object. |
| Correlation controls | Correlation, causation, and deduplication references where applicable. |
| Timestamps | Created, scheduled, sent, read, and archived timestamps as applicable. |
| Delivery attempts | Separate per-channel attempt ID, provider reference, status, timestamp, retry, and failure outcome. |

System-triggered, scheduled, campaign, manual, and support messages should use this common model. DOC-18 owns the final schema and lineage; DOC-22 may execute only expressly owner-permitted operational lookup, approved manual/batch actions, and audit workflow using approved policy and facts.

---

## 9. Channel Rules

### 9.1 Channel Types

| Channel | Intended Use | Sensitive Data Rule |
| --- | --- | --- |
| App / Inbox notification | Authenticated Inbox record, in-app status, history, or task alert. Distinct from device push. | May show more detail if authenticated and permitted. |
| Push notification | Short alert to return to app. | Avoid sensitive details. |
| Email | Receipts, statements, account notices, and longer messages. | Use appropriate masking and access links. |
| SMS | Short service alert or fallback. | Avoid detailed payment/evidence/card data. |
| WhatsApp | Short service alert, receipt prompt, or fallback where consented. | Avoid sensitive details; link back to app where practical. |
| Dashboard task | Admin or user task requiring action. | Show role-permitted operational details. |

### 9.2 Notification Parameter and Operational-Configuration Boundary

DOC-08 owns the notification policy semantics and requirements for event and channel eligibility, mandatory/important/optional/disabled classification, recipient role, template and version, fallback, retry, preference overrides, quiet-hour treatment where applicable, and approval requirements for legally sensitive communication. These requirements remain normative even when an owner permits selected parameters to be operationally configured.

Where DOC-08 or another applicable formal owner expressly permits a parameter to be configured, DOC-22 may execute the owner-permitted Admin workflow using the approved policy and facts. DOC-08 does not prescribe an Admin dashboard, Admin UI, queue, permission model, configuration screen, approval workflow, or other DOC-22 mechanism. DOC-22 may not invent, broaden, or change notification policy independently of DOC-08 or the applicable formal owner.

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
| `NOTIF-ACCT-001` | Restricted PayPlus account created; setup remains incomplete | App, email | Important service |
| `NOTIF-ACCT-002` | Full PayPlus registration completed through Account Activation | App, email | Important service |
| `NOTIF-ACCT-003` | Security or account change | App, email, SMS optional | Mandatory service |
| `NOTIF-ACCT-004` | New-device login or 2FA challenge | App, email, SMS optional | Mandatory service |
| `NOTIF-ACCT-005` | Dormant-login reauthentication required or completed | App, email optional, SMS optional | Mandatory service |
| `NOTIF-ACCT-006` | Material account, contact, login-method/credential or payment-profile change | App, email, SMS optional | Mandatory service |
| `NOTIF-ACCT-007` | Account closure request submitted or cancelled | App, email | Mandatory service |
| `NOTIF-ACCT-008` | Account closure requires action or cannot proceed | App, email, push optional | Mandatory service |
| `NOTIF-ACCT-009` | Account closure completed | Email, SMS optional | Mandatory service |
| `NOTIF-KYC-001` | KYC/KYB submission started | App | Important service |
| `NOTIF-KYC-002` | KYC/KYB submission received | App, email optional | Important service |
| `NOTIF-KYC-003` | KYC/KYB approved | App, email optional | Important service |
| `NOTIF-KYC-004` | KYC/KYB requires action | App, push optional, email optional | Important service |
| `NOTIF-KYC-005` | Identity/KYC/KYB status is `Failed` or `Update Required` | App, email | Mandatory service |
| `NOTIF-PRIV-001` | Privacy request submitted | App, email optional | Important service |
| `NOTIF-PRIV-002` | Privacy request requires action | App, push optional, email | Important service |
| `NOTIF-PRIV-003` | Privacy request completed or unable to complete | App, email | Important service |

KYC/KYB notifications that require user action should open `IDENTITY-VERIFICATION`; approved or informational status messages may open `ACCOUNT-PROFILE`. Identity notifications and banners must use only `Not Verified`, `Processing`, `Verified`, `Failed`, or `Update Required` and the actions in the status-display matrix. `Processing` may produce a dismissible Home banner with View Status; `Verified` may produce a dismissible completion banner; `Failed` and `Update Required` require an Action Required treatment. Dismissal changes presentation only. Internal provider or operational states must map to one approved label and must not expose raw provider or risk reasons. Privacy-request messages open `PRIVACY-DATA-CONTROLS`. Account-closure messages open `ACCOUNT-PROFILE`, except the final completion message where login has been disabled and the notification must use an approved external channel or pre-logon destination. Contact-change messages under `NOTIF-ACCT-006` must notify the old and new channels where available without exposing OTP or recovery detail.

First password setup, password change, payment-passcode Change/Reset, and Google/Apple login-method link or unlink use `NOTIF-ACCT-006`; they do not require separate notification IDs. Successful payment-passcode Change and Reset must notify available verified channels. A temporary registration attempt is not an account and creates no Inbox record. Pre-account prompts, OTPs, provider errors, and other in-flow authentication outcomes use the mandatory DOC-07 outcome/message mechanism rather than notification IDs. `NOTIF-ACCT-001` applies only after restricted-account creation and should open `ACCOUNT-ACTIVATION` where action remains. `NOTIF-ACCT-002` applies after phone, identity, and payment-passcode requirements complete.

`AUTH-RECOVERY` capability decisions, link-validation results, retry paths, and unavailable-method handling are in-flow Outcomes and Resolution Strategies, not notification events. The password-reset email is a controlled authentication delivery and does not prove reset success. A completed password reset must use the mandatory account-security communication family, currently `NOTIF-ACCT-006`, without creating a separate ID unless later operational review requires one. Exact recovery delivery events, Message IDs, CTA mappings, and notification-template treatment remain governed by the DOC-07 authentication slice and future DOC-18/DOC-19 implementation specifications.

### 11.1A Retired Receiving Info Identifiers

Receiving Info identifiers are retired from active notification behavior. They may remain only in append-only revision provenance and do not define a notification, recipient, route, link, delivery obligation or historical-runtime reader.

No Receiving Info notification event is active. Payout, destination and Individual-notification eligibility remain with their formal owners; DOC-08 consumes an owner-approved notification only when one is defined.

### 11.2 Retired Request Identifiers

Request identifiers are retired from active notification behavior. No Request creation, delivery, acceptance, reminder, routing, recipient or deep-link event is defined by DOC-08. Ordinary privacy, support and account requests retain their separately owned ordinary-language meaning.

No Request notification registry, action, recipient, delivery, reminder, route, sharing or deep-link behaviour is active. The retired identifiers are documentation provenance only. Ordinary privacy, support and account requests retain their separately owned ordinary-language meaning.

### 11.3 Evidence Verification Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-EVD-001` | Evidence uploaded or received | App | Optional service |
| `NOTIF-EVD-002` | Evidence fields ready for review | App, push optional | Important service |
| `NOTIF-EVD-003` | Evidence requires correction | App, push optional, email optional | Important service |
| `NOTIF-EVD-004` | Evidence pending admin review | App | Important service |
| `NOTIF-EVD-005` | Duplicate or reused evidence warning | App | Important service |
| `NOTIF-EVD-006` | Evidence verification approved after setup or review | App or disabled external channels | Important service |
| `NOTIF-EVD-007` | Evidence verification rejected | App, email optional | Important service |

Evidence messages must avoid sensitive extracted data in SMS, WhatsApp, push, and ordinary email. Duplicate/reused evidence warnings must not disclose another user's private data. Detailed evidence verification rules belong in DOC-12 and privacy handling belongs in DOC-15.

### 11.4 Promotion and Reward Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-PROM-001` | Coupon or voucher issued | App, push optional | Optional service |
| `NOTIF-PROM-002` | Coupon or voucher expiring | App, push optional, email optional | Optional service |
| `NOTIF-PROM-003` | Coupon, voucher, or discount applied at checkout | App or disabled external channels | Important service |
| `NOTIF-PROM-004` | Reward entitlement reached | App, push optional | Optional service |
| `NOTIF-PROM-005` | Referral attribution confirmed or qualification outcome changed | App, push optional | Optional service |
| `NOTIF-PROM-006` | Referral entitlement available, held, or issued | App, push optional | Optional service |
| `NOTIF-PROM-007` | Membership tier changed | App, email optional | Optional service |
| `NOTIF-PROM-008` | Miles reward pending, submitted, credited, failed, or reversed | App, email optional | Important service |
| `NOTIF-PROM-009` | External voucher claimed, ready, redeemed, failed, or reversed | App, push optional | Important service |
| `NOTIF-PROM-010` | Promotion or reward reversed or clawed back | App, email optional | Important service |

Marketing campaign messages must be consent-based. Service messages that affect checkout, reward fulfilment, reversal, or account records may be mandatory where required. Notification event wording may describe a domain event, but the displayed instrument status must use the status-display reference matrix. Detailed promotion and lifecycle logic belongs in DOC-13.

### 11.5 Payment Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-PAY-001` | Payment authorized | App or disabled external channels | Important service |
| `NOTIF-PAY-002` | Payment processing | App or disabled external channels | Optional service |
| `NOTIF-PAY-003` | Payment completed | App, email, SMS optional, WhatsApp optional | Mandatory service |
| `NOTIF-PAY-004` | Payment failed | App, push optional, email optional, SMS optional | Mandatory service |
| `NOTIF-PAY-005` | Multi-card partial failure | App, push optional, email optional | Mandatory service |
| `NOTIF-PAY-006` | Payment held for review | App, email optional | Important service |
| `NOTIF-PINS-001` | Payment instruction created | App | Important service |
| `NOTIF-PINS-002` | Deferred payment action due | App, push optional, email optional | Important service |
| `NOTIF-PINS-003` | Retired instruction identifier; incomplete Checkout continuation is owner-governed | Owner-governed | Documentation provenance |
| `NOTIF-PINS-004` | Retired instruction identifier; incomplete/partial Checkout is not a Payment Instruction | N/A | Documentation provenance |
| `NOTIF-PINS-005` | Owner-supplied Payment Instruction cancellation/expiry outcome, if defined | Owner-governed | Service boundary |
| `NOTIF-PINS-006` | Owner-supplied Payout outcome, if defined; it is not an instruction event | Owner-governed | Service boundary |
| `NOTIF-PINS-007` | Deferred payment quote or promotion changed before submission | App, push optional | Important service |

Payment authorization may require a status update without an external notification. Payment completion usually requires a receipt or confirmation message.

#### 11.5.1 Instruction-Related Notification Entry Contract

Every instruction-related notification opens `NOTIFICATION-DETAIL` before any payment action. The current baseline does not permit an instruction-related push, email, SMS, WhatsApp message, Inbox card, deeplink, or stored notification action to bypass `NOTIFICATION-DETAIL` and enter `PAYMENT-CHECKOUT` directly.

```text
Instruction-related notification
    -> NOTIFICATION-DETAIL
    -> current-state, authenticated-payer and permission revalidation
    -> owner-approved current CTA, where still available
    -> DOC-09 Instruction Pay Now Checkout Resolver
```

On Detail entry, the notification experience must consume current owner-supplied facts and revalidate:

- the authenticated payer's permission to view and act on the Payment Instruction;
- whether the instruction and its target remain current, valid and available;
- whether the notification's stored action remains permitted; and
- the applicable current Bill/Rent Payment Obligation, Evidence, eligibility, timing and control conditions before exposing a payment CTA.

Where current validation permits an instruction payment action, the Detail CTA invokes the DOC-09 Instruction `Pay Now` Checkout Resolver. It does not identify a predetermined Checkout, establish current eligibility, carry forward prior authorization, or itself create, activate, resume, fund or submit a Checkout.

A stale, withdrawn, expired, ineligible or unavailable notification target remains in `NOTIFICATION-DETAIL` with the applicable current resolution, or returns to an owner-approved source context. An earlier notification action must not create or resume Checkout after that action has ceased to be valid.

Notification content, delivery success, read/archive state, and stored status/action/quote snapshots are historical communication evidence only. They are not authoritative proof of current Checkout eligibility, payer authorization, Provider Confirmation, Payment, or payment result.

Normal due-date reminders and user manual bill/rent reminders continue to route to the bill/rent/Payment Obligation detail screen. No new notification ID is required solely because an instruction later needs card, Payment Profile, quote, fee, benefit, eligibility, or other current resolution. Exact user-facing message and CTA wording remains with DOC-07; DOC-08 owns the notification entry and action-availability contract.

### 11.5A Bill/Rent Reminder Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-REM-001` | Bill/rent reminder created or updated | App | Optional service |
| `NOTIF-REM-002` | Bill/rent reminder due | App, push where permission granted | Optional service |
| `NOTIF-REM-003` | Bill/rent reminder disabled, deactivated, expired, or inactive | App or disabled external channels | Optional service |

Ordinary reminder events are governed by DOC-06C `BILLS-REMINDER-LIST` and `BILLS-REMINDER-DETAIL`. App notification and push notification are MVP where permission is granted. Email, SMS, and WhatsApp may be enabled through the channel matrix, but should avoid sensitive bill, rent, evidence, account, and payee details outside the authenticated app. Payment instruction action alerts remain under `NOTIF-PINS-*` and must not create ordinary bill/rent reminder records.

### 11.6 Payout Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-POUT-001` | Payout pending | App | Optional service |
| `NOTIF-POUT-002` | Payout processing | App or disabled external channels | Optional service |
| `NOTIF-POUT-003` | Payout completed | App, email, WhatsApp optional, SMS optional | Important service |
| `NOTIF-POUT-004` | Payout failed | App, email, dashboard task | Mandatory service |
| `NOTIF-POUT-005` | Payout held for review | App, email optional, dashboard task | Important service |

Payout messages must not overpromise timing. They should use only settlement and payout timing confirmed by DOC-10 and applicable PSP, bank, risk, legal, partner and reconciliation owners.

`NOTIF-POUT-004` may use only an owner-approved Payer destination. It creates no economic-Payee, Receiving Info or corrective route.

### 11.7 Refund, Reversal, Dispute, and Chargeback Events

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

### 11.8 Receipt and Statement Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-RCPT-001` | Payment receipt available | App, email | Mandatory service |
| `NOTIF-RCPT-002` | Proof of payment available | App, email optional | Important service |
| `NOTIF-RCPT-003` | Retired Payee statement identifier; no active notification behaviour | N/A | Documentation provenance |
| `NOTIF-RCPT-004` | Payer statement available where an owner-approved statement exists | App, email optional | Important service |
| `NOTIF-RCPT-005` | Owner-governed transaction-document correction outcome, if any | Owner-governed | Service boundary |

### 11.9 Admin Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-ADM-001` | Owner-governed review requirement | Owner-permitted workflow | Admin-only |
| `NOTIF-ADM-002` | Owner-governed high-risk outcome | Owner-permitted workflow | Admin-only |
| `NOTIF-ADM-003` | Missing or invalid evidence | Dashboard task | Admin-only |
| `NOTIF-ADM-004` | Duplicate suspected | Dashboard task | Admin-only |
| `NOTIF-ADM-005` | Payment failed and requires review | Dashboard task | Admin-only |
| `NOTIF-ADM-006` | Payout failed or returned | Dashboard task | Admin-only |
| `NOTIF-ADM-007` | Refund or reversal review required | Dashboard task | Admin-only |
| `NOTIF-ADM-008` | Dispute or chargeback review required | Dashboard task | Admin-only |
| `NOTIF-ADM-009` | Operational exception | Dashboard task | Admin-only |
| `NOTIF-ADM-010` | Evidence verification review required | Dashboard task | Admin-only |
| `NOTIF-ADM-011` | Duplicate or reused evidence review required | Dashboard task | Admin-only |
| `NOTIF-ADM-012` | Campaign, reward, or promotion exception review required | Dashboard task | Admin-only |

### 11.10 System and Support Events

| ID | Event | Default Channels | Classification |
| --- | --- | --- | --- |
| `NOTIF-SYS-001` | General system announcement published | App; push optional | Important service or Optional service according to approved purpose |
| `NOTIF-SYS-002` | Planned maintenance or material service availability update | App; push/email optional | Important service |
| `NOTIF-SYS-003` | System notice requires user action | App; push/email optional | Important service |
| `NOTIF-SUP-001` | General support reply available | App; push/email optional | Important service |
| `NOTIF-SUP-002` | General support message requires user response | App; push/email optional | Important service |
| `NOTIF-SUP-003` | General support matter updated or closed | App; email optional | Important service |

`SYS` is for platform-wide or service-level notices that do not belong to a more specific domain. `SUP` is for general support communication. Formal clarification, dispute, refund, chargeback, risk, payment, payout, request, and privacy case messages must continue to use their owning domains rather than being reclassified as generic support.

---

## 12. Receipt Rules

### 12.1 Payment Receipt

A payment receipt should include:

- receipt ID;
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
- accepted controlled Bill/Rent Payment Obligation reference;
- payout or settlement status where appropriate;
- support or dispute reference path.

Receipt access, format and presentation remain with the applicable route, content, privacy, representation and acceptance owners; DOC-08 does not define a preview or download contract.

### 12.2 Proof of Payment

Proof of payment should be available only when the relevant payment outcome is confirmed.

It should not imply payout is complete unless payout completion is separately confirmed.

### 12.3 Transaction-Document Corrections

Applicable financial owners determine transaction-document truth and any permitted correction/reissue outcome. DOC-15 owns privacy/retention requirements, DOC-18 future representation/lineage, and DOC-22 may execute only a specifically owner-permitted workflow. DOC-08 creates no version, preview, reissue or delivery mechanism.

---

## 13. Statement Rules

Statements, if defined by their formal owners, are Payer account/payment summaries; an economic Payee is not a statement-holder user role.

Statement content should include:

- statement period;
- Payer account reference;
- completed payments;
- refunds;
- reversals;
- chargebacks where applicable;
- fees;
- discounts or promotions;
- downloadable format where supported.

Statement access, format, correction and delivery remain owner-governed. DOC-08 does not define PDF, route, preview, version, reissue or Admin workflow behaviour.

---

## 14. Sensitive Data and Masking

Notifications must avoid unnecessary sensitive data.

| Data Type | Rule |
| --- | --- |
| Account/security events | Explain required action or completed change; avoid exposing OTP, device fingerprint, risk score, or internal security details. |
| Card details | Show masked card summary only. |
| ID documents | Do not send by SMS, WhatsApp, push, or ordinary email. |
| Evidence documents | Link to authenticated app view where possible. |
| Extracted evidence fields | Avoid sensitive field values in unauthenticated or external channels. |
| Risk decisions | Use neutral user-facing wording. |
| Admin notes | Do not expose to users unless approved. |
| Payer/economic-Payee source-context data | Show only approved-purpose information. |
| DOC-15 classified data | Channel content must respect data class, sensitivity, consent, masking, and approved-purpose rules. |

---

## 15. User Preferences and Consent

Users should be able to manage optional notification preferences where permitted.

DOC-06B `ME-ROOT` opens `NOTIFICATION-SETTINGS` directly for these controls. Inbox and Settings are sibling children under `NOTIFICATION-ROOT` and provide reciprocal navigation without repeated route-stack loops. Language and Theme are separate Me preferences and do not change notification-domain ownership.

Preference controls may include:

- push enabled or disabled;
- email enabled or disabled for optional messages;
- SMS enabled or disabled for optional messages;
- WhatsApp enabled or disabled where consented;
- optional reminders and service updates;
- rewards, referral, offers, product updates, and other optional messages.

Mandatory service messages may remain enabled even if optional channels are disabled.

WhatsApp, SMS, email, and marketing communications must follow consent, privacy, direct marketing, and provider requirements.

Required communication groups must be labelled `Required` and must not use misleading disableable toggles. Preference changes save immediately. On failure, restore the prior effective value and offer Retry. Account-level preferences and Inbox read/archive state should synchronize across approved devices; operating-system push permission remains device-specific.

`PRIVACY-DATA-CONTROLS` owns the underlying direct-marketing, personalization, and approved partner-data-use choice. `NOTIFICATION-SETTINGS` controls permitted delivery for communications supported by that choice; it must not create a second consent source of truth.

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

Do not repeatedly send the same message if the user already acted on the underlying owner-governed matter.

---

## 17. Operational Configuration Handoff

DOC-08 remains the owner of notification identity, event and channel requirements, recipient and template semantics, classification, preference, fallback, retry, delivery, delivery evidence, and communication approval requirements. The policy may identify parameters that are expressly permitted to be operationally configured, but it does not define the Admin dashboard, Admin UI, queue, permissions, configuration workflow, approval workflow, preview mechanism, provider mechanism, or other DOC-22 implementation behavior.

DOC-22 may execute only a workflow expressly authorized by DOC-08 or another applicable formal owner, using approved policy and source facts. DOC-22 must not invent or change notification policy, recipient eligibility, channel semantics, template meaning, fallback/retry requirements, preference rules, delivery requirements, approval requirements, or audit meaning. Source-preserving Important Notice and independently approved Offer communication remain owner-governed notification relationships; DOC-08 does not own their source truth or route presentation.

---

## 18. Delivery Logging and Retention

PayPlus should log:

- notification event ID;
- unique recipient-specific notification message ID;
- notification batch ID where applicable;
- source type and source event ID;
- source object type and ID;
- recipient user or role;
- channel;
- template ID and version;
- approved category;
- recipient-specific read/archive state;
- status/action-at-send snapshot where applicable;
- target route and object;
- correlation, causation, and deduplication references where applicable;
- per-channel delivery attempt ID and status;
- provider reference where available;
- created, scheduled, sent, read, and archived timestamps where applicable;
- failure reason where available;
- retry count;
- related source, Payment, Payout, receipt, dispute or account ID.
- related evidence or verification event ID where applicable.
- related campaign, offer, promotion quote, reward entitlement, instrument, redemption, or fulfilment ID where applicable.

Receipt, payment, account, tax, and audit records follow the accepted indefinite-retention direction subject to DOC-15 and Legal/Privacy confirmation of lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries. DOC-08 consumes DOC-15 access, masking and lawful handling requirements; notification delivery or account closure does not erase the underlying record within that lawful scope.

Detailed schema belongs in DOC-18.

---

## 19. Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-08-001 | Which notification provider will be used for email, SMS, push, and WhatsApp? | Engineering / Product | Open |
| OQ-08-002 | Do Legal, Product, and Compliance validate or amend the working mandatory, important, optional, admin-only, and disabled classifications in the event registry before launch? | Legal / Product / Compliance | Open; working classifications defined |
| OQ-08-003 | What exact templates are required for each notification event and channel? | Product / Design / Legal | Open |
| OQ-08-004 | What WhatsApp consent and opt-out flow is required? | Legal / Product | Open |
| OQ-08-005 | What SMS consent, fallback, and cost controls are required? | Product / Operations | Open |
| OQ-08-006 | What additional receipt or statement export formats, if any, are required beyond the MVP PDF? | Product / Finance | Open |
| OQ-08-007 | What notification delivery failure threshold should create an admin alert? | Operations / Engineering | Open |
| OQ-08-008 | Which approved-purpose access, masking, audit and privacy-request handling controls apply by notification-record class under the accepted indefinite-retention direction and its lawful-scope qualification? | Legal / Privacy | Open |
| OQ-08-009 | Which evidence verification events should notify users versus remain app status or admin-only dashboard tasks? | Product / Operations / Legal | Open |
| OQ-08-010 | Which DOC-13 promotion, coupon, voucher, referral, membership, miles, entitlement, fulfilment, and clawback events should notify users versus remain app status or admin-only tasks? | Product / Growth / Operations | Open |
| OQ-08-011 | Which action-alert schedule, channel mix, and final-action wording should apply separately to deliberate Payment Instructions and incomplete Checkout Workspaces, including split-card continuation and expiry cases? | Product / Payments / Operations | Open |
| OQ-08-012 | What notification wording and channel rules should apply when deferred payment quote, promotion, card eligibility, fee, or timing terms changed before submission? | Product / Growth / Payments | Open |
| OQ-08-013 | Which eligible Inbox-backed Important Notice notification families also use push, email, SMS, or WhatsApp? | Product / Operations / Legal | Open for channels; Home requires an existing eligible Inbox record |
| OQ-08-014 | Which Hot Offer communications, independently of Home placement, require notification consent, marketing consent, or Inbox delivery? | Product / Growth / Privacy | Open for communication; Home placement creates no notification or Inbox record |

---

## 20. Acceptance Criteria

DOC-08 is acceptable when:

- notification events are separated from system statuses;
- every notification event has a stable ID;
- recipient messages, batches, source events/objects, templates, destinations, and delivery attempts are separately traceable;
- Inbox category, presentation state, domain status, and action-required signals remain separate;
- `NOTIFICATION-ROOT`, Inbox, Detail, and Settings ownership and handoffs align with DOC-06B;
- read/archive actions do not change owning-domain state and contextual actions revalidate current state;
- default channels are defined without forcing every status to notify users;
- the boundary for parameters expressly permitted for operational configuration is defined without assigning Admin policy authority;
- mandatory, optional, disabled, and admin-only messages are distinguished;
- sensitive data rules are clear;
- receipt and statement rules are defined;
- evidence verification, correction, duplicate warning, and admin review message boundaries are defined;
- promotion, reward, coupon, voucher, referral, membership, miles, entitlement, and fulfilment message boundaries are defined;
- referral share actions do not create recipient notifications, while attribution, qualification, entitlement, claim, and issued-reward events route to their defined destinations;
- deliberate Payment Instruction and incomplete Checkout Workspace action-alert boundaries, deferred action, split-card remaining action, continuation expiry/closure, confirmed Payment, and downstream Payout message boundaries are defined without collapsing them into one status family;
- deferred payment quote or promotion change notification boundaries are defined without renumbering existing notification IDs;
- dashboard placement boundaries are defined so Important Notice / Action Required, Inbox, Hot Offer, and notification events remain separate but linkable surfaces;
- DOC-08 publishes existing Inbox-backed notification records and canonical source signals for DOC-06B consumption, creates no duplicate Home record, and leaves Home selection, ordering, dismissal, routing, and return behavior to DOC-06B;
- delivery logging and retention expectations are defined;
- detailed payment, payout, refund, dispute, and data-model logic is left to owning documents.

---

## 21. Version History
| Version | Date | Summary |
| --- | --- | --- |
| 2.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. |
| 1.2.1 | 2026-08-12 | Consolidated DOC-22 execution-only, notification-policy, Payment Obligation, timing and retention-boundary corrections while preserving delivery semantics. |
| 1.2.2 | 2026-08-12 | Applied the Founder-settled indefinite-retention rule to notification and receipt records and reframed the retention open question around access, masking and privacy-request controls. |
| 1.2.0 | 2026-08-12 | Clarified DOC-08 notification policy ownership and converted Admin dashboard/configuration wording to an expressly owner-permitted DOC-22 execution handoff while preserving fallback, retry, preference, channel, template, delivery and evidence semantics. |
| 1.1.0 | 2026-08-12 | Retired active Request and Receiving Info notification runtime and aligned DOC-08 with Payer-only communication ownership and governed one-way Individual notification eligibility. |
| 1.0.34 | 2026-08-05 | Defined the bounded HOME-ROOT Important Notice notification handoff by publishing the existing Inbox-backed record, notification identity, lifecycle, and source-owned selection/destination values while retaining Home presentation, ordering, dismissal, navigation, return, and reminder-window behavior in DOC-06B. |
| 1.0.33 | 2026-08-04 | Required every instruction-related notification to enter `NOTIFICATION-DETAIL`, revalidate current state and permission before exposing an owner-approved CTA to the DOC-09 Checkout Resolver, and prohibited notification content or delivery state from establishing current eligibility, authorization or payment result. |
| 1.0.32 | 2026-07-31 | Aligned notification references with Request-as-linkage and distinct Payment Instruction versus incomplete Checkout continuation contexts without defining new notification IDs. |
| 1.0.31 | 2026-07-29 | Separated AUTH-RECOVERY Outcomes and Resolution Strategies from notification events, classified reset-link email as controlled delivery, and mapped successful password reset to the existing mandatory account-security communication family. |
| 1.0.30 | 2026-07-28 | Aligned identity notifications and Home banners with the five-state model, added processing/success/action-required presentation behavior, and required security notification after payment-passcode Change or Reset. |
| 1.0.29 | 2026-07-28 | Replaced user-facing identity suspension wording with the approved `Failed` / `Update Required` labels and required internal suspension conditions to map through the canonical status-display matrix. |
| 1.0.28 | 2026-07-28 | Aligned account notifications with non-account registration attempts, restricted-account creation, full registration through `ACCOUNT-ACTIVATION`, and the DOC-07 in-flow authentication outcome/message boundary. |
| 1.0.27 | 2026-07-27 | Aligned account notifications with explicit email/Google/Apple login methods, first-password setup, provider link/unlink changes, and the restricted-account boundary for registration-started Inbox records. |
| 1.0.26 | 2026-07-27 | Defined the Notification route-family handoff, Inbox signal separation, SYS/SUP event domains, recipient-message and batch/source traceability, Settings/consent boundaries, cross-device preference behavior, and working-classification validation while preserving domain status ownership. |
| 1.0.25 | 2026-07-27 | Distinguished payer-created linking-request notifications from payee-created payment-request notifications and aligned Pay+ Request Payment direction without changing channel or delivery rules. |
| 1.0.24 | 2026-07-26 | Confirmed that personal bill/rent archive and restore do not create counterparty notifications and remain separate from domain notification events. |
| 1.0.23 | 2026-07-26 | Replaced the obsolete archived-evidence destination with `ARCHIVED-ROOT`, `ARCHIVED-BILLS-LIST`, and `ARCHIVED-DOCS-LIST` routing references without adding notification events. |
| 1.0.22 | 2026-07-26 | Assigned `NOTIFICATION-INBOX` as the stable Inbox destination while preserving DOC-08 notification-content ownership and the separate `NOTIFICATION-SETTINGS` preference route. |
| 1.0.21 | 2026-07-26 | Clarified that request notifications represent events and must not redefine request lifecycle, evidence, readiness, linked case, payment, payout, or archive states. |
| 1.0.20 | 2026-07-23 | Added `RECEIVING-INFO` notification routing, profile lifecycle events, linked destination-change notification, destination-attributable payout-failure behavior, privacy limits, and no-payee-approval/no-delay boundary. |
| 1.0.19 | 2026-07-22 | Added identity-verification, payment-passcode-settings, privacy-request, contact-change, and account-closure notification routing and events for the defined Me child routes. |
| 1.0.18 | 2026-07-22 | Aligned account, security, privacy, receiving-destination, and archived-evidence notification destinations with DOC-06B `ME-ROOT`; defined `NOTIFICATION-SETTINGS` as the Me preference route while keeping it separate from the Inbox. |
| 1.0.17 | 2026-07-21 | Aligned issued-reward notifications with canonical reward status labels and detail routing, and prohibited QR/code credentials, internal references, and internal risk reasons in notification content. |
| 1.0.16 | 2026-07-21 | Aligned Referral notifications with role-sensitive entitlement availability, canonical issued/held/reversed reward destinations, no direct notification-to-claim action, and no MVP claim-deadline reminder. |
| 1.0.15 | 2026-07-21 | Replaced invitation-delivery wording with referral attribution, qualification, entitlement, and issuance events; aligned notification destinations with the defined Referral route family and canonical issued-reward handoff. |
| 1.0.14 | 2026-07-17 | Aligned promotion, issued-reward, and referral notification destinations with stable DOC-06B product destinations without creating document-scoped entry-point IDs. |
| 1.0.13 | 2026-07-14 | Aligned receipt and statement notification destinations with DOC-06B shared PDF preview/direct-download behavior, confirmed PDF as the MVP format, made receipt request ID conditional, and limited statements to role-mixed financial activity. |
| 1.0.12 | 2026-07-13 | Aligned notification and direct receipt/proof download routing with DOC-06B `ACTIVITY-ROOT` expanded activity cards and `ACTIVITY-DETAIL` file actions, including unavailable-file and restricted-document behavior. |
| 1.0.11 | 2026-07-08 | Aligned receipt and statement notification routing with DOC-06B `RECEIPTS-ROOT`, `RECEIPT-DETAIL`, `STATEMENT-DETAIL`, and `ACTIVITY-DETAIL`; replaced correction-view wording with re-issue/replacement and version-retention rules. |
| 0.3.0 | 2026-06-01 | Aligned notification rules with DOC-13 by adding promotion and reward event domain, coupon/voucher, referral, membership, miles, entitlement, external voucher, reversal, and admin exception notifications. |
| 0.4.0 | 2026-06-02 | Aligned notification rules with DOC-15 by adding new-device, dormant-login, material-change, sensitive account/security messaging, and DOC-15 data-classification channel controls. |
| 0.5.0 | 2026-06-02 | Aligned notification rules with DOC-09 user payment instruction by adding deferred payment action, split-card remaining action, partial funding, expiry/cancellation, and partial payout notification events. |
| 0.6.0 | 2026-06-02 | Added stable PINS notification event for deferred payment quote, promotion, card eligibility, fee, or timing changes before submission. |
| 0.7.0 | 2026-06-04 | Aligned communication boundaries with DOC-06 dashboard baseline by defining Important Notice / Action Required, Featured / What's New / Hot Offer placement, Inbox linkage, and dashboard-versus-notification separation. |
| 0.8.0 | 2026-06-12 | Aligned request and evidence notification events with DOC-06 Bills tab rules for optional payee linking, no default payee-acceptance gate for payer-created payment, and post-setup evidence verification status. |
| 0.9.0 | 2026-06-15 | Added DOC-06 route-ID destination guidance for Bills tab action notifications, including evidence, reminder, linking, and Bills list routes. |
| 1.0.0 | 2026-06-17 | Aligned reminder notification routing with DOC-06 `BILLS-REMINDER-LIST` and `BILLS-REMINDER-DETAIL`, and added ordinary bill/rent reminder notification events separate from payment instruction reminders. |
| 1.0.1 | 2026-06-17 | Added notification routing guidance to use DOC-06C specific sub-route IDs where available instead of broad shorthand route labels. |
| 1.0.2 | 2026-06-18 | Aligned evidence notification route examples with DOC-06 `BILLS-EVIDENCE-DETAIL` and `BILLS-EVIDENCE-UPLOAD`. |
| 1.0.3 | 2026-06-24 | Aligned payee-side `Request` and `Remind Payer` routing with DOC-06C `BILLS-RECEIVE` and payer-side `BILLS-PAY` destinations. |
| 1.0.4 | 2026-06-25 | Clarified that `REQ` notifications cover request and party-linking lifecycle, not payment processing, and may route to Requests or linked Bills/rent contexts. |
| 1.0.5 | 2026-06-29 | Aligned request notifications with DOC-06B `REQUESTS-DETAIL` as the default request-specific destination. |
| 1.0.6 | 2026-07-02 | Aligned request notifications with DOC-06B `REQUESTS-NEW`, evidence-before-send delivery gate, request sharing, and WhatsApp deeplink routing to `REQUESTS-DETAIL`. |
| 1.0.7 | 2026-07-03 | Aligned request delivery and share-channel rules with finalized DOC-06B `REQUESTS-NEW`, including in-app preference, privacy-safe external content, authenticated `REQUESTS-DETAIL` routing, and pending-evidence notification suppression. |
| 1.0.8 | 2026-07-03 | Aligned payment instruction communication with DOC-06B `INSTRUCTIONS-ROOT` / `INSTRUCTIONS-DETAIL`, replacing ordinary reminder treatment with action-alert routing and keeping `PINS` separate from bill/rent reminders. |
| 1.0.9 | 2026-07-06 | Aligned notification routing with DOC-06B Payment Profile route by allowing card/profile action-required items to route to `PAYMENT-PROFILE-ROOT` or relevant card/profile screens without creating new notification IDs. |
| 1.0.10 | 2026-07-06 | Clarified receipt as a transaction confirmation record and statement as a periodic/account summary record, aligned with Activity and status-display terminology, and referenced the status display matrix for user-facing status labels. |
| 0.2.0 | 2026-05-30 | Aligned notification rules with DOC-12 by adding evidence verification events, correction prompts, duplicate/reused evidence warnings, admin evidence review tasks, and sensitive extracted-field messaging limits. |
| 0.1.0 | 2026-05-29 | Initial founder working baseline for notification event IDs, channel rules, receipts, statements, admin configurability, and delivery logging. |

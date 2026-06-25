# PayPlus Product Requirements

## Purpose

This standalone product requirement document describes the PayPlus MVP for an external prototype or MVP build trial. It removes internal document references and includes enough product, UX, payment, evidence, risk, data, and admin context for an AI-assisted builder to understand the intended application.

This document is not a final production specification. A production build still requires formal legal, compliance, payment partner, security, privacy, risk, operations, and testing review.

## 1. Product Overview

PayPlus is an evidence-backed card-funded payment app for eligible bills, fees, invoices, rent, and approved obligations.

The product lets:

- a payer create an obligation and pay it by card;
- an approved payee create an evidence-backed request and send it to a payer;
- PayPlus verify evidence, payment eligibility, payee/payout details, and risk conditions;
- the payer authorize payment;
- PayPlus route payout to the approved payee after upstream settlement and reconciliation.

PayPlus must not behave as a wallet, stored-value account, unrestricted peer-to-peer transfer app, remittance app, cashout product, lending product, cash advance product, or open marketplace for arbitrary money requests.

## 2. MVP Users And Roles

| Role | MVP Capability |
| --- | --- |
| Payer | Register, verify phone, create bills/rent/obligations, upload evidence, review autofill, pay by card, split card payment, create deferred payment instruction, view receipts and activity. |
| Payee | Register where enabled, create evidence-backed requests, send or resend request, remind payer where enabled, view request status, view payout/payment status. |
| Admin | Review users, evidence, payees, payouts, risk alerts, duplicate evidence, disputes, exceptions, configuration, and support cases. |
| System | Process statuses, notifications, OCR/autofill, duplicate detection, payment quotes, funding legs, payout readiness, audit events, and analytics events. |

## 3. MVP Functional Scope

The MVP should include:

- account registration and login;
- SMS phone verification;
- identity or business verification where required;
- new-device or dormant-login reauthentication where required;
- payment passcode before payment authorization;
- payer-created bill, fee, invoice, rent, and approved-obligation setup;
- payee-created payment request setup;
- evidence upload, photo capture, QR-assisted setup, and manual entry;
- AI/OCR evidence extraction and autofill where enabled;
- user review and correction of extracted fields;
- bill/rent verification and payment readiness status;
- payer-side `To Pay` route;
- payee-side `To Receive` route;
- bill/rent cards and detail pages;
- reminders;
- payment quote and checkout;
- single-card and multi-card payment;
- deferred payment instruction;
- payout status and reconciliation-ready state;
- receipts, statements, and proof of payment;
- notifications and in-app messages;
- promotion/coupon/voucher/referral framework where enabled;
- risk controls and admin review;
- audit trail and data events.

## 4. Out Of Scope / Prohibited

The MVP must not support:

- stored balance;
- user wallet;
- cashout;
- self-payment;
- unrestricted person-to-person transfer;
- remittance;
- lending or credit line;
- automatic recurring card charge without fresh approved model;
- payment without evidence or approved exception;
- unsupported instant QR payment without evidence and verification;
- unapproved user-level partner data sharing;
- credit scoring or insurance underwriting.

## 5. Main Navigation

The mobile app should use a task-first structure.

Recommended bottom navigation:

| Navigation Item | Purpose |
| --- | --- |
| Home | Dashboard, action items, shortcuts, recent activity, upcoming bills/rent, announcements, and featured offers. |
| Bills | Bill/rent/payment obligation management. |
| Pay+ | Center action button for common payment actions. |
| Offers | Offers, coupons, vouchers, promotions, card-linked benefits, referral, and rewards. |
| Me | Profile, account, security, preferences, records, and support access. |

The exact visual design is not finalized, but the route logic should be preserved.

## 6. Home Dashboard

Home should prioritize payment tasks, not marketing.

Recommended order:

1. Greeting and top icons for inbox/notifications and coupon or offer wallet.
2. Important Notice / Action Required section.
3. Shortcut grid.
4. Featured / What's New / Hot Offer carousel.
5. Upcoming Bills / Rent.
6. Recent Activity.
7. Optional promotions or offer preview.

### Shortcut Grid

MVP shortcuts:

- Requests;
- Instructions;
- Bills & Tenancies;
- Receipts;
- Reminders;
- Cards;
- Referral;
- More.

Shortcut defaults should be admin-configurable. Users should be able to reorder shortcuts, hide/show eligible shortcuts where allowed, and restore defaults.

### Important Notice / Action Required

This section may show:

- important updates;
- system messages;
- announcements;
- late handling of payer/payee requests;
- expiring tenancies;
- evidence issues;
- payment instruction reminders;
- account or security actions.

It should be swipeable, collapsible, and hidden when empty.

### Featured / Offers Carousel

This is a combined carousel for:

- featured function;
- What's New;
- hot offer;
- partner promotion;
- campaign announcement.

Placement, priority, expiry, targeting, and enable/disable status should be admin-controllable.

## 7. Pay+ Action Button

The center Pay+ button should open a slide-up action sheet.

Current working actions:

1. Pay a Bill / Fee.
2. Pay Rent.
3. Add Bill / Rent.
4. Continue Payment.
5. Request Payment.

Notes:

- Request Payment should appear for all users by default unless disabled or restricted.
- QR scan and upload are not standalone instant payment actions. They belong inside Add Bill / Rent or evidence capture.
- Continue Payment should help users resume incomplete split payments or deferred payment instructions.
- Final button order and exact wording may be refined later.

## 8. Bills Route

The Bills route is central to PayPlus.

It should always show two top views:

| View | Meaning |
| --- | --- |
| To Pay | Bills, rent, fees, and requests the user needs or expects to pay. |
| To Receive | Payee-side records, requests, and payout/receive-management items the user expects to receive. |

If a user currently has no payee-side records, To Receive should show an empty state, not disappear.

Important rule:

- A payer receiving a payee-created request belongs in To Pay, because the user is being asked to pay.
- To Receive is for the user acting as payee, landlord, biller, or recipient.
- Payee-side records must not show payer-side Pay buttons.

### Filters

To Pay filters:

- All;
- Action Required;
- Due Soon;
- Paid;
- Archived.

To Receive filters:

- All;
- Action Required;
- Due Soon;
- Received;
- Archived.

All excludes archived records. Archived shows only archived records.

## 9. Bill / Fee Cards

Bill/fee cards should show:

- category;
- bill name;
- latest amount;
- next due date;
- last payment date;
- payment readiness or status badge.

Payer-side card actions:

- Pay;
- View Details;
- Set Reminder;
- Update Detail when action is required.

Payee-side card actions:

- Request before payer acceptance;
- View Details;
- Remind Payer.

The Request button disappears after payer acceptance.

## 10. Rent / Tenancy Cards

Rent cards should show:

- category: Rent;
- rent or tenancy name;
- rent amount;
- rent period;
- next due date;
- last payment date;
- payment readiness or status badge.

Payer-side card actions:

- Pay;
- View Details;
- Set Reminder;
- Update Detail when action is required.

Payee-side card actions:

- Request before payer acceptance;
- View Details;
- Remind Payer.

## 11. Bill / Rent Detail Pages

Bill detail should show:

- category;
- bill name;
- payee information and payout/account information with masking where required;
- latest amount;
- next due date;
- last payment date;
- approved extracted bill/invoice fields where applicable;
- evidence status area;
- payment readiness/status badge.

Rent detail should show:

- category: Rent;
- rent/tenancy name;
- property address with masking where required;
- rent amount;
- rent period;
- last payment amount;
- last payment date;
- next due date;
- landlord/payee information and payout/account information with masking where required;
- approved extracted rental fields where applicable;
- evidence status area;
- payment readiness/status badge.

Payer-side detail actions:

- Pay;
- Activities;
- Reminder;
- Edit Detail;
- Archive.

Payee-side detail actions:

- Request before payer acceptance;
- Activities;
- Reminder;
- Edit Detail;
- Archive.

Evidence should not be a default primary action button. Evidence status should appear in the detail page. If evidence is missing, rejected, expired, or action-required, show a contextual action to view, upload, or update evidence.

## 12. Add Bill / Rent Flow

The add flow should support:

1. Select category: Bill / Fee or Rent.
2. Capture evidence or enter details manually where permitted.
3. Evidence capture methods:
   - upload file;
   - take photo;
   - scan QR code;
   - enter manually.
4. AI/OCR classification and extraction where enabled.
5. Autofill extracted fields.
6. User reviews and corrects fields.
7. Submit bill/rent setup and evidence for verification or review.
8. Create evidence status and payment readiness status.

Minimum bill/fee fields:

- bill name;
- amount;
- invoice date;
- due date;
- payee name where available;
- payee account name;
- bank name;
- bank account number.

Minimum rent fields:

- rent/tenancy name;
- property address;
- rent amount;
- rent period;
- due day/date;
- landlord/payee name where available;
- landlord/payee phone where available;
- account name;
- bank name;
- bank account number.

Evidence capture should support bills, invoices, tenancy agreements, rent demands, property notices, stamp duty documents, CR109, HKHA tenancy card, carpark invoice, contracts, and other approved supporting documents where applicable.

## 13. Evidence And Verification

Evidence is a supporting attachment/status layer linked to a bill/rent record. It is not a standalone user-facing object.

Normal operation should have one active evidence set per bill/rent record. Evidence updates create new versions; the newest accepted version becomes active. Previous or archived evidence should not appear in normal bill/rent UI but should remain retained under controlled records access.

Evidence statuses:

| Evidence Status | Meaning |
| --- | --- |
| Not Provided | Required evidence is missing. |
| Uploaded / Pending Processing | Evidence received but not processed. |
| Extraction Ready | AI/OCR extracted fields and user should review. |
| Pending Review | System or admin review required. |
| Accepted | Evidence accepted for payment readiness. |
| Rejected | Evidence rejected. |
| Update Required | Evidence or extracted data must be corrected. |
| Expired / No Longer Valid | Evidence can no longer support the obligation. |
| Archived | Evidence removed from normal UI but retained. |

Evidence status may affect payment readiness.

Payment readiness statuses should include:

- Action Required;
- Pending Verification;
- Ready To Pay;
- Under Review;
- Paid / Completed;
- Archived.

## 14. Activity And Receipts

Each bill/rent detail page should have an Activities view.

Activities should show user-facing payment activity plus limited request/evidence milestones for one selected bill/rent record.

Activity list entry should show:

- payment date;
- bill/rent name;
- recipient/payee name;
- amount;
- payment status;
- transfer/payout status where applicable.

Activity detail should show:

- payment date;
- bill/rent name;
- recipient/payee name;
- amount;
- payment status;
- transfer/payout status;
- payment reference number if any;
- receipt/proof download where available;
- link to payment detail where needed.

Activities should not show full internal audit logs, ordinary edit history, every evidence status change, or admin workflow history.

Receipts should include:

- receipt ID;
- payment/request ID;
- payer reference;
- payee reference;
- amount;
- fee;
- discount or promotion where applicable;
- payment method summary;
- payment date;
- payout/settlement status where appropriate;
- receipt/proof download.

Receipt must not imply payout is complete unless payout completion is confirmed.

## 15. Reminders

There are three different reminder concepts:

| Type | Meaning | Destination |
| --- | --- | --- |
| Normal due-date reminder | System/default reminder tied to bill/rent due date. | Bill/rent detail. |
| User manual reminder | User-created reminder for a bill/rent. | Reminder management or bill/rent detail. |
| Deferred payment instruction reminder | Reminder to return to incomplete payment flow. | Payment/checkout screen. |

Reminder management should behave like an alarm-style list:

- list reminders;
- add reminder;
- edit reminder;
- enable/disable reminder;
- delete multiple reminders through selection mode;
- link each reminder to a bill/rent/obligation ID;
- filter by bill/rent/due soon;
- rank by due date or amount.

When a custom reminder exists for the same bill/rent, it should override system default reminders for that item.

## 16. Payment / Checkout

Checkout should start from payer-side Pay actions, deferred payment instruction reminders, or continue-payment actions.

Checkout must show:

- selected bill/rent/obligation;
- payee;
- amount;
- evidence/payment readiness summary;
- service fee;
- discount, coupon, voucher, reward, or promotion quote where applicable;
- total charge;
- selected card/payment profile;
- split-card allocation where applicable;
- expected processing and payout timing where relevant;
- disclosure and authorization wording;
- pay now or deferred payment instruction option where enabled.

Payer must explicitly authorize payment before card funding.

Payment passcode should be required before payment authorization. Additional 2FA may be required depending on device, risk, amount, or partner rules. If payment amount is below a configurable threshold, external 2FA may be skipped where allowed by risk, partner, compliance, and security rules.

## 17. Multi-Card And Deferred Payment Instruction

Multi-card payment is MVP scope. The user may split one approved obligation across multiple cards up to a configurable limit.

The system must track each funding leg separately:

- card/payment profile;
- amount allocated;
- status;
- authorization result;
- settlement readiness;
- failure or retry state.

Deferred payment instruction is MVP scope.

It means the user has entered the payment flow and selected payment context, but one or more funding legs have not yet been submitted to the payment gateway.

Rules:

- user can pay immediately;
- user can schedule payment action within 7 days where authorization and payment rules allow;
- if the desired action date is more than 7 days away, the app should create a reminder instead of preserving payment authorization;
- for split payment, user may complete some cards first and continue later;
- incomplete split payment is not a completed payment;
- PayPlus may still transfer settlement-ready funded portions to payee according to payout rules;
- returning to a deferred instruction must revalidate quote, fee, promotion, card eligibility, and timing before submission.

Deferred instruction is not automatic recurring payment.

## 18. Payout And Reconciliation

Payout should occur only after upstream payment settlement and required payout readiness checks.

Expected baseline:

- upstream settlement is usually T+1 to T+3;
- payout may occur same day after funds are settled;
- cutoff rules apply;
- holidays and non-business days may delay settlement or payout;
- foreign-issued cards or offshore payment channels may follow platform or issuing-market settlement calendars.

Split payments from the same user for the same invoice/fee/rent within the same business day should be grouped into one payout to the payee where possible.

Normal payouts should support batch processing or future bank API processing.

Reconciliation should support bank feed API where available or manual upload of payout/bank records. The system must recognize successful individual payouts from bank feed or uploaded records.

## 19. Notifications And Communication

Notification channels may include:

- in-app notification;
- push notification;
- email;
- SMS;
- WhatsApp.

Every notification should have:

- event ID;
- trigger/status;
- recipient role;
- channel decision;
- template version;
- routing destination.

Not every status change requires a notification. For example, payment authorized may require a status update but not external notification. Payment completed usually requires a receipt or confirmation.

Sensitive details should be avoided in push, SMS, WhatsApp, and ordinary email. Link users back to authenticated app screens for details.

## 20. Offers, Promotions, Coupons, Vouchers, Referral

The MVP should preserve a promotion framework, even if many campaigns are launch-gated.

Supported concepts:

- internal coupon;
- voucher;
- discount code;
- service fee waiver or reduction;
- card-linked benefit;
- partner offer;
- external voucher or QR redemption;
- referral / member-get-member reward;
- membership or tier framework.

Checkout should show only eligible payment offers, not a full marketing page.

Offer detail should show:

- title;
- sponsor or partner;
- eligible category;
- payment method conditions;
- campaign period;
- coupon/voucher usage period if different;
- usage cap;
- spend cap;
- benefit type;
- terms and conditions;
- redemption method;
- expiry.

Card-linked offers should be detected through payment channel, card BIN, or saved token metadata where allowed.

## 21. Risk And Compliance Controls

Risk controls are first priority where there is:

- AML risk;
- obviously fraudulent case;
- chargeback risk;
- credit card fraud;
- fake or reused evidence;
- self-cashout or circular payment pattern;
- payer/payee collusion;
- suspicious payee;
- unsupported category;
- unusual split-card pattern;
- abnormal amount or velocity.

The system should support:

- configurable limits;
- duplicate evidence detection;
- payee/payout validation;
- relationship validation where required;
- risk review queue;
- manual review;
- payout hold;
- account restriction or suspension;
- audit logs.

Controls should be configurable and proportionate. Not every red flag should automatically block every case; some should route to review depending on category, amount, evidence, and risk score.

## 22. Privacy And Data Protection

PayPlus is data-rich and should lawfully capture useful data while applying classification, masking, role-based access, approved-purpose controls, retention, and auditability.

Sensitive data may include:

- identity data;
- phone/email;
- ID copy;
- business registration document;
- landlord/tenant information;
- bank account details;
- evidence documents;
- card token/payment profile metadata;
- transaction records;
- payout records;
- risk flags;
- support records.

UI should avoid unnecessary display of sensitive extracted fields. Some fields may be stored for verification, analytics, or audit, but not shown to ordinary users unless needed.

Expected record retention baseline is 7 years for payment, tax, audit, receipt, statement, and proof records, subject to final legal and privacy review.

## 23. Authentication And Security

MVP security expectations:

- email required for registration;
- phone required with SMS OTP verification;
- individual eKYC through provider where required;
- business KYB with business registration and owner ID where required;
- login by phone or login name;
- password with normal security standards;
- biometric login where device supports it;
- new-device 2FA;
- dormant-login reauthentication after long inactivity;
- payment passcode before payment;
- password reset by email deeplink;
- sensitive account changes require password, passcode, or 2FA confirmation.

Security design should support PCI and ISO-aligned controls. Raw card data should not be stored by PayPlus unless a future approved PCI scope permits it. Tokenization should be used for saved payment profiles.

## 24. Admin Dashboard

The admin dashboard should support:

- user review;
- payee review;
- KYC/KYB status;
- bill/rent/evidence review;
- OCR extraction review;
- duplicate evidence review;
- risk alerts;
- payment status;
- payout status;
- refund/dispute/chargeback case view;
- notification configuration;
- dashboard shortcut and placement configuration;
- promotion/campaign configuration;
- fee and limit configuration;
- module enable/disable controls;
- audit logs;
- support actions.

Admin actions must be permission-controlled and auditable.

## 25. Data And AI Readiness

PayPlus should be designed as a data-engine-ready payment platform.

The system should capture structured events for:

- registration;
- authentication;
- profile change;
- evidence upload;
- OCR extraction;
- user correction;
- evidence verification;
- duplicate detection;
- bill/rent creation;
- request sent;
- request accepted/rejected/expired;
- payment quote created;
- promotion quote applied;
- payment authorization;
- funding leg status;
- settlement readiness;
- payout;
- reconciliation;
- refund/dispute/chargeback;
- receipt;
- notification sent/opened;
- reminder created/fired/acted/ignored;
- admin review action.

Events should include:

- actor;
- timestamp;
- source object;
- related object IDs;
- status transition;
- reason code where applicable;
- privacy/data classification;
- audit linkage.

Future AI/model use should remain approved-purpose, privacy-controlled, auditable, and explainable. The MVP should not include unapproved credit scoring, insurance underwriting, offsite advertising activation, or unrestricted partner data sharing.

## 26. MVP Acceptance Criteria

The MVP is acceptable when:

- payer can register, verify phone, log in, and authenticate payment;
- payer can create a bill/rent/obligation record;
- payee can create a request where enabled;
- evidence can be uploaded or entered;
- OCR/autofill can be demonstrated where enabled;
- user can review and correct extracted fields;
- evidence status can affect payment readiness;
- payer can see payer-side items in To Pay;
- payee can see payee-side items in To Receive;
- payee-side records do not show payer-side Pay buttons;
- payer can review request/evidence/amount/payee before payment;
- checkout shows quote, fee, payment method, and authorization;
- split-card payment can be represented;
- deferred payment instruction can be represented;
- payment status can be tracked;
- payout/settlement status can be tracked;
- receipt/proof can be generated or shown;
- reminder and notification concepts work;
- admin can review evidence/risk/exceptions;
- prohibited wallet/cashout/P2P behavior is blocked.

## 27. Open Items For Prototype

The following may be configured as placeholders:

- exact acquirer/payment gateway;
- exact KYC/KYB provider;
- exact fee rates;
- exact split-card count limit;
- exact admin review thresholds;
- exact notification templates;
- exact promotion campaign mechanics;
- exact refund/dispute/chargeback policies;
- exact legal/regulatory wording.

These placeholders should not be hard-coded in a way that prevents later configuration.

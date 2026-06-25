# PayPlus Product Charter

## Purpose

This standalone charter describes PayPlus for an external prototype or MVP build trial. It is intended to explain the product clearly without requiring access to the full internal documentation set.

This brief is not legal, regulatory, tax, accounting, security, or compliance advice. Any production launch must still pass legal, compliance, payment partner, privacy, security, risk, and operations review.

## Product Summary

PayPlus is a controlled card-funded bill, fee, rent, invoice, and approved-obligation payment platform.

It allows eligible users to pay eligible real-world obligations by card, while PayPlus routes the approved payout to an approved payee through supported payout rails after payment, settlement, risk, and reconciliation checks.

PayPlus supports two controlled models:

| Model | Summary |
| --- | --- |
| Payer-created payment | A payer creates a bill, fee, invoice, rent, or approved obligation record, provides evidence or details, reviews the payment quote, authorizes card payment, and PayPlus routes payout after required checks. |
| Payee-created payment request | An approved payee creates an evidence-backed request and sends it to a payer. The payer must review and authorize before any card funding or payout occurs. |

## Product Positioning

PayPlus should be positioned as:

> A controlled payer-authorized card-funded payment service for eligible verified bills, fees, rent, invoices, and approved obligations.

Where payee-created requests are enabled, PayPlus may also be positioned as:

> A controlled payment request and bill payment service that allows approved payees to request payment for eligible verified obligations while the payer remains in control of payment authorization.

PayPlus is a payer-authorized push payment model. Even when a payee sends a request, the request is only an invitation to pay. Payment occurs only when the payer reviews and authorizes it.

## Prohibited Positioning

PayPlus must not be designed or described as:

- a wallet;
- a stored-value account;
- a cash advance or cash withdrawal product;
- a cashout product;
- an unrestricted peer-to-peer transfer app;
- a remittance product;
- a lending product;
- a bank account top-up product;
- a way to pay yourself by card;
- an open invoice marketplace;
- a way to request money from anyone for any reason;
- a product that auto-charges payers without payer authorization.

Any feature that appears to move PayPlus toward these models must be treated as high-risk and disabled unless separately assessed and approved.

## Target Users

| User Type | Description |
| --- | --- |
| Payer | A person or approved user who wants to pay eligible bills, fees, invoices, rent, domestic helper, driver, or personal service obligations by card. |
| Payee | A landlord, business, school, utility, service provider, property manager, or approved recipient who may receive payout or create payment requests where enabled. |
| Admin / Operations | Internal user who reviews evidence, payees, payouts, risk alerts, disputes, exceptions, and configuration. |
| Partner | Payment gateway, acquirer, payout bank, OCR provider, KYC provider, risk provider, campaign partner, card issuer, or commercial partner. |

## MVP Scope

The MVP should support:

- payer registration and login;
- payee registration and login where enabled;
- SMS phone verification;
- identity and business verification where required;
- payer-created bill, fee, invoice, rent, and approved-obligation records;
- payee-created payment requests;
- rent and tenancy payment flows;
- evidence upload, photo capture, QR-assisted setup, and manual entry;
- AI/OCR-assisted evidence reading and autofill where enabled;
- user review and correction of extracted evidence fields;
- payment quote before authorization;
- card-funded payment;
- multi-card split payment up to a configurable limit;
- deferred payment instruction for single-card and split-card payments;
- payout after upstream settlement;
- receipts, payment proof, and status history;
- reminders and notifications;
- promotion, coupon, voucher, card-linked benefit, and referral framework where enabled;
- risk, anti-cashout, duplicate evidence, payee validation, and manual review controls;
- admin dashboard controls for review, configuration, exceptions, and support.

## Core Product Principles

1. Every payment must be tied to a real evidence-backed obligation unless an approved exception applies.
2. Payer authorization is mandatory before charging a card.
3. Payer-created payments do not require payee acceptance by default if evidence, payee, payout, risk, and authorization gates pass.
4. Payee-created requests require payer review and payer acceptance before payment.
5. PayPlus must not allow unsupported open money transfer or self-cashout behavior.
6. Major modules must be independently enableable or disableable by configuration.
7. Sensitive data must be masked or restricted by role.
8. Key user, system, payment, evidence, risk, payout, communication, and admin actions must be auditable.
9. The app should be data-engine ready, with structured events and metadata suitable for future approved analytics and AI use.

## First Market Assumptions

The first intended launch market is Hong Kong.

Current assumptions:

- card payments are expected to be treated as bill payment or ordinary online card purchase, subject to acquirer confirmation;
- the acquirer and exact transaction classification remain to be confirmed;
- PayPlus expects to seek an appropriate or special merchant category treatment from the acquirer;
- payout is expected from PayPlus operating bank account after upstream settlement;
- Hong Kong payout rails may include FPS, cheque, and EPS, subject to final bank setup;
- upstream payment settlement is expected to be T+1 to T+3;
- payout should occur on the same day after funds are settled by the upstream counterparty where operationally possible;
- receipt, account, payment, statement, tax, and audit records are expected to be retained for 7 years, subject to final legal and privacy review.

## Success Criteria For Trial Prototype

A useful prototype should demonstrate:

- a clear user journey for payer-created payment;
- a clear user journey for payee-created request;
- bill/rent setup with evidence;
- OCR/autofill review concept;
- payer-side and payee-side route separation;
- checkout quote and payer authorization concept;
- split-card and deferred instruction concept;
- payout and receipt status concept;
- notification/reminder concept;
- admin review concept;
- visible controls that prevent wallet, cashout, and unrestricted transfer behavior.

## Open Decisions

The following do not need to block a prototype, but should remain configurable or clearly marked:

- final PSP/acquirer and transaction classification;
- exact launch category gates;
- final KYC/KYB provider and screening depth;
- final fee rates and fee allocation;
- final number of cards allowed for split payment;
- exact refund, cancellation, dispute, reversal, and chargeback policy;
- exact admin review thresholds;
- exact notification templates and provider;
- exact promotion, coupon, and partner campaign launch rules.

---
document_id: DOC-01
title: Product Overview & Positioning
version: 0.4.0
status: Draft
owner: Product Owner
reviewers:
  - Product Lead
  - Engineering Lead
  - Compliance Lead
  - Risk Lead
  - Commercial Lead
approvers:
  - Product Lead
  - Project Owner
last_updated: 2026-05-27
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-14 AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control Specification
  - DOC-15 Privacy, Data Protection & Record Retention Specification
---

# DOC-01 — Product Overview & Positioning

## 1. Purpose

This document defines the PayPlus product overview, positioning, MVP scope, product boundaries, key assumptions, risks, dependencies, success criteria, and open questions.

`DOC-01` is a foundation document.

It guides downstream product, payment, compliance, risk, security, engineering, commercial, and operational documentation.

This document does not define detailed product requirements, technical architecture, payment rules, legal conclusions, compliance controls, risk policies, security controls, or operating procedures. Those belong in downstream documents.

---

## 2. Product Summary

PayPlus is a controlled card-funded bill payment platform.

It enables eligible users to pay eligible real-world bills or approved payment obligations by card, while PayPlus or its payment partners route payment value to approved payees through supported payout or settlement methods.

PayPlus supports two controlled request models:

| Request Model | Summary |
| --- | --- |
| Payer-created request | A payer creates a bill payment request, provides bill details or evidence, reviews fees and disclosures, authorizes card payment, and PayPlus pays the approved payee. |
| Payee-created request | An approved payee creates a bill, invoice, fee, rent, or approved obligation request. The payer must review and explicitly authorize payment before any card funding or payout occurs. |

Payee-created requests are allowed only where the payee is onboarded or approved, the request is evidence-backed, the category is supported, risk controls pass, and the payer explicitly authorizes payment.

PayPlus should not be positioned as a wallet, stored-value account, cashout service, peer-to-peer transfer app, remittance service, payroll product, lending product, or open invoice marketplace unless separately assessed, approved, and documented.

---

## 3. Product Problem

Many users want to pay bills by card for convenience, liquidity management, rewards, recordkeeping, or payment flexibility.

However, many billers and payees do not directly accept cards.

PayPlus addresses this gap by allowing eligible card-funded payments to be routed to approved billers or payees, while maintaining evidence, authorization, payee validation, risk controls, reconciliation, and auditability.

Some legitimate payees, such as landlords, schools, utilities, billers, property managers, and service providers, may also need a controlled way to request payment from payers.

PayPlus supports this only where the request is evidence-backed, payer-authorized, and subject to PayPlus controls.

---

## 4. Product Positioning

PayPlus should be positioned as:

> A controlled card-funded bill payment service that enables eligible users to pay eligible verified bills or approved payment obligations through approved payment rails.

Where payee-created requests are enabled, PayPlus may also be positioned as:

> A controlled payment request and bill payment service that allows approved payees to request payment for eligible verified bills or obligations, while the payer remains in control of payment authorization.

Allowed positioning language may include:

- Card-funded bill payment.
- Bill payment facilitation.
- Pay eligible bills by card.
- Receive and pay eligible bill requests from approved payees.
- Approved payees can request payment for eligible bills, invoices, fees, or rent obligations.
- Pay rent or approved fees by card where supported and verified.
- Split or combine eligible card payments for an approved bill, where supported.
- Track bill payment status, receipts, and payment evidence.

Prohibited positioning language includes:

- Wallet.
- Stored value.
- Cash advance.
- Cash withdrawal.
- Cashout.
- Convert card limit to cash.
- Peer-to-peer transfer.
- Remittance.
- Send money freely to any account.
- Bank account top-up.
- Pay yourself by card.
- Turn invoices into cash.
- Open invoice marketplace.
- Request money from anyone for any reason.
- Auto-charge tenants or payers without authorization.

Final public language must be reviewed in `DOC-07 Content, Disclosure & User Authorization Specification`.

---

## 5. Target Users

Candidate target users include:

| User Type | Description |
| --- | --- |
| Payers | Individuals or approved users who want to pay eligible bills or approved obligations by card. |
| Payees | Approved billers, landlords, schools, utilities, service providers, property managers, or businesses that may receive payouts or create payment requests where enabled. |
| Admin and operations users | Internal users who review bills, payees, risk alerts, exceptions, payouts, refunds, disputes, and reconciliation. |
| Partners | PSPs, acquirers, payout providers, banks, bill payment aggregators, OCR providers, KYC/KYB providers, risk providers, or commercial partners. |

Final user segmentation belongs in `DOC-05 Master PRD & Feature Requirement Index`.

---

## 6. Core Use Cases

PayPlus supports the following core use cases, subject to approval and downstream specification.

| Use Case | Description |
| --- | --- |
| Payer-created bill payment | Payer uploads or enters bill details, PayPlus verifies eligibility and payee, payer authorizes card payment, and PayPlus pays the approved payee. |
| Payee-created payment request | Approved payee creates an eligible bill, invoice, fee, rent, or obligation request, payer reviews and authorizes payment, and PayPlus pays the approved payee. |
| Bill and evidence verification | PayPlus validates bill category, payee, amount, evidence, and eligibility before payout. |
| Card-funded payment | Payer funds the approved request using a supported card funding source. |
| Multi-card or multi-source payment | Payer may split or combine funding sources for one approved bill where supported. |
| Payout and settlement | PayPlus or its partner routes payment value to the approved payee through a supported method. |
| Refund, cancellation, rejection, query, and dispute handling | PayPlus supports controlled lifecycle actions before or after payment, depending on request state. |
| Receipt, status, and audit trail | PayPlus records request, funding, payout, reconciliation, receipt, and audit evidence. |
| Manual review and risk monitoring | PayPlus reviews higher-risk requests, payees, documents, categories, or transaction patterns. |

Detailed requirements belong in downstream documents, especially `DOC-05`, `DOC-09`, `DOC-10`, `DOC-11`, `DOC-12`, and `DOC-14`.

---

## 7. Candidate Bill Categories

Candidate bill or obligation categories include:

| Category | Notes |
| --- | --- |
| Utilities, telecom, and internet | Generally strong bill evidence and payee traceability. |
| Rent and property-related payments | Higher risk; requires landlord onboarding, tenancy or lease evidence where required, relationship validation, and anti-cashout controls. |
| Education fees | Requires institution validation and fee evidence. |
| Insurance premiums | Requires biller, policy, and payment obligation validation. |
| Taxes and government fees | Requires legal, partner, and category feasibility assessment. |
| Healthcare bills | Requires privacy-sensitive document handling and biller validation. |
| Loan or financing payments | May be restricted by partner, card network, or regulatory requirements. |
| Business invoices | Requires business validation, invoice evidence, payer acceptance, dispute handling, and anti-collusion controls. |

Candidate categories are not automatically approved.

Each category must be assessed under:

- `DOC-03 Regulatory, PSP & Acquirer Assessment`.
- `DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification`.
- `DOC-14 AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control Specification`.

Payee-created request support must be approved separately for each category.

---

## 8. MVP Definition

The MVP should be a narrow, controlled launch.

MVP should include:

| Area | MVP Treatment |
| --- | --- |
| User registration and authentication | In scope. |
| Basic user profile | In scope. |
| Payer-created bill payment | In scope. |
| Payee-created payment requests | In scope only if approved onboarding, evidence, payer authorization, risk, privacy, support, and reconciliation controls are ready. |
| Bill upload and manual bill entry | In scope. |
| Bill category eligibility checks | In scope. |
| Payee verification | In scope. |
| Card payment | In scope through approved PSP/acquirer. |
| Payment quote and fee disclosure | In scope. |
| Payout to approved payee | In scope through approved payout or settlement method. |
| Receipt and lifecycle notifications | In scope. |
| Refund and cancellation process | In scope at minimum viable process level. |
| Admin review console | In scope for manual review and exceptions. |
| Reconciliation reporting | In scope. |
| Risk monitoring | In scope. |
| OCR/document AI | Optional; may start as manual or assisted workflow. |
| Multi-card or multi-source payment | Candidate feature; may be deferred if partner, risk, or reconciliation complexity is high. |
| Promotion engine | Optional; should not block MVP unless commercially required. |
| Partner advertisements | Out of initial MVP unless separately approved. |

Recommended MVP categories should have:

- clear bill evidence;
- verified payee identity;
- lower cashout risk;
- clear payout path;
- PSP/acquirer acceptance;
- regulatory feasibility;
- operational review capacity;
- commercial viability.

Preferred MVP category candidates may include:

- utilities;
- telecom or internet bills;
- education fees;
- insurance premiums.

Higher-risk categories, including rent, business invoices, loan repayment, or tax payments, may require additional controls or later rollout.

If rent or landlord-created rent requests are included, PayPlus must require landlord onboarding, tenancy or lease evidence where required, payer-landlord relationship validation, duplicate request detection, anti-collusion controls, limits, and manual review for higher-risk cases.

---

## 9. Product Boundaries

### 9.1 In Scope

Candidate in-scope capabilities include:

- user registration and authentication;
- user profile and eligibility checks;
- payee onboarding and payee profile creation;
- payee type and capability permissioning;
- bill, invoice, fee, rent, or obligation request creation;
- payer-created requests;
- approved payee-created requests;
- request delivery or invitation to payer;
- payer review, acceptance, rejection, query, or dispute before authorization;
- bill and evidence capture;
- bill category classification;
- payee validation;
- payment quote and service fee calculation;
- card payment authorization and capture;
- multi-card or multi-source payment where supported;
- payout or settlement to approved payees;
- receipts and notifications;
- refund, cancellation, dispute, chargeback, reversal, and exception handling;
- promotion eligibility where approved;
- audit trail and reconciliation reporting;
- risk review and manual review workflows;
- compliance evidence retention.

### 9.2 Out of Scope Unless Separately Approved

PayPlus must not support the following unless separately assessed, approved, and documented:

- wallet balance;
- stored value;
- cash withdrawal;
- cash advance;
- card-to-bank-account cashout;
- bank account top-up;
- peer-to-peer transfers;
- unrestricted transfers to arbitrary recipients;
- crypto purchases or transfers;
- gambling or gaming top-ups;
- payroll disbursement;
- lending or credit issuance by PayPlus;
- bill payments without sufficient evidence;
- payout to unverified recipients;
- user-directed payout unrelated to a verified bill or approved obligation;
- open invoice or money-request marketplace;
- payee-created requests by unverified, blocked, restricted, or ineligible payees;
- payee-created requests for fake, inflated, circular, self-dealing, collusive, or unsupported obligations;
- automatic payer charging without explicit payer authorization;
- payee modification of material request terms after payer authorization without renewed payer review and authorization.

---

## 10. Product Principles

PayPlus should follow these principles:

| Principle | Meaning |
| --- | --- |
| Verified obligation first | Payment should be tied to a valid bill or approved payment obligation. |
| Approved payee only | Payout should go only to a verified or approved payee. |
| Payer authorization required | No payee-created request should result in funding or payout without explicit payer authorization. |
| Evidence parity | Payee-created requests should meet the same evidence standard as payer-created requests. |
| Request-origin clarity | Product should clearly show whether a request was payer-created, payee-created, admin-created, or system-created. |
| Permissioned payee capability | Payees should only create request types and categories they are approved to create. |
| No unrestricted cashout | Product must not enable card-funded cash withdrawal or unrestricted transfer. |
| Transparent pricing | Payers should see service fees and total cost before payment confirmation. |
| Traceable lifecycle | Each request should be traceable from creation through funding, payout, reconciliation, and receipt. |
| Risk-based controls | Higher-risk categories or behavior should trigger stronger review and limits. |
| Privacy-bound visibility | Payers and payees should only see information appropriate to their role and authorization level. |

---

## 11. High-Level Transaction Lifecycle

### 11.1 Payer-Created Request

1. Payer signs in.
2. Payer creates a bill payment request.
3. Payer enters bill details and/or uploads evidence.
4. PayPlus checks category, payee, evidence, limits, risk, and eligibility.
5. Payer reviews quote, fee, disclosures, timing, and terms.
6. Payer authorizes card payment.
7. PSP/acquirer authorizes and captures the payment.
8. PayPlus performs final payout readiness checks.
9. PayPlus or partner pays the approved payee.
10. PayPlus records funding, payout, reconciliation, receipt, and audit evidence.

### 11.2 Payee-Created Request

1. Payee completes onboarding and verification.
2. PayPlus grants approved request capabilities by payee type and category.
3. Payee creates an eligible bill, invoice, fee, rent, or obligation request.
4. Payee provides required details and evidence.
5. PayPlus checks payee permission, category, evidence, amount, payer identification, risk, and eligibility.
6. Request is delivered to payer, returned for correction, rejected, or routed to manual review.
7. Payer reviews request origin, payee identity, amount, evidence summary, service fee, total charge, timing, refund/cancellation terms, and PayPlus role.
8. Payer accepts and authorizes payment, rejects the request, raises a query, disputes the request, or lets it expire.
9. If authorized, PSP/acquirer authorizes and captures the card payment.
10. PayPlus performs final payout readiness checks.
11. PayPlus or partner pays the approved payee.
12. PayPlus records funding, payout, reconciliation, receipt, status updates, and audit evidence.

Detailed lifecycle, state machine, settlement, refund, and chargeback rules belong in `DOC-09`, `DOC-10`, and `DOC-11`.

---

## 12. Commercial Model Summary

Potential revenue sources include:

- payer-paid service fees;
- payee-paid request, collection, platform, subscription, onboarding, or payout fees;
- biller-paid or partner-paid fees;
- campaign-funded subsidies;
- partner-funded promotions;
- revenue share with approved partners.

Payer-created payments and payee-created requests may use different fee presentation models.

Potential models include:

- payer pays the service fee;
- payee absorbs the fee;
- fee is split between payer and payee;
- biller, merchant, or partner funds the fee;
- blended or promotional fee model.

The commercial model must account for:

- card processing fees;
- scheme and acquirer fees;
- PSP fees;
- payout and bank transfer fees;
- refund and chargeback losses;
- fraud losses;
- promotion costs;
- onboarding and verification costs;
- manual review and support costs;
- reconciliation and operations costs;
- compliance, security, and audit costs.

Detailed commercial assumptions belong in `DOC-02 Business Model & Unit Economics`.

---

## 13. Compliance and Risk Positioning

PayPlus must be assessed before launch against applicable legal, regulatory, card network, PSP, acquirer, banking, privacy, AML, consumer protection, and advertising requirements.

Key compliance and risk positioning assumptions:

- PayPlus is intended as a bill payment facilitation service.
- PayPlus may support payer-created and approved payee-created payment requests only where assessed and approved.
- PayPlus must avoid wallet and stored-value behavior unless separately approved.
- PayPlus must avoid unrestricted money transmission behavior unless licensed, exempt, sponsored, or otherwise approved.
- PayPlus must not enable card-funded cashout.
- PayPlus must maintain evidence that funded payments correspond to valid bills or approved obligations.
- PayPlus must maintain evidence that payout recipients are approved payees.
- PayPlus must require payer authorization before payment on payee-created requests.
- PayPlus must use approved payment partners and settlement models.
- PayPlus must maintain appropriate disclosures, consent, records, reconciliation evidence, and audit trail.

Key risk themes include:

- cashout risk;
- fake bill, fake invoice, or fake rent request risk;
- collusive payee or related-party abuse risk;
- payee-created request spam or harassment risk;
- payer confusion or misleading communication risk;
- chargeback, refund, and dispute risk;
- AML or suspicious activity risk;
- sensitive document handling risk;
- payer/payee privacy boundary risk;
- partner or card network rule violation risk;
- reconciliation failure risk;
- negative unit economics risk.

Detailed assessments and controls belong in `DOC-03`, `DOC-04`, `DOC-14`, and `DOC-15`.

---

## 14. Partner and Payment Model Summary

PayPlus may require the following partner types:

- PSP;
- acquirer;
- card processor;
- payment facilitator or sponsored merchant provider;
- payout provider;
- bank partner;
- bill payment aggregator;
- OCR/document AI provider;
- KYC/KYB provider;
- payee onboarding provider;
- fraud and risk provider;
- notification provider;
- cloud infrastructure provider;
- reconciliation or ledger provider;
- customer support tooling provider.

Partner assessment must consider:

- supported geographies;
- supported categories;
- card network rules;
- PSP and acquirer acceptance;
- payee-created request support;
- MCC treatment;
- payee role classification;
- settlement and payout flows;
- refund and chargeback handling;
- compliance obligations;
- data sharing and privacy obligations;
- security standards;
- fees, reserves, and reporting;
- reconciliation files;
- SLAs and operational support;
- contract restrictions;
- exit and migration risk.

Detailed partner assessment belongs in `DOC-03 Regulatory, PSP & Acquirer Assessment`.

---

## 15. Key Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
| --- | --- | --- | --- |
| `ASM-DOC01-001` | Users have demand for card-funded bill payment in at least one launch category. | Product / Commercial | Open |
| `ASM-DOC01-002` | At least one PSP/acquirer model can support the intended card-funded bill payment flow. | Product / Compliance / Payments | Open |
| `ASM-DOC01-003` | Eligible bill categories can be verified with acceptable evidence and operational effort. | Product / Operations / Risk | Open |
| `ASM-DOC01-004` | Payee verification can sufficiently reduce cashout and fraud risk. | Risk / Compliance / Operations | Open |
| `ASM-DOC01-005` | Unit economics can remain positive after card costs, payout costs, support, risk losses, and promotions. | Commercial / Finance | Open |
| `ASM-DOC01-006` | Manual review can support early MVP operations before full automation. | Operations | Open |
| `ASM-DOC01-007` | Payee-created requests can be supported without converting PayPlus into an unrestricted money request, cashout, wallet, or remittance product. | Product / Legal / Compliance | Open |
| `ASM-DOC01-008` | Approved payees can provide sufficient evidence for created requests, including tenancy or lease evidence for rent where required. | Product / Risk / Operations | Open |
| `ASM-DOC01-009` | Payers will understand and accept payee-created requests only after clear review, disclosure, and authorization flow. | Product / Design / Legal | Open |
| `ASM-DOC01-010` | Partner and payment data can support reliable reconciliation and audit requirements. | Finance / Engineering / Operations | Open |

---

## 16. Key Constraints

| Constraint ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| `CON-DOC01-001` | PayPlus must not operate as a wallet or stored-value product unless separately approved. | Limits product architecture and UX. | Product / Compliance |
| `CON-DOC01-002` | PayPlus must not enable unrestricted card-funded cashout. | Requires bill and payee verification. | Risk / Compliance |
| `CON-DOC01-003` | Supported categories must be approved by compliance and payment partners. | Limits category rollout. | Product / Compliance |
| `CON-DOC01-004` | Payout recipients must be verified or approved before payout. | Requires payee verification workflow. | Risk / Operations |
| `CON-DOC01-005` | PSP/acquirer capabilities may limit multi-card payments, payout timing, refunds, and chargebacks. | May constrain MVP scope. | Payments / Engineering |
| `CON-DOC01-006` | Sensitive documents and personal data must be handled under approved privacy controls. | Requires data handling and retention controls. | Privacy / Security |
| `CON-DOC01-007` | Transaction records must support audit and reconciliation. | Requires ledger and reporting design. | Finance / Engineering |
| `CON-DOC01-008` | Payee-created request capability must be disabled unless approved payee onboarding, evidence, risk, payout, privacy, support, and reconciliation controls are in place. | Requires feature gating and launch control. | Product / Compliance / Risk |
| `CON-DOC01-009` | Payee-created requests must not charge or bind the payer without explicit payer authorization. | Requires payer acceptance and authorization controls. | Product / Legal / Payments |
| `CON-DOC01-010` | Landlord-created rent requests require approved landlord onboarding and tenancy or lease evidence where required. | Requires rent-specific onboarding, evidence, and risk controls. | Product / Risk / Operations |

---

## 17. Key Dependencies

| Dependency ID | Dependency | Required For | Owner | Status |
| --- | --- | --- | --- | --- |
| `DEP-DOC01-001` | PSP/acquirer feasibility assessment. | Card payment acceptance. | Payments / Compliance | Open |
| `DEP-DOC01-002` | Payout provider or settlement partner selection. | Payee payment execution. | Payments / Operations | Open |
| `DEP-DOC01-003` | Regulatory assessment by launch jurisdiction. | Product launch approval. | Legal / Compliance | Open |
| `DEP-DOC01-004` | Bill category approval framework. | Category rollout. | Product / Risk / Compliance | Open |
| `DEP-DOC01-005` | Payee verification process. | Anti-cashout control. | Risk / Operations | Open |
| `DEP-DOC01-006` | Privacy and data retention model. | Bill document handling. | Privacy / Security | Open |
| `DEP-DOC01-007` | Risk rules and manual review workflow. | MVP launch controls. | Risk / Operations | Open |
| `DEP-DOC01-008` | Reconciliation and transaction ledger model. | Finance and audit readiness. | Finance / Engineering | Open |
| `DEP-DOC01-009` | Content and disclosure approval. | User-facing launch. | Product / Legal / Compliance | Open |
| `DEP-DOC01-010` | Payee onboarding and capability model. | Payee-created requests and payee payout. | Product / Compliance / Risk | Open |
| `DEP-DOC01-011` | Payer identification and invitation mechanism. | Payee-created request delivery to payer. | Product / Engineering / Privacy | Open |
| `DEP-DOC01-012` | Payer response and pre-authorization dispute workflow. | Payee-created request acceptance, rejection, query, and dispute. | Product / Operations / Legal | Open |

---

## 18. Key Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-DOC01-001` | Product is perceived or used as card-to-cash cashout. | Regulatory, partner, fraud, and financial loss risk. | Bill verification, payee verification, limits, monitoring, and communication controls. | Risk / Compliance | Open |
| `RISK-DOC01-002` | Unsupported legal or money transmission classification. | Launch delay, enforcement, partner rejection, or licensing requirement. | Jurisdiction and partner assessment before launch. | Legal / Compliance | Open |
| `RISK-DOC01-003` | PSP/acquirer rejects business model or category. | Product cannot process payments as designed. | Early partner due diligence and category review. | Payments / Commercial | Open |
| `RISK-DOC01-004` | Fake bills, fake invoices, fake rent requests, or collusive payees are used for abuse. | Fraud losses and cashout risk. | Evidence validation, payee verification, velocity limits, relationship checks, and manual review. | Risk / Operations | Open |
| `RISK-DOC01-005` | Chargeback or refund process creates financial loss. | Revenue leakage, disputes, and operational burden. | Define refund, chargeback, and evidence handling rules. | Payments / Risk / Operations | Open |
| `RISK-DOC01-006` | Multi-card funding increases complexity or partner risk. | Delayed MVP or higher reconciliation risk. | Defer unless clearly supported. | Product / Engineering / Payments | Open |
| `RISK-DOC01-007` | User disclosures are unclear or misleading. | User complaints, regulatory risk, and chargebacks. | Content and legal review before launch. | Product / Legal | Open |
| `RISK-DOC01-008` | Unit economics are negative after full cost allocation. | Unsustainable business model. | Model costs and minimum fee thresholds in `DOC-02`. | Commercial / Finance | Open |
| `RISK-DOC01-009` | Manual review operations do not scale. | Delays, errors, and user dissatisfaction. | Limit MVP volume and automate high-confidence checks over time. | Operations / Product | Open |
| `RISK-DOC01-010` | Sensitive bill documents are mishandled. | Privacy, security, and reputation risk. | Apply privacy, security, access, retention, and deletion controls. | Privacy / Security | Open |
| `RISK-DOC01-011` | Payer misunderstands payee-created request as mandatory, already paid, or automatically charged. | Complaints, disputes, trust loss, and consumer protection risk. | Clear request-origin messaging, explicit payer acceptance, and no auto-charge behavior. | Product / Legal | Open |
| `RISK-DOC01-012` | Payee sees sensitive payer payment, card, or risk information. | Privacy, security, and trust risk. | Role-based access, data minimization, and payee-safe status messaging. | Privacy / Security | Open |

---

## 19. Launch Readiness Themes

PayPlus should not launch until the following are sufficiently addressed:

- product scope is approved;
- launch categories are approved;
- product positioning is approved;
- PSP/acquirer model is approved;
- payout or settlement model is approved;
- regulatory and compliance assessment is completed for launch jurisdiction;
- risk and anti-cashout controls are defined;
- bill and payee verification process is defined;
- payee onboarding and capability controls are defined if payee-created requests are enabled;
- payer acceptance and authorization flow is defined if payee-created requests are enabled;
- rent evidence and landlord verification controls are defined if rent is enabled;
- privacy and data retention controls are defined;
- payer/payee data visibility boundaries are defined;
- security model is defined;
- payment, payout, refund, and reconciliation workflows are defined;
- user disclosures are approved;
- customer support and incident workflows are defined;
- MVP test cases and UAT results are acceptable;
- operational owners are assigned;
- evidence retention and audit trail requirements are defined.

Detailed launch gates belong in `DOC-04` and `DOC-20`.

---

## 20. Success Criteria

Candidate success criteria include:

| Metric | Description |
| --- | --- |
| Activated users | Users who complete registration and become eligible to submit or pay bill payments. |
| Onboarded payees | Payees approved to receive payouts or create requests where enabled. |
| Submitted requests | Number of bill payment or payment obligation requests created. |
| Payer-created requests | Number of requests created by payers. |
| Payee-created requests | Number of requests created by approved payees. |
| Payee request acceptance rate | Percentage of payee-created requests accepted by payers. |
| Payee request rejection/query/dispute rate | Percentage of payee-created requests rejected, queried, or disputed before authorization. |
| Approved requests | Number and percentage of requests approved after verification. |
| Completed payments | Number and value of successfully funded and paid bills. |
| Payment success rate | Percentage of card payments successfully authorized and captured. |
| Payout success rate | Percentage of payouts successfully completed to approved payees. |
| Manual review rate | Percentage of transactions requiring manual review. |
| Refund, cancellation, and chargeback rate | Percentage of transactions refunded, cancelled, or charged back. |
| Fraud loss rate | Fraud losses as a percentage of processed volume. |
| Payee-created request abuse rate | Rate of requests flagged for fake invoice, fake rent, duplicate, collusive, or spam behavior. |
| Contribution margin | Revenue after variable payment, payout, promotion, risk, support, onboarding, verification, and operations costs. |
| Complaint rate | Complaints per transaction, user, or payee. |
| Repeat usage rate | Percentage of users who submit or pay more than one approved bill payment. |

Metric definitions should be finalized in `DOC-18 Data Model, Transaction State & Audit Event Specification`.

---

## 21. Downstream Document Impact

`DOC-01` guides downstream documents as follows:

| Document | Impact |
| --- | --- |
| `DOC-02` | Validate service fee, payee fee, partner fee, promotion, onboarding, verification, support, and unit economics assumptions. |
| `DOC-03` | Assess regulatory, PSP, acquirer, category, payment rail, payee feasibility, payee-created request model, and request creator implications. |
| `DOC-04` | Define launch gates, compliance controls, payee onboarding controls, payer authorization controls, evidence, and approval workflow. |
| `DOC-05` | Convert candidate capabilities into prioritized PRD requirements. |
| `DOC-06` | Define payer, payee, admin, and service blueprint flows. |
| `DOC-07` | Define product language, request-origin language, disclosures, and payer authorization content. |
| `DOC-08` | Define lifecycle notifications, request invitation messages, status messaging, and receipt language. |
| `DOC-09` | Define payment request, request creator type, payer acceptance, card funding, settlement readiness, and payment state behavior. |
| `DOC-10` | Define payout execution, payee payout status, and reconciliation rules. |
| `DOC-11` | Define cancellation, request withdrawal, payer rejection, query, refund, dispute, chargeback, and reversal rules. |
| `DOC-12` | Define category eligibility, document AI/OCR, evidence validation, rent evidence, invoice evidence, payee onboarding, and payee verification. |
| `DOC-13` | Define promotion eligibility, reward handling, campaign rules, and funded offers. |
| `DOC-14` | Define AML, anti-cashout, fraud, velocity, payee-created request abuse, relationship risk, manual review, and risk controls. |
| `DOC-15` | Define privacy, payer/payee data visibility, sensitive document handling, retention, deletion, and data rights. |
| `DOC-16` | Define technical architecture aligned to product boundaries and controls. |
| `DOC-17` | Define API and third-party integration requirements. |
| `DOC-18` | Define data model, request creator type, payee-created request object, ledger, reporting, audit trail, and metric definitions. |
| `DOC-19` | Define security, tokenization, authentication, encryption, access control, and payer/payee RBAC requirements. |
| `DOC-20` | Define test coverage, UAT, launch checklist, and release readiness. |
| `DOC-21` | Define monitoring, support, payee onboarding operations, incident response, and operational runbook. |

---

## 22. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC01-001` | What is the initial launch country or jurisdiction? | Project Owner | Critical | Open |
| `OQ-DOC01-002` | Which bill categories are approved for MVP? | Product / Compliance / Risk | Critical | Open |
| `OQ-DOC01-003` | Which PSP/acquirer model will be used? | Payments / Commercial | Critical | Open |
| `OQ-DOC01-004` | Which payout or settlement partner will be used? | Payments / Operations | Critical | Open |
| `OQ-DOC01-005` | Will MVP support multi-card or multi-source payments, or defer them? | Product / Payments / Engineering | High | Open |
| `OQ-DOC01-006` | What KYC/KYB level is required for users, payees, and business users? | Legal / Compliance / Risk | High | Open |
| `OQ-DOC01-007` | What transaction limits should apply at MVP? | Risk / Compliance / Product | High | Open |
| `OQ-DOC01-008` | What service fee model will be used? | Commercial / Finance | High | Open |
| `OQ-DOC01-009` | What user disclosures are required before payment confirmation? | Product / Legal / Compliance | High | Open |
| `OQ-DOC01-010` | What evidence must be retained for each transaction? | Compliance / Privacy / Operations | High | Open |
| `OQ-DOC01-011` | Are payee-created payment requests included in MVP, pilot, or post-MVP scope? | Project Owner / Product / Compliance | Critical | Open |
| `OQ-DOC01-012` | Which payee types can create payment requests? | Product / Risk / Compliance | Critical | Open |
| `OQ-DOC01-013` | Is landlord-created rent request creation included in MVP or deferred? | Product / Legal / Risk | Critical | Open |
| `OQ-DOC01-014` | What evidence is required for landlord-created rent requests? | Product / Legal / Risk / Operations | Critical | Open |
| `OQ-DOC01-015` | How will a payee identify or invite a payer? | Product / Engineering / Privacy | High | Open |
| `OQ-DOC01-016` | What payer response options are supported for payee-created requests? | Product / Operations / Legal | High | Open |
| `OQ-DOC01-017` | What information from a payee-created request can be shown to the payer and payee? | Product / Privacy / Security | High | Open |
| `OQ-DOC01-018` | What monitoring is required to detect fake invoices, fake rent requests, related-party abuse, and payee-created request spam? | Risk / Compliance / Operations | Critical | Open |
| `OQ-DOC01-019` | Are recurring payee-created rent or invoice requests allowed, or must each request be individually created and authorized? | Product / Legal / Payments | High | Open |

---

## 23. Acceptance Criteria

`DOC-01` is acceptable when it clearly defines:

- PayPlus product summary;
- product problem;
- product positioning;
- target users;
- core use cases;
- candidate bill categories;
- MVP definition;
- product boundaries;
- product principles;
- high-level payer-created request lifecycle;
- high-level payee-created request lifecycle;
- commercial model summary;
- compliance and risk positioning;
- partner and payment model summary;
- key assumptions;
- key constraints;
- key dependencies;
- key risks;
- launch readiness themes;
- success criteria;
- downstream document impact;
- open questions.

This document should remain a concise foundation product overview and should not become a detailed PRD, legal memo, payment specification, risk policy, or technical architecture.

---

## 24. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of `DOC-01` Project Charter & Product Positioning. |
| `0.2.0` | `2026-05-26` | Product Documentation Team | Reframed as foundation charter, clarified product positioning, added product boundaries, candidate MVP scope, assumptions, constraints, dependencies, risks, launch readiness themes, downstream document impact, and standardized metadata and version history. |
| `0.3.0` | `2026-05-27` | Product Documentation Team | Updated charter to include controlled payee-created bill, invoice, fee, and rent payment request capability. Added payee onboarding, payer acceptance and authorization, evidence parity, landlord/rent evidence controls, request-origin positioning, additional risks, dependencies, success metrics, launch readiness themes, and downstream document impacts aligned to `DOC-05 v0.2.0`. |
| `0.4.0` | `2026-05-27` | Product Documentation Team | Simplified structure and language while preserving essential product positioning, MVP scope, payer-created and payee-created request models, boundaries, controls, risks, dependencies, open questions, and downstream impacts. |

---
document_id: DOC-14
title: AML, Anti-Cashout, Fraud & Dynamic Auth Risk Control Specification
version: 0.6.1
status: Founder Working Baseline
owner: Risk / Compliance
reviewers:
  - Product Lead
  - Compliance Lead
  - Risk Lead
  - Payments Lead
  - Operations Lead
  - Engineering Lead
  - Data Lead
  - Security Lead
approvers:
  - Project Owner
  - Compliance Lead
  - Risk Lead
last_updated: 2026-07-02
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-14 - AML, Anti-Cashout, Fraud & Dynamic Auth Risk Control Specification

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-14` |
| **Title** | AML, Anti-Cashout, Fraud & Dynamic Auth Risk Control Specification |
| **Version** | `0.6.1` |
| **Status** | Founder Working Baseline |
| **Owner** | Risk / Compliance |
| **Reviewers** | Product Lead<br>Compliance Lead<br>Risk Lead<br>Payments Lead<br>Operations Lead<br>Engineering Lead<br>Data Lead<br>Security Lead |
| **Approvers** | Project Owner<br>Compliance Lead<br>Risk Lead |
| **Last Updated** | `2026-07-02` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Request, Multi-Funding Source & Settlement<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This document defines the PayPlus MVP risk-control framework for AML, sanctions, anti-cashout, fraud, credit card fraud, chargeback exposure, suspicious refund behavior, payout risk, dynamic authentication, and manual review routing.

DOC-14 protects PayPlus from legal risk, fraud loss, card/payment loss, chargeback exposure, unsupported money movement, and operational abuse while avoiding unnecessarily strict rules that block legitimate bill, fee, rent, invoice, and approved-obligation payments.

This document is not a final AML policy, legal opinion, fraud model design, database schema, admin dashboard design, security architecture, or operations runbook.

---

## 2. Scope and Ownership

DOC-14 covers:

- risk-control principles;
- MVP critical risk controls;
- configurable review controls;
- optional or future enhanced controls;
- risk signal sources;
- risk decision actions;
- AML, sanctions, and KYC/KYB risk handling at product-rule level;
- anti-cashout and prohibited-flow controls;
- evidence, payment, payout, refund, chargeback, promotion, and referral abuse controls;
- dynamic authentication risk triggers;
- manual review and audit requirements.

Detailed specifications belong to:

| Topic | Owning Document |
| --- | --- |
| Product scope and prohibited positioning | DOC-01, DOC-05 |
| Regulatory and PSP/acquirer assessment | DOC-03 |
| Compliance control framework | DOC-04 |
| User journey and UX touchpoints | DOC-06 |
| User-facing wording and disclosure | DOC-07 |
| Notifications and user/admin communication | DOC-08 |
| Payment eligibility, multi-card funding, payment profiles, authorization, settlement readiness | DOC-09 |
| Payout readiness, payout hold, payout destination, reconciliation | DOC-10 |
| Refund, cancellation, dispute, chargeback, recovery | DOC-11 |
| Bill verification, OCR, evidence matching, duplicate evidence | DOC-12 |
| Promotion, coupon, voucher, referral, membership abuse boundaries | DOC-13 |
| Privacy, retention, masking, lawful use | DOC-15 |
| Third-party APIs and provider integration | DOC-17 |
| Data model, risk events, audit schema, reporting | DOC-18 |
| Security, tokenization, authentication, RBAC | DOC-19 |
| Monitoring, incidents, escalation, SOPs | DOC-21 |
| Admin dashboard queues, permissions, overrides, workflows | DOC-22 |

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Launch market | Hong Kong. |
| Product model | Evidence-backed, payer-authorized bill, fee, rent, invoice, domestic service, and approved-obligation payment platform. |
| MVP categories | Bill payments, fee payments, and rent/tenancy payments are MVP scope. Invoice and other approved obligations are MVP where evidence and category controls are enabled. |
| Prohibited model | PayPlus must not operate as a wallet, stored-value account, cashout product, remittance product, lending product, or unrestricted P2P transfer app. |
| Risk priority | AML/legal risk, obvious fraud, chargeback risk, credit card fraud, payout loss, and cashout risk are first-priority controls. |
| Risk strictness | Not every red flag should block a transaction. Risk signals must map to proportionate actions. |
| Risk engine | MVP should use explainable rules, reason codes, configurable thresholds, risk bands, manual review, and audit trails. Black-box ML is not MVP. |
| Future AI risk support | AI or model-assisted risk scoring, relationship graph analysis, suspicious-pattern detection, and narrative support may be future enhancements only after sufficient data, privacy review, model governance, monitoring, and human-review controls are defined. |
| Dynamic authentication | Extra authentication may be skipped below a configurable amount only where risk, security, partner, and compliance rules allow. Risk flags override the amount threshold. |

Unconfirmed thresholds, providers, sanctions scope, monitoring rules, and admin workflows should remain editable assumptions until confirmed.

---

## 4. Core Risk Principles

| Principle | Requirement |
| --- | --- |
| Proportionate control | Controls should reduce legal, fraud, payment, and loss risk without creating excessive false positives. |
| Evidence-backed payment | Payment must be linked to acceptable evidence or approved exception. |
| Payer authorization | Payment cannot proceed without payer authorization. |
| No cashout | PayPlus must block self-cashout, circular payment, fake obligation, and unsupported P2P patterns. |
| Explainability | Every risk decision must have reason codes and traceable signals. |
| Configurability | Thresholds, review triggers, category rules, and module enablement must be configurable. |
| Human review for sensitive cases | High-risk or ambiguous cases should route to admin/risk review instead of relying only on automation. |
| Auditability | Risk decisions, overrides, review outcomes, holds, releases, and escalations must be logged. |
| Privacy by design | Risk review should use necessary data only and must respect masking, access, and retention rules. |
| Model governance before automation | Future AI/model-assisted risk use should have approved purpose, permitted inputs, prohibited inputs, explainability, monitoring, human-review, and audit requirements before production use. |

---

## 5. Risk Decision Actions

Each risk signal should map to one or more approved actions.

| Action | Meaning |
| --- | --- |
| Allow | Proceed without extra action. |
| Warn | Show allowed user warning or internal warning. |
| User Clarification | Ask user to correct or provide additional information. |
| Step-Up | Require extra authentication, such as OTP, biometric, 3DS, PSP challenge, or PayPlus risk challenge. |
| Manual Review | Route to admin/risk queue before proceeding. |
| Payment Hold | Hold payment processing or retry. |
| Payout Hold | Block payout release pending review or resolution. |
| Reward Hold | Hold coupon, voucher, referral, membership, miles, or promotion entitlement. |
| Block | Stop the transaction, request, payout, refund, or action. |
| Suspend / Restrict | Restrict account, payee, payment profile, payout destination, or feature access. |
| Escalate | Escalate to Compliance, Risk, Legal, Payments, Finance, PSP/acquirer, or senior operations. |

Hard blocks should be reserved for prohibited, clearly fraudulent, legally restricted, partner-blocked, or materially unsafe activity.

---

## 6. MVP Critical Controls

The following controls are required for MVP because failure may create legal exposure, fraud loss, chargeback loss, payout loss, or prohibited product behavior.

| Control Area | MVP Requirement | Default Action |
| --- | --- | --- |
| AML / sanctions / prohibited user risk | Screen or assess users, payees, business owners, payout beneficiaries, and relevant parties according to approved onboarding rules. | Block, hold, or escalate based on severity. |
| Self-cashout / circular payment | Detect payer paying self, same-party payout, circular payer/payee behavior, or card-funded transfer disguised as bill/fee/rent. | Block clear cases; review ambiguous cases. |
| Fake bill / fake invoice / fake rent | Detect materially false, altered, unsupported, or fabricated evidence. | Review or block. |
| Credit card fraud / stolen card / card testing | Detect repeated declines, failed step-up, suspicious new cards, velocity, token/profile abuse, and issuer/PSP risk signals. | Step-up, block, suspend profile, or review. |
| Chargeback risk | Preserve authorization, evidence, communication, payment, payout, and risk records for defense; identify high-risk payees/users. | Payout hold, review, restrict, or escalate. |
| High-risk payout destination change | Detect new, changed, mismatched, or suspicious payout destinations. | Payout hold and review. |
| Refund-after-payout risk | Detect refund, reversal, dispute, or chargeback requests where payout has been or may be released. | Payout hold, recovery review, or escalation. |
| Duplicate/reused evidence in sensitive categories | Detect exact or highly similar evidence, especially tenancy/rent and high-value obligations. | Review by default; block only when clearly invalid or abusive. |
| Admin override abuse | Require permission, reason, evidence, and audit log for risk hold release, payout release, block override, or manual approval. | Enforce permission and audit. |

---

## 7. MVP Configurable Review Controls

The following controls should exist at MVP but should be configurable by category, amount, user type, payee type, risk tier, launch phase, and operations capacity.

| Control Area | Recommended Handling |
| --- | --- |
| Amount threshold review | Route high-value bill, fee, rent, invoice, or obligation payments to review where configured. |
| Low OCR/document confidence | Route to user correction or admin review depending on category and severity. |
| User-corrected value differs from extracted value | Review only where mismatch is material, repeated, or risk-sensitive. |
| New payee or first payout | Review depending on amount, category, payout rail, and payee type. |
| New or changed payment profile | Step-up or review depending on card, amount, velocity, and PSP/acquirer signals. |
| Multi-card use | Allow as MVP, but monitor excessive splits, repeated failures, unusual card combinations, and refund complexity. |
| High payment velocity | Review depending on amount, category, payer/payee history, and time window. |
| Foreign-issued card or offshore payment method | Monitor and apply partner, issuer, settlement, and holiday-calendar rules; do not block by default. |
| Promotion/referral abuse | Hold rewards or entitlement where suspicious; do not automatically block the payment unless fraud/cashout risk exists. |
| Payer/payee related-party indicators | Manual review unless clearly self-cashout or prohibited. |

These controls should generate reason codes and queue routing, not broad automatic rejections.

---

## 8. Optional or Future Enhanced Controls

The following controls are useful but should not be required for MVP launch unless a provider, partner, regulator, or internal risk decision makes them mandatory.

| Future Control | Notes |
| --- | --- |
| ML-based fraud scoring | Future enhancement after sufficient labeled data, approved feature inputs, explainability, monitoring, and review controls. |
| Advanced collusion graph analysis | Future network-risk capability; payer-payee, device, evidence, payout, and referral graph signals require privacy and legal review. |
| Behavioral biometrics | Provider-dependent and privacy-sensitive. |
| Advanced device fingerprint scoring | Optional provider-based enhancement. |
| Automated relationship inference | Should require privacy and legal review; marketing use of relationship inference is not approved by DOC-14. |
| Advanced merchant/category segmentation | Useful after category volume grows. |
| Promotion abuse analytics at scale | Future enhancement after DOC-13 usage data matures. |
| Automated suspicious-activity narrative generation | Future compliance operations support, not final legal reporting. |

---

## 9. Risk Signal Sources

Risk decisioning may consume signals from:

- KYC/KYB and sanctions screening;
- user account status and verification status;
- payee, landlord, business payee, and payout destination records;
- DOC-12 evidence verification outcome, duplicate indicator, mismatch indicator, confidence, user correction, and final evidence snapshot;
- DOC-09 payment instruction, funding leg, payment profile, token reference, card metadata, multi-card allocation, authorization, step-up result, failure, retry, partial funding, quote revalidation, and expiry history;
- DOC-10 payout readiness, destination change, payout hold, bank result, and reconciliation records;
- DOC-11 refund, dispute, chargeback, reversal, recovery, and write-off cases;
- DOC-13 campaign, offer, entitlement, reward, referral, coupon, voucher, membership, promotion quote reservation, and reversal records;
- device, session, login, authentication, and security events from DOC-19;
- support, complaint, escalation, and admin review history from DOC-21 and DOC-22.

Detailed event schema and data model belong in DOC-18.

Risk signals, scores, bands, rule triggers, same-party indicators, fraud flags, sanctions/AML results, review outcomes, and escalation notes are Risk and Compliance Data under DOC-15. DOC-18 should preserve classification metadata, sensitivity, displayability, masking, retention, approved purpose, access roles, audit requirements, and lineage to source data.

Future model features, graph signals, and AI-assisted risk outputs should also preserve model purpose, permitted inputs, prohibited inputs, reason codes, confidence where applicable, human-review requirement, monitoring owner, and audit linkage under DOC-18. Risk and compliance signals should not be reused for marketing, partner reporting, credit scoring, insurance underwriting, or external activation unless separately assessed and approved under DOC-15 and the relevant source documents.

---

## 10. AML, Sanctions, and KYC/KYB Controls

PayPlus must support AML and sanctions controls appropriate to its final legal, regulatory, PSP/acquirer, and operating model.

At product-rule level, the system should support:

- individual KYC status;
- business KYB status;
- beneficial owner or owner ID checks where required;
- sanctions/watchlist screening status where required;
- payee, landlord, business payee, and payout beneficiary review;
- account restriction or enhanced due diligence status;
- compliance escalation case status;
- audit trail for onboarding, review, and exceptions.

DOC-14 does not conclude whether PayPlus is subject to a specific licensing or AML regime. Final conclusions belong to legal, compliance, and DOC-03/DOC-04 assessment.

---

## 11. Anti-Cashout and Prohibited-Flow Controls

PayPlus must prevent payments from being used as card-to-bank cashout, unsupported P2P transfer, circular transfer, or disguised remittance.

Required controls include:

- detect payer and payee being the same person, same business, same bank account holder, or equivalent self-benefit pattern;
- detect tenant/landlord same-party or related-party risk where data is available;
- detect repeated payments to the same payee without credible evidence;
- detect fake invoice, fake rent, fake fee, or unsupported obligation patterns;
- detect payment followed by suspicious refund, reversal, or payout behavior;
- detect payee-created requests used to pressure or automate payment without payer review;
- require payer authorization before payment in all cases.

Clear self-cashout should be blocked. Ambiguous relationship or related-party cases should route to manual review unless policy defines a hard block.

---

## 12. Evidence and Obligation Fraud Controls

DOC-12 owns evidence extraction and verification. DOC-14 owns the risk meaning of those signals.

Evidence-related risk controls should evaluate:

- materially altered, cropped, inconsistent, or suspicious documents;
- missing mandatory evidence fields;
- low OCR/document AI confidence in material fields;
- large mismatch between extracted and user-entered amount, payee, payer, property, reference, or payment details;
- repeated material user corrections;
- duplicate or reused bill, invoice, tenancy, property, reference, amount, or payment details;
- payee or payout destination mismatch;
- same-party or related-party indicators;
- category mismatch.

Most evidence issues should first route to user clarification or admin review. Blocking should be reserved for unsupported, fabricated, prohibited, or clearly abusive evidence.

---

## 13. Rent, Bill, Fee, and Invoice Risk Treatment

Bill, fee, and rent/tenancy payments are MVP scope. Risk strictness should vary by category and potential loss impact.

| Category | Risk Treatment |
| --- | --- |
| Rent / tenancy | Sensitive and often higher value. Strong duplicate/reused evidence, landlord/payee, property, destination, same-party, and payout-hold controls are required. |
| Bill payments | Evidence and payee matching required. Lower-risk recurring bills may use lighter review if issuer/payee is trusted. |
| Fee payments | Evidence, payee, amount, and category validation required. Business or institution fees may use risk-based review. |
| Invoice payments | Business/payee validation, invoice duplicate detection, and payout destination checks required. |
| Domestic helper, driver, and personal service obligations | MVP scope where supported by acceptable evidence and enabled controls. Apply category controls, evidence rules, privacy visibility, limits, monitoring, and risk-based review. |

DOC-05 owns MVP scope. DOC-12 owns evidence fields and verification. DOC-22 owns review queues.

---

## 14. Payment and Dynamic Authentication Controls

DOC-09 owns payment authorization and step-up authentication rules. DOC-14 defines risk triggers that may require step-up.

Step-up may be required when:

- payment amount exceeds configured threshold;
- risk score or rule result is elevated;
- payment profile is new, changed, risky, or recently failed;
- deferred payment instruction is pending, expired, repeatedly incomplete, or materially changed;
- card attempt pattern suggests testing or stolen-card use;
- selected card is linked to card-fraud or PSP/acquirer warning;
- multi-card pattern is unusual or repeatedly failing;
- split-card funding is repeatedly incomplete or produces unusual partial payout patterns;
- device, login, session, or account behavior is suspicious;
- payee, category, or payout destination is high-risk;
- user attempts retry after repeated failure;
- promotion, coupon, referral, or reward abuse is suspected.

Extra authentication may be skipped below a configurable amount only when partner, security, compliance, and risk rules allow.

Payer authorization itself must never be skipped.

Deferred payment instruction and partial funded-portion payout should be risk-monitored. Risk rules may warn, remind, hold payout, require step-up, route to review, or block where patterns suggest cashout, collusion, card testing, promotion quota holding, card-linked benefit testing, fraud, chargeback risk, or unsupported obligation use. Ordinary incomplete user action should not be treated as fraud by default.

---

## 15. Payout Hold and Release Controls

DOC-10 owns payout execution and reconciliation. DOC-14 defines risk conditions that may hold or block payout.

Payout should be held when:

- payment is not settled or settlement-ready;
- evidence review, user clarification, or risk review is unresolved;
- payee, landlord, business payee, or payout destination is not approved;
- payout destination changed recently or mismatches evidence;
- refund, dispute, chargeback, reversal, or fraud case is open;
- duplicate payment or duplicate evidence is under review;
- chargeback exposure is elevated;
- admin, compliance, risk, legal, finance, PSP/acquirer, or bank review requires hold.

Payout release must require permission, reason code, evidence where applicable, and audit trail.

---

## 16. Refund, Chargeback, and Credit Card Fraud Controls

DOC-11 owns refund, cancellation, reversal, dispute, and chargeback operations. DOC-14 owns abuse and risk triggers.

Risk controls should detect:

- repeated refund requests;
- refund requests shortly after payout;
- refund or chargeback concentration by payer, payee, card, category, or evidence type;
- repeated card declines, failed step-up, or issuer/card-network warnings;
- chargeback after payee payout;
- payee patterns that create losses or repeated disputes;
- multi-card refund complexity used to obscure abuse;
- mismatch between original evidence and later refund/dispute claims.

High-risk cases may trigger payout hold, account restriction, payee suspension, recovery review, partner escalation, or compliance escalation.

---

## 17. Promotion, Referral, and Reward Abuse Controls

DOC-13 owns promotion logic. DOC-14 owns abuse controls.

Risk controls should address:

- fake accounts;
- self-referral;
- referral farming;
- coupon brute force;
- duplicate claims;
- card-linked offer gaming;
- multi-card promotion abuse;
- reward entitlement manipulation;
- refund or chargeback after reward issuance;
- external voucher resale or misuse;
- partner-funded campaign loss exposure.

Default action should usually be reward hold, entitlement hold, manual review, or clawback review. Payment blocking should apply only where payment fraud, cashout, AML, or prohibited-use risk exists.

---

## 18. Admin Review, Overrides, and Audit

Admin/risk workflows must support:

- review queue creation with risk reason codes;
- evidence, payment, payout, refund, chargeback, promotion, and account context;
- approve, reject, hold, release, block, suspend, escalate, or request additional information actions;
- permission-based override controls;
- mandatory reason and evidence for overrides;
- immutable audit trail;
- four-eye approval where configured for high-risk actions.

Detailed admin screens, permissions, queues, and workflows belong in DOC-22.

---

## 19. Monitoring and Reporting

PayPlus should monitor:

- risk review volume and aging;
- false-positive and false-negative indicators;
- blocked request/payment/payout count;
- payout hold amount and aging;
- chargeback rate and loss exposure;
- refund and dispute concentration;
- card decline and step-up failure rate;
- duplicate/reused evidence rate;
- self-cashout and related-party review rate;
- promotion/referral abuse cases;
- admin override count;
- risk decision outcomes by category, user type, payee type, and payment method.

Detailed dashboards, alerts, incidents, and escalation procedures belong in DOC-21 and DOC-22. Reporting data model belongs in DOC-18.

---

## 20. Configuration and Governance

Risk configuration should support:

- category enablement or disablement;
- risk rule enablement or disablement;
- amount thresholds;
- velocity thresholds;
- duplicate strictness;
- OCR confidence thresholds;
- mismatch thresholds;
- dynamic authentication thresholds;
- payout hold rules;
- review queue routing;
- reason codes;
- admin permissions;
- override approval requirements;
- effective dates and version history.

Risk-rule changes must be permissioned, logged, and reviewable. Critical rule changes should require approval before production use.

---

## 21. Open Questions

| ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-14-001 | What final KYC/KYB, sanctions, and screening provider scope applies to payer, payee, landlord, business payee, and business owner checks? | Compliance / Legal / Risk | High | Open |
| OQ-14-002 | What transaction amount thresholds trigger step-up, manual review, payout hold, or enhanced review by category? | Risk / Payments | High | Open |
| OQ-14-003 | Which same-party or related-party patterns are hard blocks versus manual-review triggers? | Risk / Compliance / Product | High | Open |
| OQ-14-004 | What chargeback rate, refund rate, decline rate, and dispute concentration thresholds trigger restriction or suspension? | Risk / Payments / Operations | High | Open |
| OQ-14-005 | What exact duplicate/reused evidence strictness applies to rent, bill, fee, invoice, and other approved categories? | Risk / Product / Operations | Medium | Open |
| OQ-14-006 | What risk-review SLA and escalation path applies for critical cases? | Operations / Risk | Medium | Open |
| OQ-14-007 | What suspicious activity escalation or reporting process is required under the final legal/regulatory assessment? | Compliance / Legal | High | Open |
| OQ-14-008 | What four-eye approval rules apply to payout release, risk hold release, block override, and account reinstatement? | Risk / Operations / Security | Medium | Open |
| OQ-14-009 | What risk thresholds should apply to repeated incomplete payment instructions, unusual split-card partial payout patterns, and selected transfer date changes? | Risk / Payments / Product | Medium | Open |
| OQ-14-010 | What thresholds should identify abusive deferred payment instruction patterns involving promotion reservation, quote revalidation, or card-linked benefit testing? | Risk / Growth / Payments | Medium | Open |
| OQ-14-011 | What model governance, feature registry, monitoring, explainability, and human-review requirements must exist before AI/model-assisted risk scoring is enabled? | Risk / Data / Privacy | High | Open |
| OQ-14-012 | Which payer-payee, evidence, payout, device, card, support, and promotion graph signals may be used for risk review, and which are prohibited from marketing or partner reporting? | Risk / Privacy / Legal | High | Open |

---

## 22. Acceptance Criteria

DOC-14 is acceptable when it clearly defines:

- MVP critical controls for AML, fraud, credit card fraud, chargeback risk, payout loss, and anti-cashout;
- configurable review controls that avoid over-strict operation;
- optional/future enhanced controls;
- future AI/model-assisted risk governance boundaries;
- risk signal sources and decision actions;
- bill, fee, rent, invoice, and approved-obligation risk treatment;
- dynamic authentication risk triggers;
- deferred payment instruction, incomplete split-card funding, and partial payout risk boundaries;
- payout hold and release controls;
- refund, chargeback, promotion, referral, and reward abuse boundaries;
- admin review, override, audit, monitoring, and configuration expectations;
- clear ownership boundaries with DOC-09, DOC-10, DOC-11, DOC-12, DOC-13, DOC-15, DOC-18, DOC-19, DOC-21, and DOC-22.

This document should remain a compact risk-control specification.

It should not become:

- final legal or AML policy;
- final fraud rulebook with production thresholds;
- PSP/acquirer operating manual;
- admin dashboard screen design;
- database schema;
- security architecture;
- operations SOP;
- customer-facing policy wording.

---

## 23. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | `2026-06-02` | Product Documentation Team | Initial founder working baseline for AML, anti-cashout, fraud, credit card fraud, chargeback risk, dynamic authentication, payout hold, configurable review controls, and risk-governance boundaries. |
| `0.2.0` | `2026-06-02` | Product Documentation Team | Aligned risk signals, scores, flags, review outcomes, escalation notes, and source lineage with DOC-15 data classification and DOC-18 metadata requirements. |
| `0.3.0` | `2026-06-02` | Product Documentation Team | Aligned risk controls with DOC-09 user payment instruction by adding deferred instruction, incomplete split-card funding, partial payout, selected transfer date, and repeated incomplete pattern risk boundaries. |
| `0.4.0` | `2026-06-02` | Product Documentation Team | Added quote revalidation, promotion reservation, quota-holding, and card-linked benefit testing as deferred payment instruction risk signals. |
| `0.5.0` | `2026-06-02` | Product Documentation Team | Aligned domestic helper, driver, and personal service risk treatment with confirmed evidence-backed MVP scope and configurable risk-based controls. |
| `0.6.0` | `2026-06-08` | Product Documentation Team | Added future AI/model-assisted risk governance boundaries, graph-signal controls, prohibited reuse of risk signals, and related open questions aligned with DOC-15 and DOC-18. |
| `0.6.1` | `2026-07-02` | Product Documentation Team | Aligned risk/admin action wording with DOC-06B request-route boundaries by using additional-information wording for operational review instead of request-route clarification actions. |

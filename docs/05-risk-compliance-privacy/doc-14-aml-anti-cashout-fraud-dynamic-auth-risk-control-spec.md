---
document_id: DOC-14
title: AML, Anti-Cashout, Fraud & Dynamic Auth Risk Control Specification
version: 1.0.2
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
last_updated: 2026-09-01
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
  - DOC-09 Payment Domain Architecture
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
| **Version** | `1.0.2` |
| **Status** | Founder Working Baseline |
| **Owner** | Risk / Compliance |
| **Reviewers** | Product Lead<br>Compliance Lead<br>Risk Lead<br>Payments Lead<br>Operations Lead<br>Engineering Lead<br>Data Lead<br>Security Lead |
| **Approvers** | Project Owner<br>Compliance Lead<br>Risk Lead |
| **Last Updated** | `2026-09-01` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

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
| Payment Obligation and Checkout eligibility, payable-capacity controls, multi-card Funding Allocation, payer authorization, Provider Submission, confirmed Payment, and Payment Application | DOC-09 |
| Payout readiness, payout hold, payout destination, reconciliation | DOC-10 |
| Refund, cancellation, dispute, chargeback, recovery | DOC-11 |
| Bill verification, OCR, evidence matching, duplicate evidence | DOC-12 |
| Promotion, coupon, voucher, referral, membership abuse boundaries | DOC-13 |
| Privacy, retention, masking, lawful use | DOC-15 |
| Third-party APIs and provider integration | DOC-17 |
| Business recording, explainability, history, lineage, audit meaning, and reporting obligations handoff | DOC-18 |
| Security, tokenization, authentication, RBAC | DOC-19 |
| Monitoring, incidents, escalation, SOPs | DOC-21 |
| Admin dashboard queues, permissions, overrides, workflows | DOC-22 |

---

## 3. Current Decision Baseline

PayPlus is Payer-only. Risk consumes the authoritative Bill/Rent source, applicable Evidence/verification outcomes, intended economic-Payee and destination facts, Payment and Payout context, and approved privacy/security inputs. A Payee is not required to be a User, and source-context facts must not be expressed as an application-level Payer–Payee relationship, linking capability, participant object, reciprocal runtime or reader.

Risk may block or condition the concrete owner-controlled product, Payment, Payout, refund, account or risk outcome to which it applies. Evidence status is not payment readiness. A label-only Company/Individual disagreement may remain asynchronous and nonblocking when all concrete owner gates pass. DOC-14 does not define Category eligibility, Evidence lifecycle, payment readiness, Payout mechanics, retention, representation, routes, Copy, or Admin permissions.

Request, Linking, To Receive, Receiving Info, Payee-user and production legacy data/runtime are retired. Archive is a non-erasing source visibility projection; DOC-10/11 decide applicable Payout/reconciliation/adjustment/case blockers, while detailed Restore, prior-version and Evidence-version presentation is deferred.

| Area | Baseline |
| --- | --- |
| Launch market | Hong Kong. |
| Product model | Bills use the approved C1/G1/G2 tiered Evidence, Declaration, Payment and Payout policy. Rent remains separate and always requires attached Evidence accepted before Payment. |
| MVP scope | The accepted twelve Bill Categories are the only launch Bill inventory; Rent is a separate journey. Examples such as invoices or domestic services create neither a Category nor eligibility. |
| Prohibited model | PayPlus must not operate as a wallet, stored-value account, cashout product, remittance product, lending product, or unrestricted P2P transfer app. |
| Risk priority | AML/legal risk, obvious fraud, chargeback risk, credit card fraud, payout loss, and cashout risk are first-priority controls. |
| Risk strictness | Not every red flag should block a transaction. Risk signals must map to proportionate actions. |
| Risk engine | MVP should use explainable owner-governed rules, reason categories, configurable thresholds, risk bands, manual review, and audit trails; black-box ML is not MVP. |
| Future AI risk support | AI or model-assisted risk scoring, relationship graph analysis, suspicious-pattern detection, and narrative support may be future enhancements only after sufficient data, privacy review, model governance, monitoring, and human-review controls are defined. |
| Dynamic authentication | Extra authentication may be skipped below an owner-permitted threshold only where risk, security, partner, and compliance rules allow. Risk flags override the amount threshold. |

Unconfirmed thresholds, providers, sanctions scope, monitoring rules, and owner-permitted Admin workflows should remain editable assumptions until confirmed.

---

## 4. Core Risk Principles

| Principle | Requirement |
| --- | --- |
| Proportionate control | Controls should reduce legal, fraud, payment, and loss risk without creating excessive false positives. |
| Evidence-informed risk | Risk consumes applicable DOC-12 verification outcomes; Evidence is not itself the source, obligation or Payment. |
| Payer authorization | Payment cannot proceed without payer authorization. |
| No cashout | PayPlus must block self-cashout, circular payment, fake obligation, and unsupported P2P patterns. |
| Explainability | Every risk decision must have reason codes and traceable signals. |
| Configurability | Thresholds, review triggers, category rules, and module enablement must be configurable only under risk-owner and applicable formal-owner governance. |
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
| Block | Stop the applicable transaction, Payout, refund or owner-governed action. |
| Suspend / Restrict | Restrict account, payee, payment profile, payout destination, or feature access. |
| Escalate | Escalate to Compliance, Risk, Legal, Payments, Finance, PSP/acquirer, or senior operations. |

Hard blocks should be reserved for prohibited, clearly fraudulent, legally restricted, partner-blocked, or materially unsafe activity.

---

## 6. MVP Critical Controls

The following controls are required for MVP because failure may create legal exposure, fraud loss, chargeback loss, payout loss, or prohibited product behavior.

| Control Area | MVP Requirement | Default Action |
| --- | --- | --- |
| AML / sanctions / prohibited user risk | Screen or assess users, payees, business owners, payout beneficiaries, and relevant parties according to approved onboarding rules. | Block, hold, or escalate based on severity. |
| Self-cashout / circular payment | Detect Payer self-payment, same-party Payout, circular source-context behaviour, or card-funded transfer disguised as Bill/Rent. | Block clear cases; review ambiguous cases. |
| Fake bill / fake invoice / fake rent | Detect materially false, altered, unsupported, or fabricated evidence. | Review or block. |
| Credit card fraud / stolen card / card testing | Detect repeated declines, failed step-up, suspicious new cards, velocity, token/profile abuse, and issuer/PSP risk signals. | Step-up, block, suspend profile, or review. |
| Chargeback risk | Preserve authorization, evidence, communication, payment, payout, and risk records for defense; identify high-risk payees/users. | Payout hold, review, restrict, or escalate. |
| High-risk payout destination change | Detect new, changed, mismatched, or suspicious payout destinations. | Payout hold and review. |
| Refund-after-payout risk | Detect refund, reversal, dispute, or chargeback requests where payout has been or may be released. | Payout hold, recovery review, or escalation. |
| Duplicate/reused evidence in sensitive categories | Detect exact or highly similar evidence, especially tenancy/rent and high-value obligations. | Review by default; block only when clearly invalid or abusive. |
| Admin override abuse | Require permission, reason, evidence, and audit log for risk hold release, payout release, block override, or manual approval. | Enforce permission and audit. |

---

## 7. MVP Configurable Review Controls

The following controls should exist at MVP but may be configurable by category, amount, user type, payee type, risk tier, launch phase, and operations capacity only under risk-owner and applicable formal-owner governance.

| Control Area | Recommended Handling |
| --- | --- |
| Amount threshold review | Route high-value bill, fee, rent, invoice, or obligation payments to review where configured. |
| Low OCR/document confidence | Route to user correction or admin review depending on category and severity. |
| User-corrected value differs from extracted value | Review only where mismatch is material, repeated, or risk-sensitive. |
| New payee or first payout | Review depending on amount, category, payout rail, and payee type. |
| Payer-entered destination facts | Assess applicable source-context destination facts through the responsible verification, risk and Payout owners; no Receiving Info library exists. |
| New or changed payment profile | Step-up or review depending on card, amount, velocity, and PSP/acquirer signals. |
| Multi-card use | Allow as MVP, but monitor excessive splits, repeated failures, unusual card combinations, and refund complexity. |
| High payment velocity | Review depending on amount, Category, source-context risk indicators and time window. |
| Foreign-issued card or offshore payment method | Monitor and apply partner, issuer, settlement, and holiday-calendar rules; do not block by default. |
| Promotion/referral abuse | Hold rewards or entitlement where suspicious; do not automatically block the payment unless fraud/cashout risk exists. |
| Same-party/related-party indicators | Manual review unless clearly self-cashout or prohibited; this does not create a Payer-Payee relationship runtime. |

These controls should generate reason codes and queue routing, not broad automatic rejections.

---

## 7A. Bills-only C1/G1/G2 and Tier Risk Controls

This section defines risk/control inputs and anti-abuse outcomes for the approved Bill policy. It does not make DOC-14 the exclusive C1 product owner, redefine DOC-09 Payment objects, define DOC-12 Evidence acceptance, select a technical G1 event or grant DOC-22 policy authority.

### 7A.1 C1 ownership handoff

C1 is the approved Category single-Payment threshold. C1 policy authority belongs to the designated product/risk owner; DOC-12 binds the applicable Category configuration, DOC-09 consumes it, and DOC-22 only executes approved configuration.

DOC-14 owns the applicable risk rationale, high-value signals and proportionate risk outcomes. The approved C1 layering already assigns policy authority to the designated product/risk owner; DOC-14 must not claim exclusive product authority. Exact Category values, permitted adjustments, configuration representation and operating change details remain later owner-defined inputs that block affected configuration, enablement and acceptance until supplied.

### 7A.2 G1 receiving-destination frequency

G1 permits a maximum of five independent user-initiated Bill payment progressions to the same receiving account/authoritative payout destination per Hong Kong calendar month.

- One progression/Checkout counts once despite split-card Funding Legs, Payment Attempts, confirmed Payments, retries, recovery or continuation.
- A genuinely new independent user-initiated progression counts again.
- G1 is a product-semantic anti-abuse invariant and is not bound here to Payer authorization, Provider Submission, Payment confirmation, a status, an event or a schema.
- The key is the receiving account/authoritative payout destination, not economic-Payee identity. The rule is a deliberate predictable, low-cost simplification and does not merge or redefine economic Payees.

When the current progression would exceed five, G1 elevates the Bill to Tier 2; it does not prohibit the Payment.

### 7A.3 G2 monthly value

G2 is HKD1,000,000 of Bill Payment value per verified Payer account per Hong Kong calendar month.

- Pre-check confirmed monthly Bill usage plus the proposed obligation-funded amount.
- Final usage is actual successfully confirmed obligation-funded value; payer fees are excluded.
- Failed, declined, cancelled-before-confirmation and proven duplicate attempts do not permanently consume capacity.
- Confirmed Payments remain in their original month after Refund or reversal.
- Only a confirmed duplicate/error correction restores capacity.
- Original Tier 3 classification is not retroactively downgraded when final confirmed value remains below the threshold.
- Concurrency must not permit multiple progressions to bypass the intended Tier, but the implementation mechanism remains with later owners.

### 7A.4 Highest-tier and approval outcomes

Retain every trigger reason but execute only the highest Tier workflow:

```text
G2 -> Tier 3
Otherwise C1 or G1 -> Tier 2
No trigger -> Tier 1
```

Tier 1 retains all applicable AML, sanctions, prohibited-purpose, anti-cashout, account-security, intended-Payee, destination, provider and Payer-authorization gates despite having no attached-Evidence requirement.

Tier 2 requires qualifying owner-approved official Bill Evidence presence before Payment; acceptance remains a Payout gate. Unresolved cases may use exception-only owner-approved human review. The Founder-updated framework may include owner-approved formal bills, fee notices, school payment notices, statements, invoices and formal historical receipts; examples do not establish acceptance. Communication-originated material cannot satisfy, substitute for or contribute to mandatory Evidence. DOC-12 owns Category-specific qualification.

Tier 3 requires qualifying official Bill Evidence and mandatory authorized approval before executable Payment progression. A prepared Checkout Workspace may exist but remains non-executable before approval. The normative authority boundary is defined: the applicable designated Product/Risk/Compliance/Security owner defines approval, while DOC-22 only executes the approved workflow and cannot create approval truth. Exact operating role assignment, workflow, dual-control/segregation implementation and evidence remain later owner inputs that block Tier 3 enablement, implementation and acceptance until supplied.

### 7A.5 Rent negative control

Bill C1/G1/G2, Tier 1/2/3 and official Bill Evidence rules do not apply to Rent. Rent always requires attached Evidence and the required Evidence acceptance before Payment. A Rent-specific Declaration cannot replace, waive, reduce or defer that requirement. Shared Payment, Payout, Save and Archive definitions must not weaken Rent.

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
- economic-Payee, landlord, business-payee and authoritative payout-destination/receiving-account facts without treating destination identity as Payee identity;
- DOC-12 evidence verification outcome, duplicate indicator, mismatch indicator, confidence, user correction, and final evidence snapshot;
- DOC-09 Bill Tier, C1/G1/G2 evaluation handoff, Payment Instruction, Checkout Workspace, Obligation Allocation, payable-capacity reservation, Funding Allocation Version, Funding Leg, Payment Attempt, Provider Submission, confirmed Payment, Payment Application, authorization, step-up result, failure, retry, continuation, closure, and expiry history;
- DOC-10 payout readiness, destination change, payout hold, bank result, and reconciliation records;
- DOC-11 refund, dispute, chargeback, reversal, recovery, and write-off cases;
- DOC-13 campaign, offer, entitlement, reward, referral, coupon, voucher, membership, promotion quote reservation, and reversal records;
- device, session, login, authentication, and other security-relevant facts governed by DOC-19 controls, with a bounded DOC-18 business-recording, explainability, history, lineage, and audit-meaning handoff;
- support, complaint, escalation, and admin review history from DOC-21 and DOC-22.

Risk signals, scores, bands, rule triggers, same-party indicators, fraud flags, sanctions/AML results, review outcomes, and escalation notes are Risk and Compliance Data under DOC-15. DOC-15 governs their classification, sensitivity, displayability, masking, Founder-approved indefinite-retention product and governance direction subject to lawful-scope confirmation, required exceptions, restricted data classes and prohibited sensitive-data boundaries, approved purpose, access roles, retention, and audit requirements. DOC-18 receives only a bounded business-recording, explainability, history, lineage, audit-meaning, and reporting-obligation handoff.

Future model features, graph signals, and AI-assisted risk outputs should retain model purpose, permitted inputs, prohibited inputs, explainability, human-review requirement, monitoring owner, audit linkage, reason categories, and confidence where applicable as future safeguards. DOC-18 receives only a bounded business-recording, explainability, history, lineage, audit-meaning, and reporting-obligation handoff. Risk and compliance signals should not be reused for marketing, partner reporting, credit scoring, insurance underwriting, or external activation unless separately assessed and approved under DOC-15 and the relevant source documents.

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

- detect Payer and economic-Payee source/destination facts indicating the same person, business, account holder or equivalent self-benefit pattern;
- detect tenant/landlord same-party or related-party risk where data is available;
- detect repeated independent Bill progressions to the same receiving account/authoritative payout destination under G1 without redefining economic-Payee identity;
- detect fabricated, altered or unsupported official Bill Evidence, fake Rent Evidence, fake fee, or unsupported obligation patterns;
- detect payment followed by suspicious refund, reversal, or payout behavior;
- prevent retired payee-created Request capability from being reintroduced;
- require payer authorization before payment in all cases.

Clear self-cashout should be blocked. Ambiguous relationship or related-party cases should route to manual review unless policy defines a hard block.

An authoritative Bill/Rent source with an applicable unresolved Evidence, destination, compliance, fraud, AML or risk outcome is subject to the owner-governed DOC-10/DOC-11 Archive blockers. Archive visibility never clears a hold, bypasses a restriction, hides a case or changes risk truth; detailed Restore/version presentation remains deferred.

---

## 12. Evidence and Obligation Fraud Controls

DOC-12 owns evidence extraction and verification. DOC-14 owns the risk meaning of those signals.

Evidence-related risk controls should evaluate, where Evidence exists or is required:

- materially altered, cropped, inconsistent, or suspicious documents;
- missing mandatory evidence fields;
- low OCR/document AI confidence in material fields;
- large mismatch between extracted and user-entered amount, payee, payer, property, reference, or payment details;
- repeated material user corrections;
- duplicate or reused bill, invoice, tenancy, property, reference, amount, or payment details;
- economic-Payee or payout-destination mismatch while preserving their separate meanings;
- same-party or related-party indicators;
- category mismatch.

For Tier 2/3, risk consumes only owner-approved official Bill Evidence qualification and DOC-12 outcomes; formal document examples do not establish acceptance. This is the risk-control handoff for the Founder-updated Evidence direction. WhatsApp or other communication-originated material cannot satisfy, substitute for or contribute to the mandatory Evidence requirement. Most Evidence issues should first route to user clarification or owner-approved review. Blocking should be reserved for unsupported, fabricated, prohibited or clearly abusive Evidence and applicable mandatory gates.

---

## 13. Rent, Bill, Fee, and Invoice Risk Treatment

Risk consumes the accepted twelve Bill Categories and the separate Rent journey. Category-specific risk criteria remain owner-governed and are not inferred from examples.

| Scope context | Risk Treatment |
| --- | --- |
| Separate Rent | Sensitive and often higher value. Attached Evidence and its required acceptance remain Payment gates. Bill limits/tiers do not apply; applicable tenancy/source-context, destination, duplicate/reuse, same-party and Payout-hold controls remain owner-governed. |
| Accepted Bill inventory | Apply the approved C1/G1/G2 Tier rule, Declaration boundary, owner-approved official Bill Evidence where Tier 2/3 requires it, and applicable intended-Payee, receiving-destination, amount and Category controls. |
| Other source examples | No example establishes a Bill Category or eligibility. Category-specific treatment remains owner-governed. |

DOC-05 owns MVP scope. DOC-12 owns Evidence fields and verification. DOC-22 executes only specifically owner-permitted workflow.

---

## 14. Payment and Dynamic Authentication Controls

DOC-09 owns payment authorization and step-up authentication rules. DOC-14 defines risk triggers that may require step-up.

The MVP baseline requires additional external or risk step-up at HK$3,000 or above. DOC-14 owns this threshold and the policy, governance and audit authority for any permitted adjustment. DOC-22 may execute only an already-authorized owner-permitted configuration workflow; no Admin dashboard, UI, queue, permission or implementation mechanism is selected here. Below HK$3,000, extra step-up may be skipped only where PSP/acquirer, card-network, regulatory, security, compliance, and risk rules allow. The payment passcode and payer authorization remain mandatory at every payment amount.

Step-up may also be required below the threshold when:

- payment amount exceeds an owner-approved threshold;
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

Partner, network, regulatory, or risk rules may require stronger authentication regardless of amount and cannot be overridden by the PayPlus threshold.

Deferred payment instruction and partial funded-portion payout should be risk-monitored. Risk rules may warn, remind, hold payout, require step-up, route to review, or block where patterns suggest cashout, collusion, card testing, promotion quota holding, card-linked benefit testing, fraud, chargeback risk, or unsupported obligation use. Ordinary incomplete user action should not be treated as fraud by default.

Consumer Receiving Info is retired. Payer-entered destination facts remain in the controlled Bill/Rent journey and are assessed by the applicable Evidence, intended-Payee, risk, Payout and authorization owners.

---

## 15. Payout Hold and Release Controls

DOC-10 owns payout execution and reconciliation. DOC-14 defines risk conditions that may hold or block payout.

Payout should be held when:

- payment is not settled or settlement-ready;
- Evidence required by the applicable Bill Tier or Rent rule remains unaccepted, or a separately owner-governed material Evidence clarification/risk review requires a hold;
- payee, landlord, business payee, or payout destination is not approved;
- payout destination changed recently or mismatches evidence;
- refund, dispute, chargeback, reversal, or fraud case is open;
- duplicate payment or duplicate evidence is under review;
- chargeback exposure is elevated;
- admin, compliance, risk, legal, finance, PSP/acquirer, or bank review requires hold.

For Bill Tier 2, qualifying Evidence presence may permit Payment while Evidence acceptance remains pending, but Payout must remain held until acceptance and every other release gate passes. For Bill Tier 3, Payout remains blocked until qualifying Evidence, authorized approval and every other release gate pass. Rent retains its existing Evidence-acceptance-before-Payment rule and subsequent Payout controls.

Payout release must require permission, reason code, evidence where applicable, and audit trail.

Risk handling consumes the authoritative source and applicable authorization-time destination snapshot. A later source change cannot rewrite immutable Payment/Payout facts; owner-governed revalidation and fresh authorization apply where DOC-09 requires them.

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

DOC-14 owns risk evaluation outcomes and required escalation. DOC-22 may execute only a specifically owner-permitted workflow/configuration and record approved operational evidence; it does not decide C1 authority or values, G1/G2 policy, Evidence truth, Tier 3 approval authority, Payment/Payout truth, privacy/retention, security proof, route access, or a generic disposition. Exact queues, permissions, controls, thresholds, actions and implementations remain with the applicable formal owner or later specialist work.

The applicable formal owner determines any review, hold, override, audit or access requirement. DOC-22 may execute an expressly owner-permitted workflow only; it does not receive generic queue, disposition, permission or policy authority.

---

## 19. Monitoring and Reporting

PayPlus should monitor:

- risk review volume and aging;
- false-positive and false-negative indicators;
- blocked payment/Payout count;
- payout hold amount and aging;
- chargeback rate and loss exposure;
- refund and dispute concentration;
- card decline and step-up failure rate;
- duplicate/reused evidence rate;
- self-cashout and related-party review rate;
- promotion/referral abuse cases;
- admin override count;
- risk decision outcomes by category, user type, payee type, and payment method.

Detailed dashboards, alerts, incidents, and escalation procedures belong in DOC-21 and DOC-22.

---

## 20. Configuration and Governance

DOC-14 defines risk outcomes and owner-level reason requirements. The applicable formal owner determines configuration, approval, threshold, hold, audit and change-control detail under the settled C1 and Tier 3 ownership boundaries. C1 values/operating details and Tier 3 role/workflow/segregation implementation remain explicit later configuration/enablement inputs. DOC-22 may execute only a specifically owner-permitted workflow/configuration; this document does not define queues, permissions, overrides, technical configuration or an implementation mechanism.

Legal, Compliance, PSP/acquirer, card-network, Finance, Privacy, Security and Operations confirmations remain explicit affected-path dependencies. They must be resolved before the affected path's enablement, implementation, acceptance, production readiness or launch. A professional conflict that changes product meaning or makes the approved model impossible must be handled under the canonical PayPlus Documentation Development Workflow.

---

## 21. Open Questions

| ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-14-001 | What final KYC/KYB, sanctions, and screening provider scope applies to payer, payee, landlord, business payee, and business owner checks? | Compliance / Legal / Risk | High | Open |
| OQ-14-002 | What additional thresholds trigger manual review, payout hold or enhanced review beyond the approved G1/G2 values and confirmed HK$3,000 additional-step-up baseline, and what owner-permitted governance applies? | Risk / Payments | High | Partially open; G1/G2 and step-up values are settled, other thresholds remain owner-governed |
| OQ-14-003 | Which same-party or related-party patterns are hard blocks versus manual-review triggers? | Risk / Compliance / Product | High | Open |
| OQ-14-004 | What chargeback rate, refund rate, decline rate, and dispute concentration thresholds trigger restriction or suspension? | Risk / Payments / Operations | High | Open |
| OQ-14-005 | What owner-governed duplicate/reused Evidence strictness applies to the accepted Bill inventory and separate Rent? | Risk / Product / Operations | Medium | Open |
| OQ-14-006 | What risk-review SLA and escalation path applies for critical cases? | Operations / Risk | Medium | Open |
| OQ-14-007 | What suspicious activity escalation or reporting process is required under the final legal/regulatory assessment? | Compliance / Legal | High | Open |
| OQ-14-008 | What four-eye approval rules apply to payout release, risk hold release, block override, and account reinstatement? | Risk / Operations / Security | Medium | Open |
| OQ-14-009 | What risk thresholds should apply to repeated abandoned or incomplete Checkout Workspaces, unusual split-card funding or payout patterns, and selected transfer-date changes? Deliberate Payment Instructions remain a separate risk context. | Risk / Payments / Product | Medium | Open |
| OQ-14-010 | What thresholds should identify abusive deferred payment instruction patterns involving promotion reservation, quote revalidation, or card-linked benefit testing? | Risk / Growth / Payments | Medium | Open |
| OQ-14-011 | What model governance, feature registry, monitoring, explainability, and human-review requirements must exist before AI/model-assisted risk scoring is enabled? | Risk / Data / Privacy | High | Open |
| OQ-14-012 | Which payer-payee, evidence, payout, device, card, support, and promotion graph signals may be used for risk review, and which are prohibited from marketing or partner reporting? | Risk / Privacy / Legal | High | Open |
| OQ-14-013 | What owner-governed name-normalization, third-party/company proof, review and destination-failure rules apply to source-context destination facts without overstating external account validation? | Risk / Compliance / Operations | High | Open |
| OQ-14-014 | What owner-approved C1 Category values, permitted adjustments, configuration representation and operating change details apply under the settled designated product/risk authority? | Product / Risk / Compliance | High | Open later configuration/enablement input; blocks affected configuration, enablement and acceptance until supplied |
| OQ-14-015 | Which operating role assignment, approval workflow and segregation controls implement the settled Tier 3 owner-authority boundary? | Product / Risk / Compliance / Security / Payments / Operations | High | Open later operating/security input; blocks Tier 3 enablement, implementation and acceptance until supplied |
| OQ-14-016 | What owner-approved normalization and technical representation preserve G1's same-receiving-account/authoritative-payout-destination product invariant across payout rails without redefining economic Payee? | Payments / Risk / Data / Engineering | High | Open; blocks implementation, not the approved product invariant |

---

## 22. Acceptance Criteria

DOC-14 is acceptable when it clearly defines:

- MVP critical controls for AML, fraud, credit card fraud, chargeback risk, payout loss, and anti-cashout;
- configurable review controls that avoid over-strict operation;
- optional/future enhanced controls;
- future AI/model-assisted risk governance boundaries;
- risk signal sources and decision actions;
- C1 layered ownership and risk-input boundaries without exclusive DOC-14 policy authority;
- product-semantic receiving-account/authoritative-payout-destination G1 and verified-Payer monthly-value G2 anti-abuse controls;
- highest-tier precedence and Tier 1/2/3 risk/approval boundaries;
- explicit Tier 3 authority/segregation blocker and DOC-22 execution-only treatment;
- the Bills-only scope and controlling Rent mandatory-Evidence negative rule;
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
| `1.0.2` | `2026-09-01` | Product Documentation Team | Clarified DOC-14 owner handoffs by removing or qualifying obsolete technical-representation allocations; risk-control meaning remains unchanged and technical representation remains deferred. |
| `1.0.1` | `2026-08-21` | Product Documentation Team | Aligned security-fact consumption with DOC-19 controls and DOC-18 representation while preserving DOC-14 ownership of risk triggers, thresholds, actions, and outcomes. |
| `1.0.0` | `2026-08-18` | Product Documentation Team | Implemented the material Bills-only risk model and fixed-seat compliance supplement; preserved settled ownership and Evidence traceability, neutralized active lifecycle-language ambiguity, qualified retention by lawful scope, and retained the exact G1 key and Tier 1 voluntary-Evidence Payout-hold boundary. |
| `0.7.2` | `2026-08-13` | Product Documentation Team | Clarified DOC-14 risk-threshold ownership and bounded DOC-22 to execution of expressly owner-permitted configuration without prescribing an Admin mechanism. |
| `0.7.1` | `2026-08-12` | Product Documentation Team | Applied the Founder-settled indefinite-retention treatment to risk and compliance data handoff without changing risk outcomes, thresholds or Admin execution boundaries. |
| `0.7.0` | `2026-08-12` | Product Documentation Team | Aligned active risk framing with Payer-only source context, separate Rent, retired Request/Receiving Info runtime, source Archive boundaries, and owner-permitted DOC-22 execution. |
| `0.6.5` | `2026-07-31` | Product Documentation Team | Aligned risk references with DOC-09 Payment Domain objects, execution boundaries, and distinct Payment Instruction versus incomplete Checkout contexts. |
| `0.6.4` | `2026-07-28` | Product Documentation Team | Set the admin-configurable HK$3,000 MVP baseline for additional external/risk step-up while preserving always-required payer authorization/passcode and mandatory partner, network, regulatory, and risk overrides. |
| `0.6.3` | `2026-07-26` | Product Documentation Team | Added obligation archive/restore blockers for unresolved risk, compliance, identity, recipient, evidence, and manual review without changing underlying risk states or holds. |
| `0.6.2` | `2026-07-23` | Product Documentation Team | Added Receiving Info identity/proof risk treatment, private-library boundary, destination-difference signal, snapshot immutability, and destination-attributable versus transient payout-failure handling. |
| `0.1.0` | `2026-06-02` | Product Documentation Team | Initial founder working baseline for AML, anti-cashout, fraud, credit card fraud, chargeback risk, dynamic authentication, payout hold, configurable review controls, and risk-governance boundaries. |
| `0.2.0` | `2026-06-02` | Product Documentation Team | Aligned risk signals, scores, flags, review outcomes, escalation notes, and source lineage with DOC-15 data classification and DOC-18 metadata requirements. |
| `0.3.0` | `2026-06-02` | Product Documentation Team | Aligned risk controls with DOC-09 user payment instruction by adding deferred instruction, incomplete split-card funding, partial payout, selected transfer date, and repeated incomplete pattern risk boundaries. |
| `0.4.0` | `2026-06-02` | Product Documentation Team | Added quote revalidation, promotion reservation, quota-holding, and card-linked benefit testing as deferred payment instruction risk signals. |
| `0.5.0` | `2026-06-02` | Product Documentation Team | Aligned domestic helper, driver, and personal service risk treatment with confirmed evidence-backed MVP scope and configurable risk-based controls. |
| `0.6.0` | `2026-06-08` | Product Documentation Team | Added future AI/model-assisted risk governance boundaries, graph-signal controls, prohibited reuse of risk signals, and related open questions aligned with DOC-15 and DOC-18. |
| `0.6.1` | `2026-07-02` | Product Documentation Team | Aligned risk/admin action wording with DOC-06B request-route boundaries by using additional-information wording for operational review instead of request-route clarification actions. |

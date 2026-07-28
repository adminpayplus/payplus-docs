# PayPlus Controlled Glossary

Status: Working alignment reference

Owner: Product / Documentation Owner

Last updated: 2026-07-29
Classification: Internal

This glossary defines approved PayPlus terminology. It does not replace the owning documents. When a definition changes, update the primary owner first and then this glossary.

## Product and Actor Terms

| Term | Canonical Definition | Primary Owner |
| --- | --- | --- |
| PayPlus | A controlled application for evidence-backed bill, fee, rent, tenancy, and other approved-obligation payments. It is not a wallet, stored-value account, cashout, remittance, lending, or unrestricted P2P product. | DOC-01 / DOC-05 |
| Payer | The user who reviews the payment context and gives the final payment authorization. | DOC-05 / DOC-06A |
| Payee | The person or business intended to receive a payout. A payee may or may not be a PayPlus user. | DOC-05 / DOC-10 |
| Linked Counterparty | A payer or payee user connected to an accepted obligation context through an approved user or operational action. Linking creates permitted visibility/communication, not payment authorization. | DOC-06A / DOC-06C |
| Non-Member Payee | A payee without a PayPlus account. A payer may still create and pay a valid evidence-backed obligation to the designated destination where all gates pass. | DOC-05 / DOC-10 |

## Obligation, Evidence, and Request Terms

| Term | Canonical Definition | Primary Owner |
| --- | --- | --- |
| Obligation | A real-world bill, fee, rent, tenancy-linked payment, invoice, or other approved amount that a payer intends or is required to pay. | DOC-05 / DOC-06C |
| Bill / Fee Record | A user-facing obligation record for a bill, invoice, fee, or approved non-rent payment purpose. | DOC-06C |
| Rent / Tenancy Record | A user-facing obligation record for rent supported by tenancy, rental, or other approved relationship evidence. | DOC-06C |
| Evidence | A document or approved source proving or supporting an obligation. Evidence is not itself an obligation, request, or financial activity. | DOC-12 / DOC-06C |
| Evidence Set | The current supporting evidence linked to one obligation, with retained prior versions where accepted updates occur. | DOC-06C / DOC-12 |
| Evidence Status | The lifecycle or review condition of evidence, separate from bill/rent payment readiness. | DOC-12 / DOC-06C |
| Previous Evidence Version | A retained, read-only evidence version superseded by an accepted newer version. It cannot be restored or promoted over the newer version. | DOC-06C / DOC-12 |
| Payment Readiness | The user-facing condition showing whether an obligation is ready to pay, needs action, or remains under review. Evidence status may affect readiness but is not the same status. | DOC-06C |
| Request | A payer-created or payee-created acceptance/linking request for an evidence-backed obligation context. A request is not a payment and does not authorize funds movement. | DOC-06A / DOC-06B |
| Payee-Created Request | A request from a payee asking a payer to accept an evidence-backed obligation. Payer acceptance is required before payment can proceed from that request. | DOC-05 / DOC-06A |
| Payer-Created Linking Request | An optional invitation asking a payee to link to a payer-created obligation for shared visibility and communication. The payer-created payment does not require payee acceptance by default where all gates pass. | DOC-06A / DOC-06B |
| Request Lifecycle State | The canonical condition of a request: `Draft`, `Pending Evidence Verification`, `Pending Receiver Action`, `Accepted`, `Rejected`, `Expired`, or `Cancelled`. While receiver action is pending, the sender sees `Reviewing` and the receiver sees `Awaiting`. | DOC-06A / DOC-06B |
| Request Event | An occurrence such as sent, viewed, reminded, or shared. An event is not automatically a request status. | DOC-06A / DOC-18 |
| Participant Linking | User-initiated, user-accepted, or approved operational connection of parties to an obligation. Automatic user-to-user matching is not allowed as a product assumption. | DOC-06C / DOC-15 |

## Payment, Funding, and Payout Terms

| Term | Canonical Definition | Primary Owner |
| --- | --- | --- |
| Payment | The payer-authorized funding transaction for an eligible evidence-backed obligation. | DOC-09 |
| Payment Instruction | A pending pay-later setup or incomplete payment that has not reached full payment completion. It is not every immediate payment and is separate from an ordinary bill/rent reminder. | DOC-09 / DOC-06B |
| Reminder | A user- or system-configured alert linked to a bill/rent/tenancy obligation. It does not itself create or authorize a payment. | DOC-06C / DOC-08 |
| Tokenized Card | A card represented by a PSP-permitted token/reference and masked metadata. PayPlus does not store or reveal full PAN or CVV. | DOC-09 / DOC-19 |
| Payment Profile | A payer-owned reusable split-card allocation profile. It stores card ratios, not wallet value, and supports up to 6 cards for MVP. | DOC-06B / DOC-09 |
| Funding Leg | One separately authorized card-funded part of a split-card payment. | DOC-09 |
| Split-Card Payment | One obligation payment funded through sequential authorization of multiple card funding legs, subject to an MVP maximum of 6 cards. | DOC-09 |
| Payment Quote | The current calculated payment amount, fee, promotion effect, and payable total requiring payer review before authorization. | DOC-09 / DOC-13 |
| Settlement Ready | An internal/domain condition indicating received funds meet the rules for payout preparation. It is not a generic user-facing payment label. | DOC-09 / DOC-10 |
| Receiving Info | A payee's private reusable library of receiving-information profiles. It is optional and not the sole payout source of truth. | DOC-06B / DOC-10 |
| Receiving Info Profile | One user-linked, versioned, reusable bank/FPS/cheque/EPS destination profile with readiness and proof metadata where required. | DOC-06B / DOC-10 |
| Destination Snapshot | The immutable version of receiving information selected or entered for a request, obligation, payment, or payout context. Later profile edits must not mutate it. | DOC-09 / DOC-10 / DOC-18 |
| Payout | PayPlus's transfer of settlement-ready funds to the designated payee destination. | DOC-10 |
| Payout Rail | The operational method used for payout. FPS, cheque, and EPS are accepted Hong Kong rails, subject to operating-bank support and enablement. | DOC-10 |
| Reconciliation | Matching payment, settlement, payout, bank, batch/API, return, and exception records to confirm financial completeness and identify differences. | DOC-10 |

## Records and Status Terms

| Term | Canonical Definition | Primary Owner |
| --- | --- | --- |
| Activity | A user-facing event or transaction lifecycle view. Global Activity is account-level; Bills Activity is limited to payment-related events for one obligation. | DOC-06B / DOC-06C |
| Bills Activity | Payment, payout/transfer, failure, return, refund, and reversal activity linked to one bill/rent/tenancy obligation. It excludes request and evidence lifecycle history. | DOC-06C |
| Receipt | A transaction confirmation record for a completed transaction. | DOC-08 / DOC-06B |
| Statement | A periodic or account-level summary of payer/payee financial activity, not a standalone activity event. | DOC-08 / DOC-06B |
| System Status | The canonical domain or backend state owned by the applicable domain specification. | Domain owner / DOC-18 |
| User-Facing Label | Approved wording projected from a system/domain state for a specific role and surface. It must follow the status-display reference matrix. | Status display reference matrix |
| Action Required | A user-facing readiness or resolution label indicating that the user must take a permitted action. It is not one universal backend status. | Relevant domain owner |
| Under Review | A user-facing label indicating pending approved review without exposing internal risk, provider, fraud, or operational reasons. | Relevant domain owner |
| Linked Case | A support, query, dispute, or exception case associated with a request, obligation, payment, payout, or evidence context. Its lifecycle is `Open`, `Pending Information`, `Under Review`, `Resolved`, or `Closed` and does not replace the linked object's lifecycle state. | DOC-11 |
| Archived | A visibility/history descriptor that hides an item from normal active UI without itself deciding hard deletion, retention expiry, or legal hold. | Relevant domain owner / DOC-15 |
| Archived Records | `ARCHIVED-ROOT`, the Me route separating archived bill/fee and rent obligations from archived or previous evidence documents. | DOC-06B |
| Archive Projection | A per-user visibility record that hides an obligation and its current linked evidence from that user's active views without changing the canonical obligation, counterparty visibility, party linkage, or completed history. | DOC-06B / DOC-06C / DOC-18 |
| Archived Bills & Rent | `ARCHIVED-BILLS-LIST`, the mixed-role list of bill/fee and rent obligations archived by the current user. Invoice, tenancy, and rental documents remain evidence and are not duplicate obligations. | DOC-06C |
| Archived Documents | `ARCHIVED-DOCS-LIST`, the controlled list of current evidence archived with its parent obligation and evidence versions replaced by an accepted newer version. | DOC-06B / DOC-12 |
| Restore Eligibility | An archived-obligation rule indicating whether the parent bill/rent may return to active visibility. `Restore available` is an eligibility hint, not a lifecycle or readiness status, and restore is never offered at evidence level. | DOC-06C / DOC-18 |

## Notification and Communication Terms

| Term | Canonical Definition | Primary Owner |
| --- | --- | --- |
| Notification Event | A stable configurable communication trigger linked to a system or domain event. It does not replace the source event or domain status. | DOC-08 |
| Notification Message | One recipient-specific communication/Inbox record created from a notification event. | DOC-08 / DOC-18 |
| Notification Batch | Optional grouping for campaign, scheduled, manual, support, or other approved multi-message activity. | DOC-08 / DOC-18 / DOC-22 |
| Notification Category | Inbox presentation grouping: `System`, `Service`, `Transaction`, or `Promotion`. It is not a lifecycle status. | DOC-08 |
| Inbox Presentation State | Recipient-specific `Unread`, `Read`, or `Archived` state. It does not change the owning domain object or resolve Action Required. | DOC-06B / DOC-08 |
| Notification Inbox | `NOTIFICATION-INBOX`, the default child screen under `NOTIFICATION-ROOT` for searching, filtering, reading, and archiving notification records. | DOC-06B / DOC-08 |
| Notification Detail | `NOTIFICATION-DETAIL`, the child screen for one permitted message, mapped domain context, and current valid action. | DOC-06B / DOC-08 |
| Notification Settings | `NOTIFICATION-SETTINGS`, the child screen for permitted channel and communication preferences. Privacy & Data remains the source for underlying consent/data-use choices. | DOC-06B / DOC-08 / DOC-15 |

## Promotion, Reward, and Referral Terms

| Term | Canonical Definition | Primary Owner |
| --- | --- | --- |
| Campaign | A governed commercial or program container that may contain multiple offers, qualification rules, budgets, dates, and audiences. | DOC-13 |
| Offer | A defined benefit proposition under a campaign. One offer may appear in multiple discovery collections without becoming duplicate offers. | DOC-13 |
| Offer Card | A UI component summarizing an offer. It is not a credit card, tokenized card, payment card, or route. | DOC-06B |
| Card Offer | A payment-method-sensitive offer whose eligibility depends on the selected payment card or funding leg. | DOC-13 / DOC-09 |
| Entitlement | A beneficiary-specific right to receive or claim an approved reward after qualification. | DOC-13 |
| Reward Instrument | The issued coupon, voucher, partner benefit, miles item, code, or other supported reward created from an entitlement or approved issuance rule. It is not stored money. | DOC-13 |
| My Rewards | `REWARDS-ROOT`, the route managing issued reward instruments through Active and History views. | DOC-06B |
| Referral Program | PayPlus's existing-user-to-new-user invitation program. Every eligible user may share a reusable user-linked code/link; campaign conditions govern qualification and reward. | DOC-13 / DOC-06B |
| Referral Attribution | The immutable normal-user relationship created when a new user completes valid registration using a referral code/link. Sharing alone creates no known recipient or invitation status. | DOC-13 / DOC-18 |
| Referral Qualification | Campaign-specific progress determining whether a referrer or referee earns the corresponding entitlement. | DOC-13 |

## Privacy, Security, and UX Terms

| Term | Canonical Definition | Primary Owner |
| --- | --- | --- |
| Primary Account Email | The unique verified email assigned to one PayPlus account for account communication and supported authentication. The same primary email cannot belong to another PayPlus account. | DOC-15 |
| Entrance Root | `ENTRANCE-ROOT`, the sole unauthenticated app root providing approved public content plus Log In and Create Account entry actions. | DOC-06B |
| Login Route Family | `AUTH-LOGIN`, the authentication entry resolver that opens Fast Login for an eligible remembered account and Full Login otherwise. | DOC-06B |
| Fast Login | `AUTH-LOGIN-FAST`, the eligible remembered-account login experience using enabled OS biometric authentication or password fallback. Eligibility rolls for one month from each successful login and may end earlier for approved risk, device, credential, account, or security reasons. | DOC-06B / DOC-15 |
| Login Method | An explicitly enabled way to authenticate to one PayPlus account: email/password, Google, or Apple. Login methods do not create separate product accounts. | DOC-06B / DOC-15 |
| External Login Provider Identity | The stable provider-specific Google or Apple identity linked to one PayPlus account after explicit provider authentication. Matching email alone never creates or transfers this link. | DOC-15 / DOC-18 |
| Registration Attempt | A temporary pre-account record used to complete registration checks. It creates no PayPlus account, does not reserve proposed identifiers, grants no login or financial rights, and creates no referral attribution. | DOC-06B / DOC-15 / DOC-18 |
| Restricted Account | A PayPlus account created after successful atomic registration checks, with a unique verified primary email, at least one usable login method, and accepted Terms/Privacy, but with one or more Account Activation gates still incomplete. | DOC-05 / DOC-15 |
| Account Activation | The reusable flow for completing required phone verification, identity verification, and six-digit payment-passcode setup before payment or another financially restricted action may proceed. | DOC-06B / DOC-15 |
| Phone Verification | The reusable `ACCOUNT-PROFILE` child flow that verifies or replaces control of the account's primary phone number by SMS OTP. Hong Kong `+852` numbers are the only launch-supported numbers; Account Activation may invoke initial verification contextually. | DOC-06B / DOC-15 |
| Identity Verification | The reusable `ACCOUNT-PROFILE` child flow for first-time identity verification, processing, retry after failure, or an admin-required update. Its user-facing states are `Not Verified`, `Processing`, `Verified`, `Failed`, and `Update Required`; a verified user cannot voluntarily re-verify. | DOC-06B / DOC-15 |
| Payment Passcode | The six-digit PayPlus secret used for payment authorization and other specifically approved sensitive controls. It is not the login password and is never displayed after setup. | DOC-09 / DOC-15 / DOC-19 |
| Payment Passcode Settings | The reusable `ACCOUNT-SECURITY` child flow for six-digit Set, Change, or Reset and the permitted card/payment-profile confirmation preference. Account Activation may invoke Set contextually; Reset requires fresh login reauthentication and OTP to the registered verified phone. | DOC-06B / DOC-19 |
| Authentication Outcome Type | A stable internal classification of what resulted from an authentication, registration, activation, or recovery evaluation. It is separate from persistent account status, Resolution Strategy, user-facing Message/CTA, notification, and one occurrence of the result. | DOC-06B / DOC-07 / DOC-18 |
| Resolution Strategy | The permitted next-handling decision selected after an Outcome, such as Continue, Restart, Redirect, Wait, Support, or Stop. It is not a route, status, message, CTA, or software service. | DOC-06B / DOC-07 |
| Recovery Resolution | A capability-aware Resolution Strategy for account recovery that uses only currently permitted authentication or controlled Support capabilities without exposing protected account information. | DOC-06B / DOC-15 / DOC-19 |
| Authentication Message ID | The stable identifier for approved user-facing authentication copy, disclosure level, actions, and destination behavior. Multiple internal outcomes may map to the same Message ID. | DOC-07 |
| Authentication Occurrence / Correlation ID | The unique event and flow references used to trace one authentication occurrence and related operations without exposing credentials or sensitive values. | DOC-18 |
| Nickname / Display Name | Optional editable account-profile text used for user-facing recognition. It is not a login identifier and does not change an authentication method. | DOC-06B / DOC-15 |
| Masked Display | A permitted projection that conceals sensitive values while retaining enough context for recognition. | DOC-15 |
| Sensitive Reveal | Temporary display of an approved masked sensitive value after payment passcode or approved reauthentication. Prohibited fields remain unavailable. | DOC-15 / DOC-19 |
| Material Sensitive Change | A change to existing identity, contact, security, credential, or Receiving Info data requiring payment passcode or approved reauthentication before route-specific controls. First-time identity verification during Account Activation is not treated as a change to an existing identity record. | DOC-15 / DOC-19 |
| Ordinary Document Access | Permitted evidence, invoice, receipt, statement, or payment-proof view/download within an authenticated approved-purpose context. It does not require an extra prompt solely because the file is opened or downloaded. | DOC-15 |
| Route | A navigable product destination or deep-link target. | DOC-06B |
| Screen | A full-page UI view rendered inside a route. | DOC-06B |
| View / Filter | A role-, state-, or criteria-based presentation inside a screen; not a separate route unless a materially different destination is required. | DOC-06B |
| Sheet / Modal | A temporary focused interaction over or within a route. | DOC-06B |
| Shortcut | A fast entry point to an owning route. It is not a feature owner. | DOC-06B |
| Route Register | The canonical destination inventory at `docs/traceability/route-register.md`. | DOC-06B / DOC-00 |

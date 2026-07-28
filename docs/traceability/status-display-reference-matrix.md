# Status Display Reference Matrix

Status: Working alignment reference  
Owner: Product / Founder  
Last updated: 2026-07-28
Classification: Internal

This matrix aligns PayPlus system/domain statuses with user-facing labels across activity, receipts, checkout, bills, notifications, statements, and future admin views.

It is not the final backend status schema. DOC-18 owns the future canonical status, event, audit, and data model taxonomy. Domain documents continue to own their product-rule status meaning:

- DOC-09: payment, funding-leg, authorization, instruction, and settlement-readiness statuses.
- DOC-10: payout, settlement-calendar, batch, bank-record, and reconciliation statuses.
- DOC-11: refund, cancellation, reversal, dispute, chargeback, hold, recovery, and case statuses.
- DOC-12: evidence, OCR/autofill, verification, and duplicate/reuse statuses.
- DOC-13: promotion eligibility, qualification, entitlement, reward instrument, referral qualification, redemption, reversal, and clawback status meaning.
- DOC-14: risk, AML, anti-cashout, fraud, and review statuses.
- DOC-15: identity-verification display, privacy-request, account-closure, Receiving Info privacy, and privacy/data-control status meaning.
- DOC-22: admin queue, task, permission, and operations workflow statuses.

User-facing labels should be mapped from system/domain statuses. A route should not invent a different status meaning where the same underlying system status is being displayed.

---

## Core Definitions

| Concept | Definition |
| --- | --- |
| Activity | Event or lifecycle view of what happened in the user account. |
| Receipt | Transaction confirmation record for a completed transaction. It may be viewed, downloaded, shared where allowed, or re-issued/replaced according to DOC-08 rules. |
| Statement | Periodic or account-level summary record. It may include payer and payee-side financial activity for the same user account, but should not include unrelated system events. |

---

## Notification Display Boundary

Notification UI must keep four signal families separate:

| Signal Family | Permitted Display | Source of Truth | Rule |
| --- | --- | --- | --- |
| Category | `System`, `Service`, `Transaction`, `Promotion` | DOC-08 notification event definition | Presentation grouping only; not a domain status. |
| Inbox presentation | `Unread`, `Read`, `Archived` | Recipient-specific notification record | Read/archive does not alter the owning domain object or resolve user action. |
| Domain status | Label mapped elsewhere in this matrix | Owning domain | Notification detail must not invent a new status or use delivery/read status as a substitute. |
| Action Required | `Action Required` only where the owning domain currently requires user action | Owning domain/task | Revalidate current state before displaying an active action. |

Message delivery outcomes such as queued, sent, delivered, failed, or retried belong to notification operations. They are not payment, request, evidence, reward, privacy-request, or other product-domain statuses.

---

## Matrix Structure

| Column | Meaning |
| --- | --- |
| Domain | Broad business domain, such as Payment Lifecycle or Request Lifecycle. |
| Stage / Status Type | Human-readable grouping inside the domain. |
| System / Domain Status | Backend or domain status from the owning document. |
| Owning Doc | Source document for system meaning. |
| Payer-Facing Label | Label shown to the user when acting as payer. |
| Payee-Facing Label | Label shown to the user when acting as payee. |
| Appears In | Main user/admin surfaces expected to display the label. |
| Notes | Boundary, wording, or open-decision notes. |

---

## Payment Lifecycle - Initial MVP Display Mapping

| Domain | Stage / Status Type | System / Domain Status | Owning Doc | Payer-Facing Label | Payee-Facing Label | Appears In | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Payment Lifecycle | Payment completion | `Payment Completed` | DOC-09 | `Paid` | `Processing` | Activity, checkout result, bill/rent detail | Payee sees `Processing` until payout completes. Payer-facing Activity should not use generic `Processing` for this state. |
| Payment Lifecycle | Payout completion | `Payout Completed` | DOC-10 | `Transferred` | `Received` | Activity, receipt/proof, statement | Same transaction entry updates status instead of creating a separate payout activity entry by default. |
| Payment Lifecycle | Payment failure | `Payment Failed` | DOC-09 | `Failed` | `Rejected` | Activity, checkout result | Role-specific label. |
| Payment Lifecycle | Payout failure | `Payout Failed` / `Payout Cancelled` | DOC-10 | `Failed` / `Returned` | `Rejected` | Activity, activity detail | Exact payer label depends on whether funds are returned or whether payment did not complete. |
| Payment Lifecycle | Payout return | `Payout Returned` | DOC-10 | `Returned` | `Returned` | Activity, activity detail, receipt/proof re-issue where applicable | Do not imply refund unless DOC-11 confirms a refund. |
| Payment Lifecycle | Refund completed | `Refund Completed` | DOC-11 | `Refunded` | `Reversed` / `Adjusted` | Activity, receipt re-issue where applicable, statement | Payee label needs final policy confirmation. |
| Payment Lifecycle | Reversal completed | `Reversal Completed` | DOC-11 | `Reversed` | `Reversed` | Activity, statement | Must link to original transaction. |
| Payment Lifecycle | Case under review | `Under Review` | DOC-11 / DOC-14 / DOC-22 | `Under Review` | `Under Review` | Activity detail, action-required surfaces | Do not expose hidden risk, fraud, AML, or internal review reasons unless approved. |

---

## Reward Instrument Lifecycle - MVP Display Mapping

`Active` and `History` are route-local views in `REWARDS-ROOT`, not statuses. Instrument filters such as Coupons & Codes, Vouchers, Partner Benefits, and Miles are classifications and must not be used as lifecycle labels.

| Domain | Stage / Status Type | System / Domain State | Owning Doc | User-Facing Label | Appears In | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| Reward Instrument Lifecycle | Issued and usable | Issued instrument passes current eligibility and availability checks | DOC-13 | `Available` | Rewards Active, reward detail, checkout selector | Checkout must revalidate before authorization. |
| Reward Instrument Lifecycle | Recoverable issue | Issued instrument requires user correction or permitted setup | DOC-13 | `Action Required` | Rewards Active, reward detail | Show only the permitted resolution action and a safe explanation. |
| Reward Instrument Lifecycle | Fulfilment pending | Redemption or partner/miles fulfilment submitted but not final | DOC-13 | `In Progress` | Rewards Active, reward detail | Internal `Processing` may exist but is not a separate persistent user-facing label. |
| Reward Instrument Lifecycle | Held for review | Issued instrument is temporarily inactive under approved review | DOC-13 / DOC-14 / DOC-22 | `Under Review` | Rewards Active, reward detail | Do not expose internal risk reasons. Hold-versus-expiry treatment remains open. |
| Reward Instrument Lifecycle | Authoritative consumption | Checkout, QR, code, partner, or other approved use confirmed | DOC-13 | `Used` | Rewards History, reward detail | Reveal, copy, or partner-link open alone does not establish this state. |
| Reward Instrument Lifecycle | Value delivered | Miles or another non-use fulfilment confirmed delivered | DOC-13 | `Credited` | Rewards History, reward detail | Use when delivery, not consumption, is the terminal outcome. |
| Reward Instrument Lifecycle | Usage period ended | Instrument expired before authoritative use/delivery | DOC-13 | `Expired` | Rewards History, reward detail | Exact hold-versus-expiry precedence remains open. |
| Reward Instrument Lifecycle | Withdrawn or clawed back | Instrument voided, reversed, or clawed back under an approved rule | DOC-13 / DOC-11 | `Reversed` | Rewards History, reward detail | Show a safe explanation and preserve audit history. |

A partner or miles `failed` state is domain/internal, not an additional display label. Map it to `In Progress` while unresolved or automatically retrying, `Action Required` where the user can resolve it, or `Reversed` where the instrument is terminally withdrawn. Preserve the underlying failure and reason for operations and audit under DOC-18/DOC-22.

Referral claim `Issued` means that an entitlement created one canonical reward instrument. It is not the issued instrument's ongoing status. A claimed referral item may remain in Referral Rewards `History` while the canonical instrument appears in My Rewards Active as `Available`, `Action Required`, `In Progress`, or `Under Review`, and later in My Rewards History as `Used`, `Credited`, `Expired`, or `Reversed`.

---

## Identity Verification - MVP Display Mapping

External-provider results and PayPlus policy outcomes must map into these five user-facing labels. Final provider-specific mapping belongs in DOC-17, DOC-18, and DOC-22 after provider selection.

| Domain | Stage / Status Type | User-Facing Label | Owning Docs | Appears In | User Action / Notes |
| --- | --- | --- | --- | --- | --- |
| Identity Verification | Not started, incomplete capture, or authorized admin reset | `Not Verified` | DOC-06B / DOC-15 | Account Information, Identity Verification, activation banner where applicable | Show `Verify Now` or `Continue Verification`. |
| Identity Verification | Submitted; authoritative provider result or PayPlus policy decision pending | `Processing` | DOC-06B / DOC-15 | Account Information, Identity Verification, Home banner, notification where applicable | Show `View Status`; do not permit duplicate submission. |
| Identity Verification | Authoritative provider result and PayPlus policy checks passed | `Verified` | DOC-06B / DOC-15 | Account Information, Identity Verification, dismissible completion banner | No verification action; user cannot voluntarily re-verify. |
| Identity Verification | Provider verification or PayPlus policy check failed, including duplicate identity | `Failed` | DOC-06B / DOC-15 | Account Information, Identity Verification, Action Required banner, notification where applicable | Show `Verify Again` and `Get Help`, subject to retry controls and safe reason disclosure. |
| Identity Verification | Authorized admin review requires updated information | `Update Required` | DOC-06B / DOC-15 / DOC-22 | Account Information, Identity Verification, Action Required banner, notification where applicable | Show `Update Verification`; admin cannot directly set `Verified`. |

Provider-specific states, internal review states, suspension, retry restrictions, duplicate checks, and admin workflow states are not additional user-facing labels. They must map to the five labels above according to the owning domain meaning. `Verified` to `Not Verified` requires dual admin approval for MVP.

## Privacy Request - MVP Display Mapping

| Domain | Stage / Status Type | User-Facing Label | Owning Docs | Appears In | Notes |
| --- | --- | --- | --- | --- | --- |
| Privacy Request | Request recorded | `Submitted` | DOC-15 / DOC-22 | Privacy & Data, notification | Acknowledges receipt; it does not promise the requested outcome. |
| Privacy Request | Operational processing | `In Progress` | DOC-15 / DOC-22 | Privacy & Data | Internal queue and assignee detail remain hidden. |
| Privacy Request | User information or action needed | `Action Required` | DOC-15 / DOC-22 | Privacy & Data, notification | Show only the permitted action and safe explanation. |
| Privacy Request | Request completed under the approved process | `Completed` | DOC-15 / DOC-22 | Privacy & Data, notification | A completed export uses protected, time-limited in-app access. |
| Privacy Request | Request cannot be completed as requested | `Unable to Complete` | DOC-15 / DOC-22 | Privacy & Data, notification | Explain the permitted reason category without exposing restricted internal detail. |

---

## Receiving Info - MVP Display Mapping

These labels describe a saved Receiving Info profile, not payout execution and not external bank-account validation. Payout statuses remain in the Payment Lifecycle mapping.

| Domain | Stage / Status Type | User-Facing Label | Owning Docs | Appears In | Notes |
| --- | --- | --- | --- | --- | --- |
| Receiving Info | Personal account matches verified identity under configured rules | `Ready to Receive` | DOC-10 / DOC-12 / DOC-14 | Receiving Info list, card, detail | Internal PayPlus readiness only; do not imply bank validation. |
| Receiving Info | Third-party/company account, ownership mismatch, or proof review pending | `Under Review` | DOC-10 / DOC-12 / DOC-14 | Receiving Info list, card, detail, notification | Show a safe explanation without internal risk reasons. |
| Receiving Info | Review approved | `Ready to Receive` | DOC-10 / DOC-12 / DOC-14 | Receiving Info list, card, detail, notification | Approval is version-specific. |
| Receiving Info | Proof correction or destination-attributable failure requires user action | `Action Required` | DOC-10 / DOC-12 / DOC-14 | Receiving Info list, card, detail, action-required surface, notification | Show the permitted correction action. |
| Receiving Info | Profile archived by user | `Archived` | DOC-10 / DOC-15 | Controlled archived/history access where permitted | Hidden from ordinary selection; retained for audit and historical snapshot linkage. |

A transient bank, rail, provider, or system payout failure does not change the Receiving Info profile label. The payout event uses the Payment Lifecycle mapping instead.

---

## Request Lifecycle - MVP Display Mapping

Request lifecycle is independent from request events, evidence processing, obligation readiness, linked case handling, payment/payout status, and archive visibility.

| Underlying Request State | Sender-Facing Label | Receiver-Facing Label | Visibility and Notes |
| --- | --- | --- | --- |
| `Draft` | `Draft` | Hidden | Sender-only until submitted. |
| `Pending Evidence Verification` | `Waiting for Verification` | Hidden | Evidence gate is active; the request must not be delivered yet. |
| `Pending Receiver Action` | `Reviewing` | `Awaiting` | Same underlying state with role-aware labels. |
| `Accepted` | `Accepted` | `Accepted` | Establishes permitted party/obligation linkage; it is not payment authorization or automatic payment readiness. |
| `Rejected` | `Rejected` | `Rejected` | Terminal request response; reason visibility follows privacy and content rules. |
| `Expired` | `Expired` | `Expired` | Terminal lifecycle result subject to recreate/resend rules. |
| `Cancelled` | `Cancelled` | `Cancelled` where previously visible | Receiver sees cancellation only when the request was previously delivered or visible. |

`Created`, `Updated`, `Submitted`, evidence-gate entered/passed, auto-sent, sent/delivered, shared, viewed, reminded, accepted, rejected, expired, cancelled, resent/recreated, parties linked, archived, and restored are events or visibility transitions. `Archived` hides the item from active views without replacing its retained lifecycle state.

---

## Additional Status Domains and Owners

The following domains already have human-readable status requirements or explicit open alignment work. Domain owners govern state meaning; this matrix governs cross-surface display alignment and must not collapse distinct state families.

| Domain | Covers | Likely Owners |
| --- | --- | --- |
| Request Lifecycle | Canonical states and role-facing labels are defined in the Request Lifecycle mapping above. Events, evidence processing, obligation readiness, linked cases, payment/payout status, and archive visibility are separate. | DOC-06A, DOC-06B, DOC-06C, DOC-08, DOC-18 |
| Bill / Rent Readiness | `Ready to Pay`, `Action Required`, and `Under Review`. `Paid` / `Received` are payment outcomes; `Archived` is visibility; due-state display is date-derived. | DOC-06C, DOC-12, DOC-14, DOC-18 |
| Payment Instruction Lifecycle | Pending instruction, incomplete instruction, expired, cancelled, and archived. Payment-instruction action alerts are not ordinary bill/rent reminder records. | DOC-06B, DOC-09, DOC-18 |
| Evidence Lifecycle | `Not Provided`, `Pending Review`, `Accepted`, `Correction Needed`, `Update Needed`, `Rejected`, and `Duplicate Suspected`. Evidence status may affect obligation readiness but is not payment activity or archive visibility. | DOC-06C, DOC-12, DOC-18, DOC-22 |
| Obligation Archive and Evidence History | `Archived` is an obligation/document visibility label; `Previous version` is evidence history created after accepted replacement. Neither is an evidence-processing status. Restore eligibility belongs to the archived obligation and is not offered on evidence. | DOC-06B, DOC-06C, DOC-12, DOC-15, DOC-18 |
| Promotion Eligibility and Quote Lifecycle | Eligible, selected, applied, reserved, recalculated, released, or rejected before or during checkout. Issued reward-instrument display uses the MVP mapping above. | DOC-09, DOC-13, DOC-18, DOC-22 |
| Referral Qualification Lifecycle | `In Progress`, `Qualified`, `Not Qualified`, `Under Review`. These labels belong to attributed-referee progress in `REFERRAL-ROOT`. | DOC-06B, DOC-13, DOC-18, DOC-22 |
| Referral Reward Presentation | `Available to Claim`, `Issued`, `Expired`, `Reversed`. Entitlement presentation does not create a referral-only issued-instrument status family. `Processing` is transient/internal. A held claim record may remain inactive in Referral History as `Under Review`, while the canonical issued instrument follows the Reward Instrument Lifecycle mapping above. | DOC-06B, DOC-13, DOC-18, DOC-22 |
| Account / Security Lifecycle | Login, device, passcode, suspended, restricted, and account-closure states not explicitly mapped above. Identity-verification and privacy-request display use the MVP mappings above. | DOC-15, DOC-19, DOC-22 |
| Support / Case Lifecycle | `Open`, `Pending Information`, `Under Review`, `Resolved`, and `Closed`. Operational action/outcome states and holds remain separate. | DOC-11, DOC-14, DOC-21, DOC-22 |

---

## Activity Detail Rule

Activity detail may show system lifecycle milestones, but user-facing labels must follow this matrix or the future DOC-18 canonical mapping. For example, the detail may preserve backend milestones such as payment authorization, payment completion, settlement readiness, payout completion, refund, reversal, return, or failure, but the status displayed to payer/payee must use the mapped user-facing label.

`BILLS-ACTIVITY` is limited to payment and related payout/transfer, failure, return, refund, and reversal events for one obligation. Request and evidence lifecycle events must not be inserted into that activity route merely because they relate to the same bill/rent/tenancy record.

## Obligation Archive and Evidence History - MVP Display Mapping

| Record / Condition | User-Facing Label | Appears In | Mapping Rule |
| --- | --- | --- | --- |
| Bill/rent manually archived | `Archived` | `ARCHIVED-BILLS-LIST` | A per-user visibility label. The current linked evidence, where one exists, appears in the same user's `ARCHIVED-DOCS-LIST`; counterparty visibility and canonical records remain unchanged. |
| Current evidence replaced by an accepted newer version | `Previous version` | `ARCHIVED-DOCS-LIST` | Historical and non-restorable; it cannot replace the newer accepted version. |
| Evidence inherited from an archived obligation | `Archived` | `ARCHIVED-DOCS-LIST` | Visibility/history descriptor only; preserve the retained verification outcome separately. |
| Archived obligation eligible for restore from its archive-time class and not blocked by a current operational condition | `Restore available` | `ARCHIVED-BILLS-LIST` and archived detail | Eligibility hint, not a lifecycle or readiness status. Later evidence expiry does not remove the hint; revalidation after restore may produce `Action Required` or `Under Review`. Where restore is unavailable, show a neutral reason only in detail rather than a `Cannot be restored` label. |
| Eligible archived obligation restored | No archive label in active Bills views | Bills detail / readiness surface | Restore its last current evidence and re-evaluate validity, expiry, verification, recipient, compliance, and risk before projecting readiness. |
| Already-expired obligation manually archived | `Archived` | `ARCHIVED-BILLS-LIST`; linked evidence in `ARCHIVED-DOCS-LIST` | Non-restorable. Expiry alone does not auto-archive an obligation. |

The sole current evidence linked to an active bill/rent cannot be archived independently. Missing, pending, rejected, expired, or update-required evidence uses the evidence-processing and obligation-readiness mappings rather than an archive label.

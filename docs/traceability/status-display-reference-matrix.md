# Status Display Reference Matrix

Status: Working alignment reference  
Owner: Product / Founder  
Last updated: 2026-07-22
Classification: Internal

This matrix aligns PayPlus system/domain statuses with user-facing labels across activity, receipts, checkout, bills, notifications, statements, and future admin views.

It is not the final backend status schema. DOC-18 owns the future canonical status, event, audit, and data model taxonomy. Domain documents continue to own their product-rule status meaning:

- DOC-09: payment, funding-leg, authorization, instruction, and settlement-readiness statuses.
- DOC-10: payout, settlement-calendar, batch, bank-record, and reconciliation statuses.
- DOC-11: refund, cancellation, reversal, dispute, chargeback, hold, recovery, and case statuses.
- DOC-12: evidence, OCR/autofill, verification, and duplicate/reuse statuses.
- DOC-13: promotion eligibility, qualification, entitlement, reward instrument, referral qualification, redemption, reversal, and clawback status meaning.
- DOC-14: risk, AML, anti-cashout, fraud, and review statuses.
- DOC-15: identity-verification display, privacy-request, account-closure, and privacy/data-control status meaning.
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

External-provider and backend states must map into these four user-facing labels. Final provider-specific mapping belongs in DOC-18/DOC-22 after provider selection.

| Domain | Stage / Status Type | User-Facing Label | Owning Docs | Appears In | User Action / Notes |
| --- | --- | --- | --- | --- | --- |
| Identity Verification | Submission incomplete or provider result pending | `Pending` | DOC-06B / DOC-15 | Account Information, Identity Verification, notification where applicable | Show `Verify Now`. Resume the current flow or show its active position; do not encourage duplicate submission. |
| Identity Verification | Approved result remains valid | `Verified` | DOC-06B / DOC-15 | Account Information, Identity Verification | No verification action is shown. |
| Identity Verification | Submission or verification did not pass | `Failed` | DOC-06B / DOC-15 | Account Information, Identity Verification, notification where applicable | Show `Verify Now` and a safe explanation without exposing provider or risk detail. |
| Identity Verification | Existing verification must be refreshed or corrected | `Update Required` | DOC-06B / DOC-15 | Account Information, Identity Verification, notification where applicable | Show `Verify Now`; provider-required correction may use the same reusable flow. |

## Privacy Request - MVP Display Mapping

| Domain | Stage / Status Type | User-Facing Label | Owning Docs | Appears In | Notes |
| --- | --- | --- | --- | --- | --- |
| Privacy Request | Request recorded | `Submitted` | DOC-15 / DOC-22 | Privacy & Data, notification | Acknowledges receipt; it does not promise the requested outcome. |
| Privacy Request | Operational processing | `In Progress` | DOC-15 / DOC-22 | Privacy & Data | Internal queue and assignee detail remain hidden. |
| Privacy Request | User information or action needed | `Action Required` | DOC-15 / DOC-22 | Privacy & Data, notification | Show only the permitted action and safe explanation. |
| Privacy Request | Request completed under the approved process | `Completed` | DOC-15 / DOC-22 | Privacy & Data, notification | A completed export uses protected, time-limited in-app access. |
| Privacy Request | Request cannot be completed as requested | `Unable to Complete` | DOC-15 / DOC-22 | Privacy & Data, notification | Explain the permitted reason category without exposing restricted internal detail. |

---

## Future Status Domains

The following domains should be aligned later as their routes, checkout screens, admin workflows, and technical specs mature. They are not all MVP for the current Activity / Receipts route drafting step.

| Domain | Covers | Likely Owners |
| --- | --- | --- |
| Request Lifecycle | Request sent, viewed, accepted, rejected, expired, cancelled, archived. | DOC-06A, DOC-06B, DOC-06C, DOC-08, DOC-18 |
| Bill / Rent Readiness | Evidence, payee information, readiness, action required, due, paid, received. | DOC-06C, DOC-12, DOC-14, DOC-18 |
| Payment Lifecycle | Payment, funding leg, settlement, payout, refund, reversal, return, failed, under review. | DOC-09, DOC-10, DOC-11, DOC-14, DOC-18 |
| Payment Instruction Lifecycle | Pending instruction, incomplete instruction, expired, cancelled, archived. | DOC-06B, DOC-09, DOC-18 |
| Evidence Lifecycle | Uploaded, processing, approved, rejected, update required, archived. | DOC-06C, DOC-12, DOC-18, DOC-22 |
| Promotion Eligibility and Quote Lifecycle | Eligible, selected, applied, reserved, recalculated, released, or rejected before or during checkout. Issued reward-instrument display uses the MVP mapping above. | DOC-09, DOC-13, DOC-18, DOC-22 |
| Referral Qualification Lifecycle | `In Progress`, `Qualified`, `Not Qualified`, `Under Review`. These labels belong to attributed-referee progress in `REFERRAL-ROOT`. | DOC-06B, DOC-13, DOC-18, DOC-22 |
| Referral Reward Presentation | `Available to Claim`, `Issued`, `Expired`, `Reversed`. Entitlement presentation does not create a referral-only issued-instrument status family. `Processing` is transient/internal. A held claim record may remain inactive in Referral History as `Under Review`, while the canonical issued instrument follows the Reward Instrument Lifecycle mapping above. | DOC-06B, DOC-13, DOC-18, DOC-22 |
| Account / Security Lifecycle | Login, device, passcode, suspended, restricted, and account-closure states not explicitly mapped above. Identity-verification and privacy-request display use the MVP mappings above. | DOC-15, DOC-19, DOC-22 |
| Support / Case Lifecycle | Open, pending information, under review, resolved, closed. | DOC-11, DOC-14, DOC-21, DOC-22 |

---

## Activity Detail Rule

Activity detail may show system lifecycle milestones, but user-facing labels must follow this matrix or the future DOC-18 canonical mapping. For example, the detail may preserve backend milestones such as payment authorization, payment completion, settlement readiness, payout completion, refund, reversal, return, or failure, but the status displayed to payer/payee must use the mapped user-facing label.

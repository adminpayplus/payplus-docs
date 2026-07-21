# Status Display Reference Matrix

Status: Working alignment reference  
Owner: Product / Founder  
Last updated: 2026-07-21
Classification: Internal

This matrix aligns PayPlus system/domain statuses with user-facing labels across activity, receipts, checkout, bills, notifications, statements, and future admin views.

It is not the final backend status schema. DOC-18 owns the future canonical status, event, audit, and data model taxonomy. Domain documents continue to own their product-rule status meaning:

- DOC-09: payment, funding-leg, authorization, instruction, and settlement-readiness statuses.
- DOC-10: payout, settlement-calendar, batch, bank-record, and reconciliation statuses.
- DOC-11: refund, cancellation, reversal, dispute, chargeback, hold, recovery, and case statuses.
- DOC-12: evidence, OCR/autofill, verification, and duplicate/reuse statuses.
- DOC-13: promotion eligibility, qualification, entitlement, reward instrument, referral qualification, redemption, reversal, and clawback status meaning.
- DOC-14: risk, AML, anti-cashout, fraud, and review statuses.
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

## Future Status Domains

The following domains should be aligned later as their routes, checkout screens, admin workflows, and technical specs mature. They are not all MVP for the current Activity / Receipts route drafting step.

| Domain | Covers | Likely Owners |
| --- | --- | --- |
| Request Lifecycle | Request sent, viewed, accepted, rejected, expired, cancelled, archived. | DOC-06A, DOC-06B, DOC-06C, DOC-08, DOC-18 |
| Bill / Rent Readiness | Evidence, payee information, readiness, action required, due, paid, received. | DOC-06C, DOC-12, DOC-14, DOC-18 |
| Payment Lifecycle | Payment, funding leg, settlement, payout, refund, reversal, return, failed, under review. | DOC-09, DOC-10, DOC-11, DOC-14, DOC-18 |
| Payment Instruction Lifecycle | Pending instruction, incomplete instruction, expired, cancelled, archived. | DOC-06B, DOC-09, DOC-18 |
| Evidence Lifecycle | Uploaded, processing, approved, rejected, update required, archived. | DOC-06C, DOC-12, DOC-18, DOC-22 |
| Promotion / Reward Lifecycle | Eligible, applied, redeemed, reversed, expired, clawed back. | DOC-13, DOC-18, DOC-22 |
| Referral Qualification Lifecycle | In Progress, Qualified, Not Qualified, Under Review. Referral entitlement and issued-instrument states reuse the Promotion / Reward Lifecycle rather than creating a second reward status family. | DOC-06B, DOC-13, DOC-18, DOC-22 |
| Account / Security Lifecycle | Verification, login, device, passcode, suspended, restricted. | DOC-15, DOC-19, DOC-22 |
| Support / Case Lifecycle | Open, pending information, under review, resolved, closed. | DOC-11, DOC-14, DOC-21, DOC-22 |

---

## Activity Detail Rule

Activity detail may show system lifecycle milestones, but user-facing labels must follow this matrix or the future DOC-18 canonical mapping. For example, the detail may preserve backend milestones such as payment authorization, payment completion, settlement readiness, payout completion, refund, reversal, return, or failure, but the status displayed to payer/payee must use the mapped user-facing label.

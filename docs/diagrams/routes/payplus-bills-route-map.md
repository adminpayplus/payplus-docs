# PayPlus Bills Route Map

Status: Current discussion reference
Owner: DOC-06C
Last updated: 2026-11-13

This map owns the current Bills route family and shows only material external handoffs. Checkout and source Archive retain their own owners; retired Requests, Linking, Receive, and Receiving Info runtime is not represented.

Bills use the accepted Tier 1/2/3 handoffs: Tier 1 uses Declaration without mandatory attached Evidence; Tier 2 requires qualifying official Bill Evidence presence before Payment and acceptance before Payout; Tier 3 may preserve a prepared but non-executable Checkout before approval. Rent remains a separate mandatory attached-Evidence journey. `ARCHIVED-BILLS-LIST` is the Saved/Archived presentation and is excluded from the current Bills list; history-only sources remain outside the Saved/current and Saved/Archived projections.

After an owner-recorded Tier 3 approval, the Payer remains in, or returns to, the current Bill context. A deliberate current `Pay` action invokes the DOC-09 Checkout Resolver; approval itself creates no navigation, route, notification, authorization, Provider Submission, or generic status.

```mermaid
flowchart TD
  ROOT["BILLS-ROOT"] --> PAY["BILLS-PAY"]
  ROOT --> ADD["BILLS-ADD"]
  PAY --> DETAILB["BILLS-DETAIL-BILL"]
  PAY --> DETAILR["BILLS-DETAIL-RENT"]
  ADD --> CAPTURE["Category-scoped Bill / separate Rent capture<br/>Bill B/D/upfront unselected interval; reviewed source facts"]
  CAPTURE -->|"Optional or owner-required Evidence assistance"| UPLOAD["BILLS-EVIDENCE-UPLOAD"]
  UPLOAD -->|"Proposed values; deliberate review"| REVIEW["Source review / owner admission"]
  CAPTURE -->|"Manual facts where permitted"| REVIEW
  REVIEW -->|"Ordinary Save; no Continue Payment"| SAVERES["Actual same-source Save outcome"]
  SAVERES -->|"Confirmed new-source Save"| SUCCESS["New-source success"]
  SUCCESS -->|"View same Bill"| DETAILB
  SUCCESS -->|"View same Rent"| DETAILR
  SUCCESS -->|"Immediate Pay; exact source/current gates"| BILLRES["DOC-09 Checkout Resolver<br/>operation, not route"]
  DETAILB --> ACTIVITY["BILLS-ACTIVITY"]
  DETAILR --> ACTIVITY
  ACTIVITY --> ACTIVITYDETAIL["BILLS-ACTIVITY-DETAIL"]
  DETAILB --> EVIDENCE["BILLS-EVIDENCE-DETAIL"]
  DETAILR --> EVIDENCE
  EVIDENCE --> UPLOAD
  DETAILB --> INLINE["Shared inline Next Payment Reminder<br/>source-bound control, not route"]
  RESULT["Applicable single/split payment result"] --> INLINE
  INLINE -. "Detail caller stays in same detail" .-> DETAILB
  INLINE -. "Result caller stays in original result" .-> RESULT
  DETAILR -->|"Retained Rent policy"| REMINDER["BILLS-REMINDER-DETAIL"]
  REMINDER --> REMINDERLIST["BILLS-REMINDER-LIST<br/>retained Rent consumers"]
  PAY -->|"Current Bill Pay"| BILLRES
  DETAILB -->|"Current Bill Pay"| BILLRES
  BILLRES -->|"Eligible New or valid Resume; current checks"| CHECKOUT["PAYMENT-CHECKOUT"]
  DETAILB -. "Source Archive; linked reminders inactive" .-> ARCHIVE["ARCHIVED-BILLS-LIST"]
  DETAILR -. "Source Archive under separate Rent policy" .-> ARCHIVE
  ARCHIVE -->|"Existing archived read-only mode"| DETAILB
  ARCHIVE -->|"Existing archived read-only mode"| DETAILR
```

DOC-06C Sections 5.9/5.12 own the ordinary Save/new-source versus edit-success distinction, upfront Bill B/D/I and period-isolated inline preferences, retained Rent LIST/DETAIL and narrow valid-D/missing-B preference-only exception. Instruction-origin source-add takes its confirmed same-account Save return to the original Instruction draft rather than inferring success from cancel/unknown; see the Instructions map. Immediate-pay capture has no forced prior Save. All source/Evidence/C1/tier/Rent/destination/risk/authorization gates remain.

Unknown source Save and the narrow independently eligible confirmed-result artifact exception follow DOC-05 Section 10.1; no general history/list or Save-from-Activity entitlement is created. `ARCHIVED-DOCS-LIST` remains a provisional identity with deeper document/version/Restore interaction deferred; this map adds no such active edge. Archive is neither paid confirmation nor erasure, and edit success does not gain the new-source Pay CTA.

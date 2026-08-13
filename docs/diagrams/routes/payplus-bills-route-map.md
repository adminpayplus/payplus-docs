# PayPlus Bills Route Map

Status: Current discussion reference
Owner: DOC-06C
Last updated: 2026-07-26

This map owns the current Bills route family and shows only material external handoffs. Checkout and source Archive retain their own owners; retired Requests, Linking, Receive, and Receiving Info runtime is not represented.

```mermaid
flowchart TD
  ROOT["BILLS-ROOT"] --> PAY["BILLS-PAY"]
  ROOT --> ADD["BILLS-ADD"]

  PAY --> DETAILB["BILLS-DETAIL-BILL"]
  PAY --> DETAILR["BILLS-DETAIL-RENT"]

  ADD --> UPLOAD["BILLS-EVIDENCE-UPLOAD"]
  UPLOAD --> DETAILB
  UPLOAD --> DETAILR

  DETAILB --> ACTIVITY["BILLS-ACTIVITY"]
  DETAILR --> ACTIVITY
  ACTIVITY --> ACTIVITYDETAIL["BILLS-ACTIVITY-DETAIL"]

  DETAILB --> EVIDENCE["BILLS-EVIDENCE-DETAIL"]
  DETAILR --> EVIDENCE
  EVIDENCE --> UPLOAD

  DETAILB --> REMINDER["BILLS-REMINDER-DETAIL"]
  DETAILR --> REMINDER
  REMINDER --> REMINDERLIST["BILLS-REMINDER-LIST"]

  PAY --> CHECKOUT["PAYMENT-CHECKOUT<br/>DOC-09"]

  DETAILB -. "After personal archive, record is accessible later" .-> ARCHIVE["ARCHIVED-BILLS-LIST"]
  DETAILR -. "After personal archive, record is accessible later" .-> ARCHIVE
  ARCHIVE -->|"Open archived read-only mode"| DETAILB
  ARCHIVE -->|"Open archived read-only mode"| DETAILR
  DETAILB -. "View Archived Documents" .-> ARCHIVEDDOCS["ARCHIVED-DOCS-LIST"]
  DETAILR -. "View Archived Documents" .-> ARCHIVEDDOCS
```

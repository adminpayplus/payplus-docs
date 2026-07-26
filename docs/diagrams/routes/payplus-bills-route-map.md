# PayPlus Bills Route Map

Status: Current discussion reference
Owner: DOC-06C
Last updated: 2026-07-26

This map owns the Bills route family and shows only material external handoffs. Checkout, Archive, Requests, and Receiving Info retain their own owners.

```mermaid
flowchart TD
  ROOT["BILLS-ROOT"] --> PAY["BILLS-PAY"]
  ROOT --> RECEIVE["BILLS-RECEIVE"]
  ROOT --> ADD["BILLS-ADD"]

  PAY --> DETAILB["BILLS-DETAIL-BILL"]
  PAY --> DETAILR["BILLS-DETAIL-RENT"]
  RECEIVE --> DETAILB
  RECEIVE --> DETAILR

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

  DETAILB --> LINKING["BILLS-LINKING<br/>Partially defined"]
  DETAILR --> LINKING

  PAY --> CHECKOUT["PAYMENT-CHECKOUT<br/>DOC-09"]
  RECEIVE --> REQUESTS["REQUESTS-DETAIL / REQUESTS-NEW<br/>where applicable"]

  DETAILB -. "After personal archive, record is accessible later" .-> ARCHIVE["ARCHIVED-BILLS-LIST"]
  DETAILR -. "After personal archive, record is accessible later" .-> ARCHIVE
  ARCHIVE -->|"Open archived read-only mode"| DETAILB
  ARCHIVE -->|"Open archived read-only mode"| DETAILR
  DETAILB -. "View Archived Documents" .-> ARCHIVEDDOCS["ARCHIVED-DOCS-LIST"]
  DETAILR -. "View Archived Documents" .-> ARCHIVEDDOCS
```

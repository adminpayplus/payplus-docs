# PayPlus Archive Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-06C
Last updated: 2026-07-26

This map owns the Archive route family. Archive is a per-user visibility projection; the route register and owning documents remain authoritative.

```mermaid
flowchart TD
  ME["ME-ROOT"] --> ROOT["ARCHIVED-ROOT<br/>Archived Records"]
  ROOT --> BILLS["ARCHIVED-BILLS-LIST<br/>Archived Bills & Rent"]
  ROOT --> DOCS["ARCHIVED-DOCS-LIST<br/>Archived Documents"]

  BILLS --> BILLDETAIL["BILLS-DETAIL-BILL<br/>Archived read-only mode"]
  BILLS --> RENTDETAIL["BILLS-DETAIL-RENT<br/>Archived read-only mode"]

  BILLDETAIL --> ACTIVITY["BILLS-ACTIVITY"]
  RENTDETAIL --> ACTIVITY
  BILLDETAIL -->|"View Archived Documents"| SCOPEDDOCS["ARCHIVED-DOCS-LIST<br/>Scoped to obligation"]
  RENTDETAIL -->|"View Archived Documents"| SCOPEDDOCS

  BILLDETAIL -->|"Restore when currently eligible"| ACTIVEBILL["BILLS-DETAIL-BILL<br/>Active Pay / Receive context"]
  RENTDETAIL -->|"Restore when currently eligible"| ACTIVERENT["BILLS-DETAIL-RENT<br/>Active Pay / Receive context"]

  DOCS --> PREVIEW["Route-local read-only preview"]
  SCOPEDDOCS --> PREVIEW
  PREVIEW -->|"View linked obligation"| BILLDETAIL
  PREVIEW -->|"View linked obligation"| RENTDETAIL

  BLOCKED["Review, payment, payout, case, restriction, or legal-hold blocker"] -. "Archive / restore unavailable" .-> BILLS
```

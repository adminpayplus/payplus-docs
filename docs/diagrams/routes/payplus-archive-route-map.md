# PayPlus Archive Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-06C
Last updated: 2026-08-19

This map owns the Archive route family. Saved/current sources move to the Saved/Archived presentation; Archived is not readiness or a financial state and is excluded from the active/current list. History-only sources after confirmed Payment without Save are not Saved/current or Saved/Archived. Archive is non-erasing; the route register and owning documents remain authoritative. Bills and Rent retain their separate Evidence rules.

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

  BILLDETAIL -->|"Restore when currently eligible"| ACTIVEBILL["BILLS-DETAIL-BILL<br/>Saved/current context"]
  RENTDETAIL -->|"Restore when currently eligible"| ACTIVERENT["BILLS-DETAIL-RENT<br/>Saved/current context"]

  DOCS --> PREVIEW["Route-local read-only preview"]
  SCOPEDDOCS --> PREVIEW
  PREVIEW -->|"View linked obligation"| BILLDETAIL
  PREVIEW -->|"View linked obligation"| RENTDETAIL

  BLOCKED["Review, payment, payout, case, restriction, or legal-hold blocker"] -. "Archive / restore unavailable" .-> BILLS
```

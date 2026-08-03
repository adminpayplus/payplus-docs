# PayPlus Action Sheet Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-08-03

This map owns the five `PAYPLUS-ACTION-SHEET` handoffs. Destination internals belong to their route-family maps. It defines behavior, not final visual design.

```mermaid
flowchart TD
  PLUS["Bottom navigation: Pay+"] --> SHEET["PAYPLUS-ACTION-SHEET"]

  SHEET --> BILL["Pay a Bill"]
  SHEET --> RENT["Pay Rent"]
  SHEET --> ADD["Add Bill / Rent"]
  SHEET --> CONTINUE["Continue Payment"]
  SHEET --> REQUEST["Request Payment<br/>payee to payer"]

  BILL --> BILLPAY["BILLS-PAY<br/>temporary Bill / Fee scope"]
  RENT --> RENTPAY["BILLS-PAY<br/>temporary Rent / Tenancy scope"]
  ADD --> BILLSADD["BILLS-ADD"]
  REQUEST --> REQUESTNEW["REQUESTS-NEW"]

  CONTINUE --> COUNT{"Active Payment Instructions or<br/>incomplete Checkout Workspaces"}
  COUNT -->|"None"| DISABLED["Action disabled"]
  COUNT -->|"One"| DETAIL["INSTRUCTIONS-DETAIL"]
  COUNT -->|"More than one"| ROOT["INSTRUCTIONS-ROOT"]

  DETAIL -->|"Incomplete Checkout context"| ALLOWED{"Active, eligible,<br/>and continuable?"}
  ALLOWED -->|"No"| VISIBLE["Continuation unavailable<br/>show current resolution"]
  ALLOWED -->|"Yes; Continue existing Checkout"| CHECKOUT["PAYMENT-CHECKOUT"]

  BILLPAY -. "See Bills route map" .-> BILLSFAMILY["Bills route family"]
  RENTPAY -. "See Bills route map" .-> BILLSFAMILY
  BILLSADD -. "See Bills route map" .-> BILLSFAMILY
  REQUESTNEW -. "See Requests route map" .-> REQUESTFAMILY["Requests route family"]
  ROOT -. "See Instructions route map" .-> INSTRUCTIONFAMILY["Instructions route family"]
  DETAIL -. "See Instructions route map" .-> INSTRUCTIONFAMILY

  subgraph UNRESOLVED["Unresolved entry-contract scope"]
    X01["OQ-XDOC-007: Instruction Pay Now identity<br/>PDM-PROP-X01 evidence alias"]
  end
```

`Request Payment` is the payee-to-payer request action. Optional payer-to-payee linking starts from an approved bill/rent or linking context and is not a Pay+ action-sheet destination.

After `Continue Payment` reaches `INSTRUCTIONS-DETAIL`, only an incomplete Checkout that remains active, eligible, and continuable may follow the connected edge to the existing `PAYMENT-CHECKOUT`. A Payment Instruction may expose `Pay Now`, but its creates/activates/resumes identity contract remains unresolved under `OQ-XDOC-007`; the unconnected annotation records that exclusion without deciding it.

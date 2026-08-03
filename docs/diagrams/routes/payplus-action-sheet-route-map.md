# PayPlus Action Sheet Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-08-04

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

  DETAIL -->|"Current Payment Instruction: Pay Now"| IPVALID["Validate payer, Instruction,<br/>and action availability"]
  IPVALID --> RESOLVER{"DOC-09 Checkout Resolver"}
  RESOLVER -->|"Active, eligible and continuable Checkout exists"| CHECKOUT
  RESOLVER -->|"No active continuable Checkout;<br/>current eligibility permits"| CHECKOUT
  RESOLVER -->|"Cannot proceed"| VISIBLE

  BILLPAY -. "See Bills route map" .-> BILLSFAMILY["Bills route family"]
  RENTPAY -. "See Bills route map" .-> BILLSFAMILY
  BILLSADD -. "See Bills route map" .-> BILLSFAMILY
  REQUESTNEW -. "See Requests route map" .-> REQUESTFAMILY["Requests route family"]
  ROOT -. "See Instructions route map" .-> INSTRUCTIONFAMILY["Instructions route family"]
  DETAIL -. "See Instructions route map" .-> INSTRUCTIONFAMILY

```

`Request Payment` is the payee-to-payer request action. Optional payer-to-payee linking starts from an approved bill/rent or linking context and is not a Pay+ action-sheet destination.

After `Continue Payment` reaches `INSTRUCTIONS-DETAIL`, only an incomplete Checkout that remains active, eligible, and continuable may follow the connected continuation edge to the existing `PAYMENT-CHECKOUT`.

When a current Payment Instruction exposes `Pay Now`, `INSTRUCTIONS-DETAIL` validates the payer, Instruction, and action before invoking the DOC-09 Checkout Resolver. The resolver resumes the existing Checkout when it remains active, eligible, and continuable; permits a later eligible Checkout only when no active continuable Checkout exists; and otherwise returns the current unavailable resolution. Payment Instruction and Checkout remain separate, and resolver entry does not carry stale authorization or silently create funding or submission activity.

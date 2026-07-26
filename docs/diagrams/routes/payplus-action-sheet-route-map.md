# PayPlus Action Sheet Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-07-27

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

  CONTINUE --> COUNT{"Active pending or<br/>incomplete instructions"}
  COUNT -->|"None"| DISABLED["Action disabled"]
  COUNT -->|"One"| DETAIL["INSTRUCTIONS-DETAIL"]
  COUNT -->|"More than one"| ROOT["INSTRUCTIONS-ROOT"]

  DETAIL -->|"Pay Now / Continue"| ALLOWED{"Continuation allowed?"}
  ALLOWED -->|"No; review-blocked"| VISIBLE["Visible; continuation disabled"]
  ALLOWED -->|"Yes"| CHECKOUT["PAYMENT-CHECKOUT"]

  BILLPAY -. "See Bills route map" .-> BILLSFAMILY["Bills route family"]
  RENTPAY -. "See Bills route map" .-> BILLSFAMILY
  BILLSADD -. "See Bills route map" .-> BILLSFAMILY
  REQUESTNEW -. "See Requests route map" .-> REQUESTFAMILY["Requests route family"]
  ROOT -. "See Instructions route map" .-> INSTRUCTIONFAMILY["Instructions route family"]
  DETAIL -. "See Instructions route map" .-> INSTRUCTIONFAMILY
```

`Request Payment` is the payee-to-payer request action. Optional payer-to-payee linking starts from an approved bill/rent or linking context and is not a Pay+ action-sheet destination.

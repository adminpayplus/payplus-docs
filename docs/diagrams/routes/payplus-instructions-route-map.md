# PayPlus Payment Instructions Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-09
Last updated: 2026-07-26

```mermaid
flowchart TD
  SHORTCUT["Dashboard Instructions shortcut"] --> ROOT["INSTRUCTIONS-ROOT"]
  PAYPLUS["Pay+ Continue Payment"] --> ROOT
  ALERT["Instruction action alert"] --> DETAIL["INSTRUCTIONS-DETAIL"]
  ROOT --> DETAIL
  ROOT --> SETUP["Instruction setup"]

  SETUP --> SELECT["Select bill / rent / fee"]
  SETUP --> ADD["BILLS-ADD<br/>if new context is needed"]
  ADD -. "Return with selected context" .-> SETUP

  DETAIL -->|"Pay Now / Continue Payment"| CHECKOUT["PAYMENT-CHECKOUT"]
  DETAIL -->|"Choose or edit card/profile"| PROFILE["PAYMENT-PROFILE-ROOT"]
  PROFILE -. "Return with refreshed selection" .-> DETAIL
  DETAIL -->|"Update pending instruction"| SETUP
  DETAIL -->|"Cancel / Archive where allowed"| ROOT

  CHECKOUT -->|"Still pending or incomplete"| DETAIL
  CHECKOUT -->|"Completed"| ACTIVITY["ACTIVITY-DETAIL"]
```

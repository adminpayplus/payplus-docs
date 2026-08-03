# PayPlus Payment Instructions Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-09
Last updated: 2026-08-03

```mermaid
flowchart TD
  SHORTCUT["Dashboard Instructions shortcut"] --> ROOT["INSTRUCTIONS-ROOT"]
  PAYPLUS["PAYPLUS-ACTION-SHEET<br/>see Pay+ route map"] -. "more than one active managed item" .-> ROOT
  PAYPLUS -. "exactly one active managed item" .-> DETAIL
  ALERT["Payment action alert"] --> DETAIL["INSTRUCTIONS-DETAIL<br/>instruction or checkout context"]
  ROOT --> DETAIL
  ROOT --> SETUP["Instruction setup"]

  SETUP --> SELECT["Select bill / rent / fee"]
  SETUP --> ADD["BILLS-ADD<br/>if new context is needed"]
  ADD -. "Return with selected context" .-> SETUP

  DETAIL -->|"Incomplete Checkout context"| CONTINUABLE{"Active, eligible,<br/>and continuable?"}
  CONTINUABLE -->|"Yes; Continue Payment"| CHECKOUT["PAYMENT-CHECKOUT"]
  CONTINUABLE -->|"No"| UNAVAILABLE["Continuation unavailable<br/>show current resolution"]
  DETAIL -->|"Choose or edit card/profile"| PROFILE["PAYMENT-PROFILE-ROOT"]
  PROFILE -. "Return with refreshed selection" .-> DETAIL
  DETAIL -->|"Update deliberate pay-later instruction"| SETUP
  DETAIL -->|"Cancel / Archive where allowed"| ROOT

  CHECKOUT -->|"Deliberate pay later"| DETAIL
  CHECKOUT -->|"Execution incomplete<br/>retain Checkout identity"| DETAIL
  CHECKOUT -->|"Completed"| ACTIVITY["ACTIVITY-DETAIL"]

  subgraph UNRESOLVED["Unresolved entry-contract scope"]
    X01["OQ-XDOC-007: Instruction Pay Now identity<br/>PDM-PROP-X01 evidence alias"]
  end
```

`Instruction Pay Now` remains an unconnected unresolved-scope annotation. This map does not decide whether that action creates, activates, or resumes Checkout. Only an existing Checkout that remains active, eligible, and continuable may follow the connected `Continue Payment` edge.

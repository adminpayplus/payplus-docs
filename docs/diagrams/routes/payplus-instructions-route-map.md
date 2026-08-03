# PayPlus Payment Instructions Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-09
Last updated: 2026-08-04

```mermaid
flowchart TD
  SHORTCUT["Dashboard Instructions shortcut"] --> ROOT["INSTRUCTIONS-ROOT"]
  PAYPLUS["PAYPLUS-ACTION-SHEET<br/>see Pay+ route map"] -. "more than one active managed item" .-> ROOT
  PAYPLUS -. "exactly one active managed item" .-> DETAIL
  ALERT["Notification-backed Payment Instruction action alert"] --> NDETAIL["NOTIFICATION-DETAIL"]
  NDETAIL -->|"Revalidate current state, payer,<br/>permission, target, and action"| NCTA{"Owner-approved current CTA available?"}
  NCTA -->|"Yes: Pay Now"| IVALID
  NCTA -->|"No"| NRES["Notification/current resolution"]
  ROOT --> DETAIL
  ROOT --> SETUP["Instruction setup"]

  SETUP --> SELECT["Select bill / rent / fee"]
  SETUP --> ADD["BILLS-ADD<br/>if new context is needed"]
  ADD -. "Return with selected context" .-> SETUP

  DETAIL -->|"Incomplete Checkout context"| CONTINUABLE{"Active, eligible,<br/>and continuable?"}
  CONTINUABLE -->|"Yes; Continue Payment"| CHECKOUT["PAYMENT-CHECKOUT"]
  CONTINUABLE -->|"No"| UNAVAILABLE["Continuation unavailable<br/>show current resolution"]
  DETAIL -->|"Current Payment Instruction: Pay Now"| IVALID["Validate payer, Instruction,<br/>and action availability"]
  IVALID --> RESOLVER{"DOC-09 Checkout Resolver"}
  RESOLVER -->|"Active, eligible and continuable Checkout exists"| CHECKOUT
  RESOLVER -->|"No active continuable Checkout;<br/>current eligibility permits"| CHECKOUT
  RESOLVER -->|"Cannot proceed"| UNAVAILABLE
  DETAIL -->|"Choose or edit card/profile"| PROFILE["PAYMENT-PROFILE-ROOT"]
  PROFILE -. "Return with refreshed selection" .-> DETAIL
  DETAIL -->|"Update deliberate pay-later instruction"| SETUP
  DETAIL -->|"Cancel / Archive where allowed"| ROOT

  CHECKOUT -->|"Deliberate pay later"| DETAIL
  CHECKOUT -->|"Execution incomplete<br/>retain Checkout identity"| DETAIL
  CHECKOUT -->|"Completed"| ACTIVITY["ACTIVITY-DETAIL"]

```

A notification-backed Payment Instruction action alert always enters `NOTIFICATION-DETAIL`. Only after current state, authenticated payer, permission, target, and action availability are revalidated may an owner-approved current `Pay Now` CTA invoke the DOC-09 Checkout Resolver. No notification edge enters `INSTRUCTIONS-DETAIL` or `PAYMENT-CHECKOUT` directly.

Instruction `Pay Now` does not predetermine Checkout identity. The resolver resumes an existing Checkout only when it remains active, eligible, and continuable; permits a later eligible Checkout only when no active continuable Checkout exists; and otherwise returns the applicable current resolution. Payment Instruction and Checkout remain separate, retained historical Checkouts are not reactivated, and resolver entry does not carry stale authorization or silently create a Funding Leg, Payment Attempt, or Provider Submission. The connected `Continue Payment` edge remains limited to an existing active, eligible, and continuable Checkout.

# PayPlus Payment Instructions Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-09
Last updated: 2026-11-13

```mermaid
flowchart TD
  SHORTCUT["Dashboard Instructions shortcut"] --> ROOT["INSTRUCTIONS-ROOT"]
  PAYPLUS["PAYPLUS-ACTION-SHEET<br/>see Pay+ map"] -. "More than one active managed item" .-> ROOT
  PAYPLUS -. "Exactly one active managed item" .-> DETAIL["INSTRUCTIONS-DETAIL"]
  ALERT["Notification-backed Instruction alert"] --> NDETAIL["NOTIFICATION-DETAIL"]
  NDETAIL -->|"Current state / payer / permission / target / action"| NCTA{"Owner-approved CTA?"}
  NCTA -->|"Pay Now"| IVALID
  NCTA -->|"Unavailable"| NRES["Current notification resolution"]
  ROOT --> DETAIL
  ROOT --> SETUP["Original Instruction setup draft<br/>internal view"]
  SETUP --> SELECT["Select eligible source"]
  SETUP --> ADD["BILLS-ADD<br/>new source support"]
  ADD -. "Confirmed current same-account Save only<br/>select exact source; preserve draft/date/target" .-> SETUP
  ADD -. "Cancel / unknown: preserve draft; no success selection" .-> SETUP
  SETUP -->|"Explicit Create / Pay after return"| EXPLICIT["Current owner-controlled action<br/>not automatic submission"]
  DETAIL -->|"Incomplete Checkout"| CONTINUABLE{"Active, eligible and continuable?"}
  CONTINUABLE -->|"Continue exact Checkout"| CHECKOUT["PAYMENT-CHECKOUT"]
  CONTINUABLE -->|"No"| UNAVAILABLE["Current unavailable resolution"]
  DETAIL -->|"Current Instruction Pay Now"| IVALID["Validate payer / Instruction / action"]
  IVALID --> RESOLVER{"DOC-09 Checkout Resolver"}
  RESOLVER -->|"Active continuable Checkout"| CHECKOUT
  RESOLVER -->|"No active continuable Checkout; current eligibility"| CHECKOUT
  RESOLVER -->|"Cannot proceed"| UNAVAILABLE
  DETAIL -->|"Card / profile support"| PROFILE["PAYMENT-PROFILE-ROOT"]
  SETUP -->|"Card / profile support"| PROFILE
  PROFILE -. "Actual original Instruction caller/draft" .-> SETUP
  PROFILE -. "Actual Instruction-detail caller" .-> DETAIL
  DETAIL -->|"Update deliberate pay-later setup"| SETUP
  DETAIL -->|"Cancel where permitted"| ROOT
  CHECKOUT -->|"Deliberate pay later / incomplete execution<br/>retain respective identities"| DETAIL
  CHECKOUT -->|"Current payment result"| RESULT["Payment Result<br/>DOC-05 actual Save / artifact boundary"]
  RESULT -->|"Only separately permitted current history access"| ACTIVITY["ACTIVITY-DETAIL"]
```

A notification-backed Payment Instruction action alert always enters `NOTIFICATION-DETAIL`. Only after current state, authenticated payer, permission, target, and action availability are revalidated may an owner-approved current `Pay Now` CTA invoke the DOC-09 Checkout Resolver. No notification edge enters `INSTRUCTIONS-DETAIL` or `PAYMENT-CHECKOUT` directly.

Instruction `Pay Now` does not predetermine Checkout identity. The resolver resumes an existing Checkout only when it remains active, eligible, and continuable; permits a later eligible Checkout only when no active continuable Checkout exists; and otherwise returns the applicable current resolution. Payment Instruction and Checkout remain separate, retained historical Checkouts are not reactivated, and resolver entry does not carry stale authorization or silently create a Funding Leg, Payment Attempt, or Provider Submission. The connected `Continue Payment` edge remains limited to an existing active, eligible, and continuable Checkout. Source Archive is owned by the Bills/Rent route family and never archives a Payment Instruction or Checkout.

Source-add success is confirmed same-account Save, not cancel/unknown or profile selection. Supporting return never creates an Instruction or submits Payment. Optional source Save unknown/Retry/Skip and independently eligible confirmed-result artifacts follow DOC-05 Section 10.1 and the Checkout map; they grant no general Activity/list or Save-from-Activity entitlement. Dotted returns are alternatives bound to the actual caller.

<a id="payplus-payment-profile-route-map"></a>
# CardMore Payment Profile Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-09
Last updated: 2026-11-16

```mermaid
flowchart TD
  SHORTCUT["Dashboard Cards shortcut"] --> ROOT["PAYMENT-PROFILE-ROOT"]
  ME["ME-ROOT<br/>Payments & Bills / Payment Methods"] --> ROOT
  CHECKOUT["PAYMENT-CHECKOUT"] -->|"Add / change card or profile"| ROOT
  INSTRUCTION["INSTRUCTIONS-DETAIL"] -->|"Permitted existing-Checkout funding support"| ROOT

  ROOT --> CARDS["PAYMENT-CARD-LIST<br/>Cards tab"]
  ROOT --> PROFILES["PAYMENT-PROFILE-LIST<br/>Profiles tab"]
  CARDS --> ADDCARD["PAYMENT-CARD-ADD"]
  CARDS --> CARDDETAIL["PAYMENT-CARD-DETAIL"]
  ADDCARD --> TOKEN["Provider-controlled tokenization<br/>DOC-16 / DOC-17<br/>security: DOC-19"]
  TOKEN -. "Return" .-> CARDS

  PROFILES --> ADDPROFILE["PAYMENT-PROFILE-ADD"]
  PROFILES --> PROFILEDETAIL["PAYMENT-PROFILE-DETAIL"]
  ADDPROFILE -. "Save / Cancel" .-> PROFILES
  PROFILEDETAIL -. "Save / Cancel" .-> PROFILES

  ROOT -. "Actual Checkout caller; selection is not submission" .-> CHECKOUT
  ROOT -. "Actual retained Checkout-management caller; no setup draft" .-> INSTRUCTION
  ROOT -. "Actual Me caller; no forced financial action" .-> ME
```

DOC-06B Sections 5.13.2/5.13.5 retain the shared NEW/EDIT ratio editor (100% total), its applicable editor draft and actual account/caller/Checkout allocation-target-mode preservation. Dotted returns remain contextual alternatives. Ordinary Me Save/Cancel returns to Me without forced financial action; permitted Checkout/retained Checkout-management support returns to its actual existing caller, where any later payment action remains explicit and currently gated. Deliberate Instruction setup-draft/Create support is retired. Profile selection/Save never authorizes or submits payment.

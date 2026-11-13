# PayPlus Payment Profile Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-09
Last updated: 2026-11-13

```mermaid
flowchart TD
  SHORTCUT["Dashboard Cards shortcut"] --> ROOT["PAYMENT-PROFILE-ROOT"]
  ME["ME-ROOT<br/>Payments & Bills / Payment Methods"] --> ROOT
  CHECKOUT["PAYMENT-CHECKOUT"] -->|"Add / change card or profile"| ROOT
  INSTRUCTION["INSTRUCTIONS-DETAIL"] -->|"Choose / update card or profile"| ROOT

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
  ROOT -. "Actual Instruction caller/draft; explicit action remains" .-> INSTRUCTION
  ROOT -. "Actual Me caller; no forced Create/Pay" .-> ME
```

DOC-06B Sections 5.13.2/5.13.5 own the shared NEW/EDIT ratio editor (100% total) and applicable account/caller/draft/target/mode preservation. Dotted returns are contextual alternatives, not simultaneous navigation. Ordinary Me Save/Cancel returns to Me; Checkout/Instruction alone performs any applicable explicit later financial action. Profile selection/Save never authorizes or submits payment.

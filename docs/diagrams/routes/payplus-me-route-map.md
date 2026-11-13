# PayPlus Me Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-11-13

This parent map shows direct Me child destinations and the three material account-control handoffs under Account Profile and Account Security. It intentionally does not duplicate deeper child-route flows.

```mermaid
flowchart TD
  NAV["Bottom navigation Me"] --> ME["ME-ROOT<br/>navbar-free grouped My Account"]
  ME --> ACCOUNT["Account & Login<br/>presentation group"]
  ACCOUNT --> PROFILE["ACCOUNT-PROFILE"]
  ACCOUNT --> SECURITY["ACCOUNT-SECURITY"]
  ME -->|"Standalone Notifications"| NOTIFY["NOTIFICATION-SETTINGS"]
  ME --> PAYMENTS["Payments & Bills<br/>presentation group"]
  PAYMENTS -->|"Payment Methods"| PAYMENTPROFILE["PAYMENT-PROFILE-ROOT"]
  PAYMENTS -->|"Transaction History"| ACTIVITY["ACTIVITY-ROOT"]
  PAYMENTS -->|"Bill Management"| BILLS["BILLS-ROOT"]
  PAYMENTS -->|"Archived Data"| ARCHIVE["ARCHIVED-ROOT"]
  ME --> BENEFITS["Rewards & Referral<br/>presentation group"]
  BENEFITS --> REWARDS["REWARDS-ROOT"]
  BENEFITS --> REFERRAL["REFERRAL-ROOT"]
  ME --> SETTINGS["Settings & Support<br/>presentation group"]
  SETTINGS --> PREFS["Preferences<br/>owned local controls"]
  SETTINGS --> PRIVACY["PRIVACY-DATA-CONTROLS"]
  SETTINGS --> SUPPORT["SUPPORT-ROOT"]
  ME --> ABOUTGROUP["About PayPlus<br/>presentation group"]
  ABOUTGROUP -->|"Version"| ABOUT["ABOUT-ROOT"]
  ABOUTGROUP -->|"Terms"| TERMS["TERMS-ROOT"]
  ME --> LOGOUT["Logout"]
  PROFILE --> PHONE["PHONE-VERIFICATION"]
  PROFILE --> IDENTITY["IDENTITY-VERIFICATION"]
  SECURITY --> PASSCODE["PAYMENT-PASSCODE-SETTINGS"]
  ARCHIVE -. "Owning Archive family; no deeper R1 behavior adopted" .-> ARCHIVEFAMILY["Archive family handoff"]
  NOTIFY -. "See Notifications map" .-> NOTIFICATIONFAMILY["Notifications family"]
  LOGOUT --> ENTRANCE["ENTRANCE-ROOT"]
```

Phone-verification modes, identity capture/processing/result states, and payment-passcode Set/Change/Reset modes remain inside their reusable child flows. They are not separate route nodes.

Groups, search and at-most-one-open state are presentation, not routes. Every child returns to its actual permitted Me/query/group/position or contextual Checkout/Instruction/notification caller, with no automatic authentication/payment effect. One shared passcode owner and separately controlled email/phone/identity/privacy/closure flows remain in DOC-06B/DOC-15/DOC-19; Verified is not a voluntary re-verification action.

`RECEIVING-INFO` remains retired/non-active provenance, not a Me edge. `RECEIPTS-ROOT` remains an existing destination through other permitted callers, but is not an adopted Me row. The retained Archived Data entry does not approve provisional archived-document, deep Restore or version behavior. Unavailable capabilities remain honest implementation limits.

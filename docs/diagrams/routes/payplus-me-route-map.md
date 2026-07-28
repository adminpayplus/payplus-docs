# PayPlus Me Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-07-28

This parent map shows direct Me child destinations and the three material account-control handoffs under Account Profile and Account Security. It intentionally does not duplicate deeper child-route flows.

```mermaid
flowchart TD
  NAV["Bottom navigation Me"] --> ME["ME-ROOT"]
  ME --> PROFILE["ACCOUNT-PROFILE"]
  ME --> SECURITY["ACCOUNT-SECURITY"]
  ME --> PRIVACY["PRIVACY-DATA-CONTROLS"]
  ME --> BILLS["BILLS-ROOT"]
  ME --> PAYMENTPROFILE["PAYMENT-PROFILE-ROOT"]
  ME --> RECEIVING["RECEIVING-INFO"]
  ME --> ACTIVITY["ACTIVITY-ROOT"]
  ME --> RECEIPTS["RECEIPTS-ROOT"]
  ME --> ARCHIVE["ARCHIVED-ROOT"]
  ME --> REWARDS["REWARDS-ROOT"]
  ME --> REFERRAL["REFERRAL-ROOT"]
  ME --> NOTIFY["NOTIFICATION-SETTINGS"]
  ME --> SUPPORT["SUPPORT-ROOT"]
  ME --> ABOUT["ABOUT-ROOT"]
  ME --> TERMS["TERMS-ROOT"]
  ME --> LOGOUT["Log Out"]

  PROFILE --> PHONE["PHONE-VERIFICATION"]
  PROFILE --> IDENTITY["IDENTITY-VERIFICATION"]
  SECURITY --> PASSCODE["PAYMENT-PASSCODE-SETTINGS"]

  ARCHIVE -. "See Archive route map" .-> ARCHIVEFAMILY["Archive route family"]
  NOTIFY -. "See Notifications route map" .-> NOTIFICATIONFAMILY["Notifications route family"]
  LOGOUT --> ENTRANCE["ENTRANCE-ROOT"]
```

Phone-verification modes, identity capture/processing/result states, and payment-passcode Set/Change/Reset modes remain inside their reusable child flows. They are not separate route nodes.

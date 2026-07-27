# PayPlus Me Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-07-27

This parent map stops at direct Me child destinations. It intentionally does not duplicate each child's internal tree.

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

  ARCHIVE -. "See Archive route map" .-> ARCHIVEFAMILY["Archive route family"]
  NOTIFY -. "See Notifications route map" .-> NOTIFICATIONFAMILY["Notifications route family"]
  LOGOUT --> AUTH["AUTH-ENTRY"]
```

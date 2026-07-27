# PayPlus Home Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-07-27

This map owns Home sections and the shortcut entry handoffs. Home has a default and maximum of 8 shortcuts, with up to 7 configurable entries plus protected `More`; the effective set may contain fewer configurable entries. Pay+ and destination internals belong to their route-family maps.

```mermaid
flowchart TD
  HOME["HOME-ROOT"] --> NOTICE["Important Notice / Action Required"]
  HOME --> INBOX["NOTIFICATION-INBOX"]
  HOME --> SHORTCUTS["Shortcut grid<br/>1-8 effective entries<br/>More protected and final"]
  HOME --> FEATURED["Featured / What's New / Hot Offer"]
  HOME --> UPCOMING["Upcoming Bills / Rent"]
  HOME --> RECENT["Recent Activity"]

  SHORTCUTS --> REQUESTS["REQUESTS-ROOT"]
  SHORTCUTS --> INSTRUCTIONS["INSTRUCTIONS-ROOT"]
  SHORTCUTS --> BILLS["BILLS-ROOT"]
  SHORTCUTS --> RECEIPTS["RECEIPTS-ROOT"]
  SHORTCUTS --> REMINDERS["BILLS-REMINDER-LIST"]
  SHORTCUTS --> PROFILE["PAYMENT-PROFILE-ROOT"]
  SHORTCUTS --> REFERRAL["REFERRAL-ROOT"]
  SHORTCUTS --> MORE["MORE-ROOT"]

  RECENT --> ACTIVITY["ACTIVITY-ROOT"]
  FEATURED --> OFFER["OFFER-DETAIL<br/>when item is an offer"]
  UPCOMING --> BILLS

  HOME --> PAYPLUS["PAYPLUS-ACTION-SHEET"]
  PAYPLUS -. "See Pay+ route map" .-> PAYPLUSHANDOFFS["Pay+ action handoffs"]
  INBOX -. "See Notifications route map" .-> NOTIFICATIONFAMILY["Notifications route family"]
```

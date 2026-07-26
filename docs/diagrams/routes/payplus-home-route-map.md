# PayPlus Home Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-07-26

This map owns Home sections, the eight MVP shortcuts, and Pay+ action-sheet handoffs. Destination internals belong to their route-family maps.

```mermaid
flowchart TD
  HOME["HOME-ROOT"] --> NOTICE["Important Notice / Action Required"]
  HOME --> INBOX["NOTIFICATION-INBOX"]
  HOME --> SHORTCUTS["Shortcut grid<br/>8 MVP shortcuts"]
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
  PAYPLUS --> PAY["BILLS-PAY<br/>Pay Bill / Fee or Rent"]
  PAYPLUS --> ADD["BILLS-ADD<br/>Add Bill / Rent"]
  PAYPLUS --> CONTINUE["INSTRUCTIONS-ROOT<br/>Continue Payment"]
  PAYPLUS --> NEWREQUEST["REQUESTS-NEW<br/>Request Payment"]
```

# PayPlus App Route Entry Map

Status: Discussion reference / IA alignment aid  
Owner: DOC-06B  
Last updated: 2026-07-02

This Mermaid diagram shows the current working relationship between bottom navigation, the Pay+ action sheet, the eight dashboard shortcuts, and major route handoffs.

It is not final UI design, visual design, component specification, or implementation source of truth. If this diagram conflicts with formal `DOC-XX` documents, the formal documents prevail.

```mermaid
flowchart TD
  NAV["Bottom Navigation"]

  NAV --> HOME["Home Dashboard"]
  NAV --> BILLS["BILLS-ROOT"]
  NAV --> PAYPLUS["Pay+ Action Sheet"]
  NAV --> OFFERS["Offers Hub<br/>(not fully defined)"]
  NAV --> ME["Me<br/>(not fully defined)"]

  HOME --> SHORTCUTS["Dashboard Shortcut Grid<br/>(8 MVP shortcuts)"]
  HOME --> NOTICE["Important Notice / Action Required"]
  HOME --> FEATURED["Featured / What's New / Hot Offer"]
  HOME --> UPCOMING["Upcoming Bills / Rent"]
  HOME --> RECENT["Recent Activity"]

  SHORTCUTS --> REQ["Requests -> REQUESTS-ROOT"]
  SHORTCUTS --> INS["Instructions<br/>(not fully defined / DOC-09)"]
  SHORTCUTS --> BT["Bills & Tenancies -> BILLS-ROOT"]
  SHORTCUTS --> RECEIPTS["Receipts<br/>(global hub not fully defined)"]
  SHORTCUTS --> REMINDERS["Reminders -> BILLS-REMINDER-LIST"]
  SHORTCUTS --> CARDS["Cards / Payment Methods<br/>(not fully defined)"]
  SHORTCUTS --> REFERRAL["Referral<br/>(not fully defined)"]
  SHORTCUTS --> MORE["More<br/>(not fully defined)"]

  BILLS --> BPAY["BILLS-PAY"]
  BILLS --> BRECEIVE["BILLS-RECEIVE"]
  BILLS --> BADD["BILLS-ADD"]

  PAYPLUS -->|"Pay Bill / Fee"| BPAY
  PAYPLUS -->|"Pay Rent"| BPAY
  PAYPLUS -->|"Add Bill / Rent"| BADD
  PAYPLUS -->|"Continue Payment"| INS
  PAYPLUS -->|"Request Payment"| REQ

  BPAY --> BDETAIL["BILLS-DETAIL-BILL / BILLS-DETAIL-RENT"]
  BRECEIVE --> BDETAIL
  BADD --> BEVU["BILLS-EVIDENCE-UPLOAD"]

  BDETAIL --> BACT["BILLS-ACTIVITY"]
  BDETAIL --> BEVD["BILLS-EVIDENCE-DETAIL"]
  BDETAIL --> BRMD["BILLS-REMINDER-DETAIL"]

  BACT --> BACTD["BILLS-ACTIVITY-DETAIL"]
  BEVD --> BEVU
  REMINDERS --> BRMD

  REQ --> RDETAIL["REQUESTS-DETAIL"]
  RDETAIL --> BDETAIL
```


# PayPlus App Route Entry Map

Status: Discussion reference / IA alignment aid  
Owner: DOC-06B  
Last updated: 2026-07-06

These Mermaid diagrams show the current working relationship between bottom navigation, the Pay+ action sheet, the eight dashboard shortcuts, and major route handoffs.

The map is split into layers so that navigation entry points, Bills-route ownership, and Requests-route ownership are not mixed into one unreadable graph.

It is not final UI design, visual design, component specification, or implementation source of truth. If this diagram conflicts with formal `DOC-XX` documents, the formal documents prevail.

## 1. Main Entry Map

This diagram shows only how users enter major areas. It does not try to show every sub-route.

```mermaid
flowchart TD
  NAV["Bottom Navigation"]

  NAV --> HOME["Home"]
  NAV --> BILLS["Bills"]
  NAV --> PAYPLUS["Pay+"]
  NAV --> OFFERS["Offers"]
  NAV --> ME["Me"]

  HOME --> HNOTICE["Important Notice / Action Required"]
  HOME --> HSHORTCUTS["Shortcut Grid<br/>8 MVP shortcuts"]
  HOME --> HFEATURED["Featured / What's New / Hot Offer"]
  HOME --> HUPCOMING["Upcoming Bills / Rent"]
  HOME --> HRECENT["Recent Activity"]

  PAYPLUS --> PACTIONS["Pay+ Action Sheet"]
  PACTIONS --> BPAY["BILLS-PAY<br/>Pay Bill / Fee or Pay Rent"]
  PACTIONS --> BADD["BILLS-ADD<br/>Add Bill / Rent"]
  PACTIONS --> INSTRUCTIONS["INSTRUCTIONS-ROOT<br/>Payment Instructions / Continue Payment"]
  PACTIONS --> RNEW["REQUESTS-NEW<br/>Request Payment"]

  HSHORTCUTS --> REQROOT["REQUESTS-ROOT<br/>Requests"]
  HSHORTCUTS --> INSTRUCTIONS
  HSHORTCUTS --> BROOT["BILLS-ROOT<br/>Bills & Tenancies"]
  HSHORTCUTS --> RECEIPTS["Receipts<br/>Not fully defined"]
  HSHORTCUTS --> REMINDERS["BILLS-REMINDER-LIST<br/>Reminders"]
  HSHORTCUTS --> PPROOT["PAYMENT-PROFILE-ROOT<br/>Cards / Payment Profile"]
  HSHORTCUTS --> REFERRAL["Referral<br/>Not fully defined"]
  HSHORTCUTS --> MORE["More<br/>Not fully defined"]
```

## 2. Bills Route Handoff

This diagram shows the Bills route family owned by DOC-06C.

```mermaid
flowchart TD
  BROOT["BILLS-ROOT"] --> BPAY["BILLS-PAY<br/>To Pay view"]
  BROOT --> BRECEIVE["BILLS-RECEIVE<br/>To Receive view"]
  BROOT --> BADD["BILLS-ADD<br/>Add Bill / Rent"]

  BPAY --> BDETAIL["BILLS-DETAIL-BILL / BILLS-DETAIL-RENT"]
  BRECEIVE --> BDETAIL
  BADD --> BEVUPLOAD["Evidence capture during setup"]
  BEVUPLOAD --> BDETAIL

  BDETAIL --> BACTIVITY["BILLS-ACTIVITY"]
  BDETAIL --> BEVIDENCE["BILLS-EVIDENCE-DETAIL"]
  BDETAIL --> BREMINDER["BILLS-REMINDER-DETAIL"]

  BACTIVITY --> BACTIVITYDETAIL["BILLS-ACTIVITY-DETAIL"]
  BEVIDENCE --> BEVUPLOAD2["Upload / update evidence"]
  BREMINDER --> BREMINDERLIST["BILLS-REMINDER-LIST"]
```

## 3. Requests Route Handoff

This diagram shows the Requests route family owned by DOC-06B and its handoff to Bills routes.

```mermaid
flowchart TD
  ENTRY1["Dashboard Requests shortcut"] --> RROOT["REQUESTS-ROOT"]
  ENTRY2["Inbox / notification / app link"] --> RDETAIL["REQUESTS-DETAIL"]
  ENTRY3["Pay+ Request Payment"] --> RNEW["REQUESTS-NEW"]
  ENTRY4["+ Create Request"] --> RNEW

  RROOT --> RVIEWS["Received / Sent / Archived views"]
  RVIEWS --> RDETAIL
  RROOT --> RNEW

  RNEW --> RSELECT["Select existing bill / rent context"]
  RNEW --> RCREATE["Create new bill / rent context"]
  RCREATE --> BADD["BILLS-ADD"]
  BADD --> RNEWRETURN["Return to REQUESTS-NEW<br/>with created context selected"]

  RSELECT --> RGATE["Evidence verification gate"]
  RNEWRETURN --> RGATE
  RGATE -->|"Verified or approved exception"| RSEND["Send request to receiver"]
  RGATE -->|"Rejected / correction needed"| RACTION["Sender action required"]

  RSEND --> RDETAIL
  RACTION --> RNEW
  RDETAIL --> BDETAIL["Linked BILLS-DETAIL-BILL / BILLS-DETAIL-RENT"]
  BDETAIL --> RDETAILRETURN["Back / save returns to REQUESTS-DETAIL"]
```

## 4. Instructions Route Handoff

This diagram shows the Payment Instructions route shell owned by DOC-06B and its handoff to DOC-09 checkout/payment.

```mermaid
flowchart TD
  ENTRY1["Dashboard Instructions shortcut"] --> IROOT["INSTRUCTIONS-ROOT"]
  ENTRY2["Pay+ Continue Payment"] --> IROOT
  ENTRY3["Action Required / PINS notification"] --> IDETAIL["INSTRUCTIONS-DETAIL"]
  ENTRY4["+ Add Instruction"] --> ISETUP["Instruction setup"]

  IROOT --> ICARDS["Pending / Incomplete / Archived cards"]
  ICARDS --> IDETAIL
  IROOT --> ISETUP

  ISETUP --> BSELECT["Select existing bill / rent / fee"]
  ISETUP --> BADD["BILLS-ADD<br/>if new bill/rent needed"]
  BADD --> ISETUPRETURN["Return to instruction setup<br/>with target selected"]

  IDETAIL -->|"Pending: Pay Now"| CHECKOUT["DOC-09 checkout / review"]
  IDETAIL -->|"Pending: Update Instruction"| ISETUP
  IDETAIL -->|"Pending: Cancel"| IARCHIVE["Cancelled / archived view"]
  IDETAIL -->|"Incomplete: Continue Payment"| CHECKOUT
  IDETAIL -->|"Incomplete: Archive"| IARCHIVE

  CHECKOUT -->|"Submitted / completed"| ACTIVITY["Receipts / Activity"]
  CHECKOUT -->|"Still pending or incomplete"| IDETAIL
```

## 5. Payment Profile Route Handoff

This diagram shows the Payment Profile route shell owned by DOC-06B and its handoff to DOC-09 checkout/payment and DOC-19 tokenization/security.

```mermaid
flowchart TD
  ENTRY1["Dashboard Cards shortcut"] --> PPROOT["PAYMENT-PROFILE-ROOT"]
  ENTRY2["Me / payment settings"] --> PPROOT
  ENTRY3["Checkout change card/profile"] --> PPROOT
  ENTRY4["Instruction card/profile action"] --> PPROOT

  PPROOT --> CARDS["PAYMENT-CARD-LIST<br/>Manage Cards"]
  PPROOT --> PROFILES["PAYMENT-PROFILE-LIST<br/>Manage Profiles"]

  CARDS --> ADDCARD["PAYMENT-CARD-ADD<br/>PSP tokenization"]
  CARDS --> CARDDETAIL["PAYMENT-CARD-DETAIL"]
  PROFILES --> ADDPROFILE["PAYMENT-PROFILE-ADD"]
  PROFILES --> PROFILEDETAIL["PAYMENT-PROFILE-DETAIL"]

  ADDCARD --> TOKEN["DOC-19 tokenization / PSP return"]
  TOKEN --> CARDS

  ADDPROFILE --> PROFILES
  PROFILEDETAIL --> PROFILES

  PPROOT -->|"Return when opened from checkout"| CHECKOUT["DOC-09 checkout / review"]
  PPROOT -->|"Return when opened from instruction"| IDETAIL["INSTRUCTIONS-DETAIL"]
```

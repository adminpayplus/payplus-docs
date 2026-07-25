# PayPlus App Product Destination and Navigation Transition Map

Status: Discussion reference / IA alignment aid  
Owner: DOC-06B  
Last updated: 2026-07-26

These Mermaid diagrams show the current working relationship between bottom navigation, the Pay+ action sheet, the eight dashboard shortcuts, stable product destinations, and major route transitions.

The map is split into layers so that navigation actions, destination hierarchy, Bills-route ownership, and Requests-route ownership are not mixed into one unreadable graph.

It is not final UI design, visual design, component specification, or implementation source of truth. If this diagram conflicts with formal `DOC-XX` documents, the formal documents prevail.

The canonical destination inventory and definition status are maintained in `docs/traceability/route-register.md`.

## 1. Main Navigation Map

This diagram shows only how users enter major areas. It does not try to show every sub-route.

```mermaid
flowchart TD
  NAV["Bottom Navigation"]

  NAV --> HOME["Home"]
  NAV --> BILLS["Bills"]
  NAV --> PAYPLUS["Pay+"]
  NAV --> OFFERS["Offers"]
  NAV --> ME["ME-ROOT<br/>Me"]

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
  HSHORTCUTS --> RECEIPTS["RECEIPTS-ROOT<br/>Receipts & Statements"]
  HSHORTCUTS --> REMINDERS["BILLS-REMINDER-LIST<br/>Reminders"]
  HSHORTCUTS --> PPROOT["PAYMENT-PROFILE-ROOT<br/>Cards / Payment Profile"]
  HSHORTCUTS --> REFERRAL["REFERRAL-ROOT<br/>Defined baseline"]
  HSHORTCUTS --> MORE["More<br/>Shortcut management / overflow<br/>Route detail pending"]

  HRECENT --> ACTIVITYROOT["ACTIVITY-ROOT<br/>Activity"]

  OFFERS --> OFFERSROOT["OFFERS-ROOT<br/>Offer discovery"]
  HFEATURED --> OFFERDETAIL["OFFER-DETAIL<br/>when the item is an offer"]
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
  BADD --> BEVUPLOAD["BILLS-EVIDENCE-UPLOAD<br/>Evidence capture during setup"]
  BEVUPLOAD --> BDETAIL

  BDETAIL --> BACTIVITY["BILLS-ACTIVITY<br/>Payment-related activity only"]
  BDETAIL --> BEVIDENCE["BILLS-EVIDENCE-DETAIL"]
  BDETAIL --> BREMINDER["BILLS-REMINDER-DETAIL"]
  BDETAIL --> BLINK["BILLS-LINKING<br/>Optional; partially defined"]

  BACTIVITY --> BACTIVITYDETAIL["BILLS-ACTIVITY-DETAIL"]
  BEVIDENCE --> BEVUPLOAD
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

  RNEW --> RDEST["Select one receiving destination<br/>for this request"]
  RDEST --> RINFO["RECEIVING-INFO / RECEIVING-INFO-SETUP<br/>if saved profile management is needed"]
  RINFO -. "Return with selected destination" .-> RDEST

  RSELECT --> RCONTEXT["Bill / rent context ready"]
  RNEWRETURN --> RCONTEXT
  RDEST --> RDESTREADY["Destination snapshot ready"]
  RCONTEXT --> RGATE["Send gate<br/>requires verified evidence and destination"]
  RDESTREADY --> RGATE
  RGATE -->|"Verified or approved exception"| RSEND["Send request to receiver"]
  RGATE -->|"Rejected / correction needed"| RACTION["Sender action required"]

  RSEND --> RDETAIL
  RACTION --> RNEW
  RDETAIL --> BDETAIL["Linked BILLS-DETAIL-BILL / BILLS-DETAIL-RENT"]
  BDETAIL --> RDETAILRETURN["Back / save returns to REQUESTS-DETAIL"]
```

The two incoming lines to the send gate are required prerequisites, not alternative paths: the request needs both an eligible bill/rent context with verified evidence and a selected destination snapshot before delivery.

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
  IDETAIL -->|"Choose / update card or profile"| PPROOT["PAYMENT-PROFILE-ROOT<br/>Payment Profile"]
  IDETAIL -->|"Pending: Cancel"| IARCHIVE["Cancelled / archived view"]
  IDETAIL -->|"Incomplete: Continue Payment"| CHECKOUT
  IDETAIL -->|"Incomplete: Archive"| IARCHIVE

  PPROOT -->|"Return with refreshed card/profile data"| IDETAIL

  CHECKOUT -->|"Submitted / completed"| ACTIVITYDETAIL["ACTIVITY-DETAIL"]
  CHECKOUT -->|"Still pending or incomplete"| IDETAIL
```

## 5. Payment Profile Route Handoff

This diagram shows the Payment Profile route shell owned by DOC-06B, including the confirmed two-tab `Cards` / `Profiles` baseline and its handoff to DOC-09 checkout/payment and DOC-19 tokenization/security.

```mermaid
flowchart TD
  ENTRY1["Dashboard Cards shortcut"] --> PPROOT["PAYMENT-PROFILE-ROOT"]
  MEROOT["ME-ROOT"] --> PPROOT
  CHECKOUT["DOC-09 checkout / review"] -->|"Add / change card or profile"| PPROOT
  IDETAIL["INSTRUCTIONS-DETAIL"] -->|"Choose / update card or profile"| PPROOT

  PPROOT --> TABS["Two-tab route<br/>Cards / Profiles"]
  TABS --> CARDS["Cards tab<br/>PAYMENT-CARD-LIST"]
  TABS --> PROFILES["Profiles tab<br/>PAYMENT-PROFILE-LIST"]

  CARDS --> ADDCARD["PAYMENT-CARD-ADD<br/>PSP tokenization"]
  CARDS --> CARDDETAIL["PAYMENT-CARD-DETAIL"]
  PROFILES --> ADDPROFILE["PAYMENT-PROFILE-ADD"]
  PROFILES --> PROFILEDETAIL["PAYMENT-PROFILE-DETAIL"]

  ADDCARD --> TOKEN["DOC-19 tokenization / PSP return"]
  TOKEN --> CARDS

  ADDPROFILE --> PROFILES
  PROFILEDETAIL --> PROFILES

  PPROOT -->|"Return with refreshed card/profile data"| RETURN["Return to originating context"]
  RETURN --> CHECKOUT
  RETURN --> IDETAIL
```

## 6. Activity and Receipts Route Handoff

This diagram separates event/lifecycle activity from receipt and statement files.

```mermaid
flowchart TD
  DASHRECENT["Dashboard Recent Activity arrow"] --> AROOT["ACTIVITY-ROOT"]
  MEROOT["ME-ROOT<br/>Activity row"] --> AROOT
  ACTNOTIF["Payment / payout / refund / reversal notification"] --> ADETAIL["ACTIVITY-DETAIL"]
  CHECKOUT["DOC-09 checkout / result"] --> ADETAIL

  AROOT --> AVIEWS["All / Paid / Received views"]
  AVIEWS --> AENTRY["Accounting-style activity entry"]
  AENTRY --> AEXPANDED["Expanded activity card"]
  AEXPANDED --> ADETAIL
  AEXPANDED --> ROOTDOWNLOAD["Direct receipt / proof / permitted invoice download"]

  ADETAIL --> BILLDETAIL["Linked BILLS-DETAIL-BILL / BILLS-DETAIL-RENT<br/>where applicable"]
  ADETAIL --> RECEIPTDOWNLOAD["Direct receipt / proof download<br/>where available"]

  SHORTCUT["Dashboard Receipts shortcut"] --> RROOT["RECEIPTS-ROOT"]
  MEROOT --> RROOT
  RCPTNOTIF["Receipt notification"] --> RDETAIL["RECEIPT-DETAIL"]
  STMTNOTIF["Statement notification"] --> SDETAIL["STATEMENT-DETAIL"]

  RROOT --> RLIST["Searchable document list<br/>All / Receipts / Statements views"]
  RLIST --> RITEM["Receipt list item"]
  RLIST --> SITEM["Statement list item"]

  RITEM -->|"View"| RDETAIL
  RITEM -->|"Download"| RDIRECT["Direct receipt PDF download"]
  SITEM -->|"View"| SDETAIL
  SITEM -->|"Download"| SDIRECT["Direct statement PDF download"]

  RDETAIL --> RFILE["In-app receipt PDF preview<br/>Close / Back / Download"]
  SDETAIL --> SFILE["In-app statement PDF preview<br/>Close / Back / Download"]

  BILLDETAIL --> BACTIVITY["BILLS-ACTIVITY<br/>contextual bill/rent activity"]
  BACTIVITY --> BACTIVITYDETAIL["BILLS-ACTIVITY-DETAIL"]
  BACTIVITYDETAIL --> BDIRECT["Receipt / proof direct download by default"]
```

## 7. Offers and Rewards Route Handoff

This diagram separates promotion discovery, issued-reward management, and referral participation. It also shows the Referral registration-attribution handoff without treating sharing as a known-recipient invitation. `BILLS-PAY` is shown only as a cross-route destination and is not part of the Offers route family.

```mermaid
flowchart TD
  NAV["Bottom navigation: Offers"] --> OROOT["OFFERS-ROOT<br/>Main Offers screen"]
  FEATURED["Home Featured / Hot Offer"] -->|"Tap offer"| ODETAIL["OFFER-DETAIL<br/>Full-screen modal"]
  PROMONOTIF["Promotion notification or approved deeplink"] -->|"Open referenced offer"| ODETAIL

  OROOT -->|"Tap displayed offer"| ODETAIL
  OROOT -->|"Card Offers: View More"| CARDLIST["OFFERS-CARD-LIST<br/>All Card Offers"]
  OROOT -->|"Pay+ Offers: View More"| PAYPLUSLIST["OFFERS-PAYPLUS-LIST<br/>All Pay+ Offers"]
  OROOT -->|"Partner Offers: View More"| PARTNERLIST["OFFERS-PARTNER-LIST<br/>All Partner Offers"]
  CARDLIST -->|"Tap offer"| ODETAIL
  PAYPLUSLIST -->|"Tap offer"| ODETAIL
  PARTNERLIST -->|"Tap offer"| ODETAIL

  OROOT -->|"My Rewards banner"| REWARDS["REWARDS-ROOT<br/>My Rewards"]
  REWARDICON["Home coupon / rewards icon"] --> REWARDS
  REWARDNOTIF["Reward notification"] -->|"Open referenced reward"| RDETAIL["REWARD-DETAIL<br/>Full-screen modal"]
  REWARDS -->|"Tap reward"| RDETAIL
  RDETAIL -. "Close; restore My Rewards state when origin" .-> REWARDS
  CHECKOUT["DOC-09 checkout<br/>Card/profile then eligible rewards"] -->|"View reward details"| RDETAIL
  RDETAIL -. "Close; preserve checkout without selection" .-> CHECKOUT

  ODETAIL -. "Referral-program action" .-> REFERRAL
  REFSHORTCUT["Dashboard Referral shortcut"] --> REFERRAL["REFERRAL-ROOT<br/>Defined baseline"]
  ME["ME-ROOT<br/>Me"] --> REFERRAL
  REFERRAL -->|"View Referral Rewards"| REFLIST["REFERRAL-REWARDS-LIST<br/>Referrer and referee entitlements"]
  REFLIST -->|"Tap reward card / View Details"| REFDETAIL["REFERRAL-ENTITLEMENT-DETAIL"]
  REFDETAIL -->|"Claim Reward"| REFCLAIM["REFERRAL-REWARD-CLAIM"]
  REFCLAIM -->|"View Reward after issuance"| RDETAIL
  REFCLAIM -. "Done / History selected" .-> REFLIST
  REFLIST -. "View issued reward" .-> RDETAIL
  RDETAIL -. "Close; restore originating Referral context" .-> REFLIST

  REFLINK["Referral deeplink / QR"] --> REGISTRATION["Registration / onboarding<br/>Code prefilled and not editable"]
  REGISTRATION -. "Valid completed registration" .-> ATTRIBUTION["Referral attribution record<br/>DOC-13 / DOC-18"]
  ATTRIBUTION -. "Progress visible to referrer" .-> REFERRAL

  ODETAIL -. "Issued reward handoff" .-> REWARDS
  ODETAIL -. "Eligible obligation handoff" .-> BPAY["BILLS-PAY<br/>Owned by DOC-06C"]
```

## 8. Me Route Handoff

This diagram shows the permanent `ME-ROOT` account-control route and its confirmed destination relationships. It does not define the detailed UI inside child routes. Dashboard shortcut management and More are intentionally excluded because they are separate from the Me route.

```mermaid
flowchart TD
  NAV["Bottom navigation Me"] --> MROOT["ME-ROOT<br/>Permanent mixed-role route"]

  MROOT --> ACTION["Action Required<br/>Hidden when empty"]
  MROOT --> ACCOUNT["Account Information"]
  MROOT --> SECURITY["Security & Privacy"]
  MROOT --> BILLS["Bills & Tenancies"]
  MROOT --> PAYMENTS["Payments & Records"]
  MROOT --> BENEFITS["Rewards & Programs"]
  MROOT --> REFERRAL["Referral Program"]
  MROOT --> PREFS["Preferences & Settings"]
  MROOT --> SUPPORT["Help & Support"]
  MROOT --> ABOUT["About PayPlus"]
  MROOT --> LOGOUT["Log Out<br/>Bottom button"]

  ACCOUNT --> APROFILE["ACCOUNT-PROFILE"]
  APROFILE --> IDVERIFY["IDENTITY-VERIFICATION<br/>Reusable controlled flow"]
  IDVERIFY -. "Back / Cancel / completion" .-> APROFILE
  SECURITY --> ASECURITY["ACCOUNT-SECURITY"]
  ASECURITY --> PASSCODE["PAYMENT-PASSCODE-SETTINGS"]
  PASSCODE -. "Back / completion" .-> ASECURITY
  SECURITY --> PRIVACY["PRIVACY-DATA-CONTROLS"]
  PRIVACY -. "Permitted profile edit<br/>or account closure" .-> APROFILE
  BILLS --> BROOT["BILLS-ROOT"]

  PAYMENTS --> PPROOT["PAYMENT-PROFILE-ROOT"]
  PAYMENTS --> RECEIVE["RECEIVING-INFO<br/>Private reusable profile library"]
  RECEIVE --> RECEIVELIST["RECEIVING-INFO-LIST<br/>Initial rendered screen"]
  RECEIVELIST --> RECEIVEDETAIL["RECEIVING-INFO-DETAILS"]
  RECEIVELIST --> RECEIVESETUP["RECEIVING-INFO-SETUP"]
  RECEIVEDETAIL --> RECEIVESETUP
  RECEIVESETUP -. "Save / Cancel / originating-context return" .-> RECEIVELIST
  PAYMENTS --> AROOT["ACTIVITY-ROOT<br/>Payer and payee activity"]
  PAYMENTS --> RROOT["RECEIPTS-ROOT"]
  PAYMENTS --> ARCHIVE["ARCHIVED-EVIDENCE-LIST<br/>Archived Documents"]

  BENEFITS --> REWARDS["REWARDS-ROOT"]
  BENEFITS -. "Hidden until defined and enabled" .-> MEMBERSHIP["Membership destination TBC"]
  REFERRAL --> REFROOT["REFERRAL-ROOT"]

  PREFS --> NOTIFY["NOTIFICATION-SETTINGS"]
  PRIVACY -. "Notification-channel settings" .-> NOTIFY
  PREFS --> SELECTORS["Language / Theme<br/>Selection sheets"]
  SUPPORT --> SUPROOT["SUPPORT-ROOT"]
  ABOUT --> ABOUTROOT["ABOUT-ROOT"]
  ABOUT --> TERMS["TERMS-ROOT"]
  LOGOUT --> AUTH["Pre-logon / login<br/>Protected history cleared"]

  RETURN["Child route closes or returns<br/>Restore Me position"] -.-> MROOT
```

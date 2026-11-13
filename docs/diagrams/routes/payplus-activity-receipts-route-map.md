# PayPlus Activity and Receipts Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-06C
Last updated: 2026-11-13

```mermaid
flowchart TD
  RECENT["Home Recent Activity"] -->|"Item directly"| ACTDETAIL["ACTIVITY-DETAIL"]
  RECENT -->|"View More"| ACTROOT["ACTIVITY-ROOT"]
  ME["ME-ROOT<br/>Transaction History"] --> ACTROOT
  NOTIFY["Transaction notification message"] --> NDETAIL["NOTIFICATION-DETAIL"]
  NDETAIL -->|"Owner-approved current detail action after revalidation"| ACTDETAIL
  ACTROOT --> SUMMARY["Global-only recent30-day summary"]
  SUMMARY --> STATS["Internal Statistics view<br/>not new route / Statement / ledger"]
  STATS --> FILTERS["Draft / applied scope and charts<br/>DOC-06B Section 5.14.3"]
  STATS -. "Back; do not apply Statistics filters to history" .-> ACTROOT
  ACTROOT -->|"Tap entry"| EXPAND["Expanded entry actions"]
  EXPAND -->|"View Details"| ACTDETAIL
  ACTDETAIL --> BILLDETAIL["BILLS-DETAIL-BILL / BILLS-DETAIL-RENT"]
  ACTDETAIL --> FILES["Existing permitted document actions"]
  SHORTCUT["Dashboard Receipts shortcut"] --> RECEIPTS["RECEIPTS-ROOT"]
  RECEIPTS --> RECEIPT["RECEIPT-DETAIL<br/>actual private Single / Combined PDF"]
  RECEIPTS --> STATEMENT["STATEMENT-DETAIL<br/>actual period PDF"]
  RECEIPTS --> DIRECT["Download actual permitted PDF"]
  FILES --> RECEIPT
  FILES -->|"Separate current full-linked-Bill / binding / access gate"| PUBLIC["Public PNG Save Image / user-confirmed WhatsApp<br/>not an App preview route"]
  RECEIPTNOTIFY["Permitted receipt document notification"] --> RECEIPT
  STATEMENTNOTIFY["Permitted Statement document notification"] --> STATEMENT
  BILLDETAIL --> BILLACTIVITY["BILLS-ACTIVITY"]
  BILLACTIVITY --> BILLACTIVITYDETAIL["BILLS-ACTIVITY-DETAIL"]
  PREVIEW["Source payment-history preview"] -->|"Item directly"| BILLACTIVITYDETAIL
  BILLACTIVITYDETAIL --> FILES
  RECEIPT -. "Actual originating list/result/detail" .-> CALLER["Original caller context"]
  STATEMENT -. "Actual originating list/detail" .-> CALLER
  PUBLIC -. "Actual originating result/detail" .-> CALLER
```

The global record list, source history and immutable financial detail retain separate scopes/callers; cold financial detail falls back safely to Activity. Statistics uses one applied scope and the selected control/chart/Back contract; production metric/date/refund/fee/time/category/label inputs remain Open (R03), not fixture arithmetic or a second ledger.

Private zero/one/two-or-more eligible confirmed Payment membership governs unavailable/Single/Combined presentation and individual Single access under DOC-08 Section 12.1. A partial leg may have a private receipt without public-proof entitlement. Public seven-field PNG/current full-linked-Bill eligibility is separate under Section 12.2; actual save completion, download initiation, cancel/failure and native handoff limits must be truthful (R04). Document notifications retain their specifically permitted owning entries/access checks; a notification-message action follows Detail-first/current revalidation. The unadopted Me-to-Receipts edge is absent; the existing receipt routes/callers are not retired.

Only independently permitted confirmed-result artifacts may precede optional source Save under DOC-05 Section 10.1 and return to that Result; the exception gives no general history/list or later Save-from-Activity right.

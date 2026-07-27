# PayPlus Notifications Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-08
Last updated: 2026-07-27

This map shows the Notifications route family and its material external entries and handoffs. `NOTIFICATION-LIST` and `NOTIFICATION-CARD` are components inside Inbox, and Archived is an Inbox filter.

```mermaid
flowchart LR
  HOME["HOME-ROOT"]
  ME["ME-ROOT"]
  EXTERNAL["Approved external notification context"]
  DEST["Owning product destination"]

  subgraph NOTIFICATIONS["NOTIFICATION-ROOT"]
    INBOX["NOTIFICATION-INBOX"]
    DETAIL["NOTIFICATION-DETAIL"]
    SETTINGS["NOTIFICATION-SETTINGS"]

    INBOX --> DETAIL
    INBOX <--> SETTINGS
  end

  HOME -->|"Inbox icon"| INBOX
  ME -->|"Notification Settings"| SETTINGS
  EXTERNAL -->|"Open specific message"| DETAIL
  DETAIL -->|"Current contextual action"| DEST
```

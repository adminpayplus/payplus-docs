# PayPlus App Route Map

Status: Current discussion reference
Level: 0 - app navigation
Owner: DOC-06B
Last updated: 2026-07-27

This map shows only primary app entry and direct global destinations. Detailed route trees belong to the route-family maps in this folder. The canonical destination inventory is `docs/traceability/route-register.md`.

```mermaid
flowchart TD
  AUTH["AUTH-ENTRY"] --> LOGIN["AUTH-LOGIN"]
  AUTH --> REGISTER["AUTH-REGISTRATION"]
  LOGIN --> HOME["HOME-ROOT"]
  REGISTER --> HOME

  NAV["Bottom navigation"] --> HOME
  NAV --> BILLS["BILLS-ROOT"]
  NAV --> PAYPLUS["PAYPLUS-ACTION-SHEET"]
  NAV --> OFFERS["OFFERS-ROOT"]
  NAV --> ME["ME-ROOT"]

  HOME -. "See Home route map" .-> HOMEFAMILY["Home and shortcuts"]
  BILLS -. "See Bills route map" .-> BILLSFAMILY["Bills route family"]
  PAYPLUS -. "See Pay+ route map" .-> PAYPLUSHANDOFFS["Pay+ action handoffs"]
  OFFERS -. "See Offers route map" .-> OFFERSFAMILY["Offers, Rewards, Referral"]
  ME -. "See Me route map" .-> MEFAMILY["Me direct children"]
```

<a id="payplus-app-route-map"></a>
# CardMore App Route Map

Status: Current discussion reference
Level: 0 - app navigation
Owner: DOC-06B
Last updated: 2026-11-17

This map shows only primary app entry and direct global destinations. Entry edges abbreviate DOC-06B's in-root Start/public choice sheet or qualifying remembered-session PIN branch; they are not direct horizontal buttons or an interstitial. Detailed conditions, dismissal and safe returns belong to the authentication map. The canonical destination inventory is `docs/traceability/route-register.md`.

```mermaid
flowchart TD
  ENTRANCE["ENTRANCE-ROOT<br/>adopted Splash / Start"] -->|"Qualifying Start or public Log In choice"| LOGIN["AUTH-LOGIN"]
  ENTRANCE -->|"Public Create Account choice"| REGISTER["AUTH-REGISTRATION"]
  LOGIN --> HOME["HOME-ROOT"]
  REGISTER --> HOME
  ENTRANCE -. "See Authentication route map" .-> AUTHFAMILY["Entrance and Authentication route family"]

  NAV["Bottom navigation"] --> HOME
  NAV --> BILLS["BILLS-ROOT"]
  NAV --> PAYPLUS["PAYPLUS-ACTION-SHEET"]
  NAV --> OFFERS["OFFERS-ROOT"]
  NAV --> ME["ME-ROOT"]

  HOME -. "See Home route map" .-> HOMEFAMILY["Home and shortcuts"]
  BILLS -. "See Bills route map" .-> BILLSFAMILY["Bills route family"]
  PAYPLUS -. "See CardMore route map" .-> PAYPLUSHANDOFFS["CardMore action handoffs"]
  OFFERS -. "See Offers route map" .-> OFFERSFAMILY["Offers, Rewards, Referral"]
  ME -. "See Me route map" .-> MEFAMILY["Me direct children"]
```

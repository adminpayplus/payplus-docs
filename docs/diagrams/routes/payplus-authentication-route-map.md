# PayPlus Entrance and Authentication Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-07-28

This route-family map shows the approved Entrance, Login, Registration, Recovery, and Account Activation destinations and their material handoffs. Detailed provider, verification, passcode, security, and message behavior remains in the owning documents.

```mermaid
flowchart TD
  LAUNCH["App launch or Log Out"] --> ENTRANCE["ENTRANCE-ROOT"]
  ENTRANCE --> PROMOTION["ENTRANCE-PROMOTION-DETAIL"]
  PROMOTION --> ENTRANCE

  ENTRANCE --> LOGIN["AUTH-LOGIN"]
  LOGIN --> FAST["AUTH-LOGIN-FAST"]
  LOGIN --> FULL["AUTH-LOGIN-FULL"]
  FAST --> RECOVERY["AUTH-RECOVERY"]
  FULL --> RECOVERY
  FAST -->|"Log In With Another Account"| FULL
  FAST --> RETURN["Post-authentication return resolver"]
  FULL --> RETURN
  RETURN -->|"Normal login or invalid target"| HOME["HOME-ROOT"]
  RETURN -->|"Protected target valid"| TARGET["Validated target"]

  ENTRANCE --> REGISTRATION["AUTH-REGISTRATION"]
  REGISTRATION -->|"Restricted account created"| HOME
  REGISTRATION -->|"Complete Now"| ACTIVATION["ACCOUNT-ACTIVATION"]

  HOME -->|"Setup banner"| ACTIVATION
  FINANCIAL["Financial action detects incomplete setup"] --> ACTIVATION
  ACTIVATION --> PHONE["PHONE-VERIFICATION"]
  ACTIVATION --> IDENTITY["IDENTITY-VERIFICATION"]
  ACTIVATION --> PASSCODE["PAYMENT-PASSCODE-SETTINGS"]
  PHONE --> ACTIVATION
  IDENTITY --> ACTIVATION
  PASSCODE --> ACTIVATION
  ACTIVATION -->|"Setup complete"| HOME
  ACTIVATION -->|"Setup complete and context revalidated"| ORIGIN["Originating financial route"]

  DEEPLINK["Protected deeplink"] --> LOGIN
  REFERRAL["Referral deeplink"] --> REGISTRATION
```

# PayPlus Entrance and Authentication Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-07-29

This route-family map shows the approved Entrance, Login, Registration, Recovery, post-authentication return, and Account Activation handoff. The separate Account Activation map explains the contextual verification and passcode handoffs without changing their canonical parentage.

```mermaid
flowchart TD
  LAUNCH["App launch / Log Out"] --> ENTRANCE["ENTRANCE-ROOT"]

  ENTRANCE --> PROMOTION["ENTRANCE-PROMOTION-DETAIL"]
  ENTRANCE --> LOGIN["AUTH-LOGIN"]
  ENTRANCE --> REGISTRATION["AUTH-REGISTRATION"]

  LOGIN --> FAST["AUTH-LOGIN-FAST"]
  LOGIN --> FULL["AUTH-LOGIN-FULL"]
  FAST --> RECOVERY["AUTH-RECOVERY"]
  FULL --> RECOVERY

  FAST --> RETURN["Return resolver"]
  FULL --> RETURN
  RETURN --> HOME["HOME-ROOT"]
  RETURN --> TARGET["Validated protected destination"]

  REGISTRATION --> HOME
  REGISTRATION --> ACTIVATION["ACCOUNT-ACTIVATION"]
```

`AUTH-RECOVERY` is one route with internal screens and states. Its capability evaluation, Outcome, and Resolution Strategy do not create additional route nodes. A permitted resolution may continue or restart Recovery, redirect to an available login method, wait for a controlled condition, hand off to Support, or stop as Recovery Not Permitted.

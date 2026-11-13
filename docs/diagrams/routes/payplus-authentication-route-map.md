# PayPlus Entrance and Authentication Route Map

Status: Current discussion reference
Owner: DOC-06B
Last updated: 2026-11-13

This map projects DOC-06B Sections 5.0.2/5.0.4–5.0.6. OTP tabs, registration checks, Done and Later are internal views/results, not new destinations. New Done/Home identity callers are direct; other permitted activation callers retain their own orchestration. Canonical verification/passcode parentage remains in the Account Activation/Me owners.

```mermaid
flowchart TD
  LAUNCH["App launch / Log Out"] --> ENTRANCE["ENTRANCE-ROOT"]
  ENTRANCE --> PROMOTION["ENTRANCE-PROMOTION-DETAIL"]
  ENTRANCE --> LOGIN["AUTH-LOGIN"]
  ENTRANCE --> REGISTRATION["AUTH-REGISTRATION"]
  LOGIN --> FAST["AUTH-LOGIN-FAST<br/>eligible remembered Login PIN / previously enabled biometric"]
  LOGIN --> FULL["AUTH-LOGIN-FULL<br/>Phone / Email OTP views; Google / Apple"]
  FAST -. "Approved recovery context only" .-> RECOVERY["AUTH-RECOVERY"]
  FULL -. "Separately applicable approved recovery entry" .-> RECOVERY
  FAST --> RETURN["Current protected-return resolver"]
  FULL --> RETURN
  RETURN --> HOME["HOME-ROOT"]
  RETURN --> TARGET["Validated protected destination"]
  REGISTRATION --> REGCHECKS["Phone / provider shared registration views<br/>verified phone; required email proof<br/>matching Login PIN then Terms"]
  REGCHECKS -->|"Confirmed account creation only"| DONE["Account Created Done<br/>internal registration result"]
  DONE -->|"Start Verification"| IDENTITY["IDENTITY-VERIFICATION<br/>shared child; canonical parent ACCOUNT-PROFILE"]
  IDENTITY -. "Actual Done caller: Back / refreshed return" .-> DONE
  DONE -->|"Later"| LATER["One confirmation"]
  LATER -->|"Confirm"| HOME
  LATER -. "Dismiss / Escape" .-> DONE
  HOME -->|"New-user identity-only prompt"| IDENTITY
  IDENTITY -. "Actual Home caller: return" .-> HOME
  PROTECTED["Blocked financial / other permitted activation caller"] --> ACTIVATION["ACCOUNT-ACTIVATION<br/>see activation map"]
```

`AUTH-RECOVERY` is one route with internal screens and states. Its capability evaluation, Outcome, and Resolution Strategy do not create additional route nodes. A permitted resolution may continue or restart Recovery, redirect to an available login method, wait for a controlled condition, hand off to Support, or stop as Recovery Not Permitted.

Phone/email/provider proofs remain purpose/recipient/attempt/revision-bound; unknown send/create reconciles the same operation without automatic duplicate effects. Optional password/recovery is not a password field in the adopted Full Login OTP views. Completing identity does not bypass actual financial, Evidence, risk or authorization gates.

---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor enters a code that does not match, or was already used
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Product refuses the code and keeps the Visitor signed out
  kind: condition
  entities:
  - entity: visitor
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
references:
- kind: code
  role: implementation
  target: actions/emailAuth.tsx
- kind: code
  role: implementation
  target: app/login/confirm/page.tsx
- kind: code
  role: implementation
  target: actions/login.ts
---

# A wrong or used code is refused

## Trigger

The code entered is not the one sent, or has already signed someone in.

## Outcome

Nobody is signed in; the Visitor can try the code again.

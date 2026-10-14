---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to log out
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in
- text: The Product ends the session on leaflet.pub and on the current domain
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts: []
  - entity: domain
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: app/api/auth/logout/route.ts
---

# Sign out

## Trigger

A signed-in User logs out.

## Outcome

The browser is no longer signed in, and the session can no longer be used.

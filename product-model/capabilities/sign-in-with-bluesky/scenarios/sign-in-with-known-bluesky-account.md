---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their Bluesky handle and approves the sign-in at their provider
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Product finds the User with that Bluesky account and signs them in
  kind: product
  entities:
  - entity: user
    effect: reads
    facts:
    - Bluesky account
  contexts:
    web:
      place: leaflet-web::public::sign-in
references:
- kind: code
  role: implementation
  target: app/api/oauth/[route]/route.ts
- kind: code
  role: implementation
  target: src/auth.ts
---

# Sign in with a Bluesky account Leaflet knows

## Trigger

A Visitor whose Bluesky account already has a Leaflet account logs in.

## Outcome

The existing account is signed in; nothing new is created.

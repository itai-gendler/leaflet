---
kind: edge
routes:
  web: Web
steps:
- text: The Visitor enters a handle that does not resolve, or declines at their provider
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Product shows that signing in failed and keeps the Visitor signed out
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
  target: components/OAuthError.tsx
- kind: code
  role: implementation
  target: src/atproto-oauth.ts
---

# Bluesky sign-in does not complete

## Trigger

Authorization at the Bluesky provider fails or is declined.

## Outcome

No account is created or signed in, and the Visitor sees why.

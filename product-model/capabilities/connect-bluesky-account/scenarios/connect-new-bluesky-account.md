---
kind: primary
routes:
  web: Web
steps:
- text: The User, signed in by email only, approves the sign-in at their Bluesky account's provider
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in
- text: The Product connects the Bluesky account to the User and brings in the Bluesky subscriptions it already holds
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Bluesky account
  - entity: subscription
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: app/api/oauth/[route]/route.ts
- kind: code
  role: implementation
  target: src/subscriptions/atproto.ts
---

# Connect a Bluesky account to an email account

## Trigger

A User without a connected Bluesky account chooses to connect one.

## Outcome

The account signs in with either the email or Bluesky, and its existing Bluesky subscriptions show as its own.

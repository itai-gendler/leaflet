---
kind: edge
routes:
  web: Web
steps:
- text: The User approves the sign-in at a Bluesky account that already has a Leaflet account
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in
- text: The Product leaves both accounts as they are and asks the User whether to merge them
  kind: product
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Bluesky account
    - Email
  contexts:
    web:
      place: leaflet-web::signed-in::merge-accounts
references:
- kind: code
  role: implementation
  target: app/api/oauth/[route]/route.ts
- kind: code
  role: implementation
  target: src/subscriptions/atproto.ts
---

# The Bluesky account already has its own Leaflet account

## Trigger

The Bluesky account being connected already belongs to another Leaflet account.

## Outcome

Nothing is connected yet; the User is on the merge page deciding whether to merge the two accounts.

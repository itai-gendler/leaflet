---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their Bluesky handle and chooses to log in
  kind: actor
  actor: visitor
  entities:
  - entity: user
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Visitor approves the sign-in at their Bluesky account provider
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Product finds no account for the Bluesky account and creates a User with it, signed in
  kind: product
  entities:
  - entity: user
    effect: creates
    facts:
    - Bluesky account
    - Profile
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Product returns the Visitor to the page they signed in from
  kind: product
  entities:
  - entity: visitor
    effect: reads
    facts: []
  - entity: page
    effect: reads
    facts: []
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

# Sign in with a Bluesky account for the first time

## Trigger

A Visitor without a Leaflet account chooses to log in with Bluesky.

## Outcome

A new Leaflet account for the Bluesky account exists and is signed in, back on the page the person started from.

## Edge cases

- Signing in from a custom domain signs the person in on leaflet.pub first and carries the session back to the custom domain.
- Choosing to create a new Bluesky account sends the Visitor to their provider's sign-up first.

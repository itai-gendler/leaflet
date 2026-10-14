---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor chooses to subscribe with Bluesky and enters their handle
  kind: actor
  actor: visitor
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
    - Newsletter
  contexts:
    web:
      place: leaflet-web::public::publication
- text: The Visitor approves the sign-in at their Bluesky account's provider
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public::publication
- text: The Product signs them in, creating their account if new, and records the subscription in their Bluesky account
  kind: product
  entities:
  - entity: user
    effect: reads
    facts:
    - Bluesky account
  - entity: subscription
    effect: creates
    facts:
    - Subscribed at
  - entity: notification
    effect: creates
    to: Unread
    facts:
    - Kind
    - Subject
    - Created at
  contexts:
    web:
      place: leaflet-web::public::publication
references:
- kind: code
  role: implementation
  target: actions/publications/subscribeToPublication.ts
- kind: code
  role: implementation
  target: src/subscriptions/atproto.ts
- kind: code
  role: implementation
  target: components/Subscribe/HandleSubscribe.tsx
- kind: code
  role: implementation
  target: app/api/oauth/[route]/afterSignInActions.ts
---

# Subscribe while signed out

## Trigger

A signed-out reader chooses to subscribe with Bluesky.

## Outcome

The reader is signed in, subscribed, and back on the publication.

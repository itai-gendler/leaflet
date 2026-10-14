---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Subscribe
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: leaflet-web::signed-in::publication
- text: The Product records the subscription in the User's Bluesky account and notifies the owner
  kind: product
  actor: user
  entities:
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
      place: leaflet-web::signed-in::publication
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
---

# Subscribe while signed in

## Trigger

A signed-in reader subscribes.

## Outcome

The publication's posts reach the reader's Reader inbox.

## Edge cases

- Subscribing again when already subscribed records nothing new.
- An expired Bluesky sign-in asks the reader to sign in again.

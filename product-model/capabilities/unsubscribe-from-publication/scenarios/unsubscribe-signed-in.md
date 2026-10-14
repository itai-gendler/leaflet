---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to unsubscribe in a publication's subscription panel
  kind: actor
  actor: user
  entities:
  - entity: subscription
    effect: reads
    facts:
    - Subscribed at
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication
- text: The Product deletes the Bluesky subscription and unsubscribes the User's email subscription
  kind: product
  actor: user
  entities:
  - entity: subscription
    effect: removes
  - entity: email-subscription
    effect: changes
    from: Confirmed
    to: Unsubscribed
    facts:
    - Unsubscribed at
  contexts:
    web:
      place: leaflet-web::signed-in::publication
references:
- kind: code
  role: implementation
  target: actions/publications/subscribeEmail.tsx
- kind: code
  role: implementation
  target: src/subscriptions/unsubscribe.ts
- kind: code
  role: implementation
  target: components/Subscribe/ManageSubscribe.tsx
---

# Unsubscribe

## Trigger

A reader no longer wants a publication.

## Outcome

Its posts no longer reach the reader's inbox or email.

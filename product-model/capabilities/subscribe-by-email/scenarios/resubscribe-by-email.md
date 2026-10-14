---
kind: primary
routes:
  web: Web
steps:
- text: The User subscribes with an address that unsubscribed earlier
  kind: actor
  actor: user
  entities:
  - entity: email-subscription
    effect: reads
    facts:
    - Email
  contexts:
    web:
      place: leaflet-web::signed-in::publication
- text: The Product confirms the same subscription again
  kind: product
  actor: user
  entities:
  - entity: email-subscription
    effect: changes
    from: Unsubscribed
    to: Confirmed
    facts:
    - Confirmed at
  - entity: subscription
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication
references:
- kind: code
  role: implementation
  target: actions/publications/subscribeEmail.tsx
- kind: code
  role: implementation
  target: app/api/auth/email-login/route.ts
- kind: code
  role: implementation
  target: src/subscriptions/email.ts
---

# Subscribe again after unsubscribing

## Trigger

A former subscriber comes back.

## Outcome

The address receives the emails again.

---
kind: primary
routes:
  web: Web
steps:
- text: The User enters their account's email address in the subscribe form
  kind: actor
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Email
  contexts:
    web:
      place: leaflet-web::signed-in::publication
- text: The Product confirms the email subscription at once
  kind: product
  actor: user
  entities:
  - entity: email-subscription
    effect: creates
    to: Confirmed
    facts:
    - Email
    - Confirmed at
    - Unsubscribe link
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

# Subscribe with the account's own email

## Trigger

A signed-in reader subscribes with the email their account already has.

## Outcome

The subscription is confirmed without a code.

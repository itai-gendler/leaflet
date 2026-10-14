---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a different address
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Newsletter
  contexts:
    web:
      place: leaflet-web::signed-in::publication
- text: The Product keeps the subscription pending and emails a code
  kind: product
  actor: user
  entities:
  - entity: email-subscription
    effect: creates
    to: Pending
    facts:
    - Email
  - entity: subscription
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication
- text: The User enters the code
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication
- text: The Product confirms the subscription for the User's account
  kind: product
  actor: user
  entities:
  - entity: email-subscription
    effect: changes
    from: Pending
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

# Subscribe with another address

## Trigger

A signed-in reader wants emails at an address other than the account's.

## Outcome

The address is confirmed and receives the emails.

## Edge cases

- A wrong code leaves the subscription pending.

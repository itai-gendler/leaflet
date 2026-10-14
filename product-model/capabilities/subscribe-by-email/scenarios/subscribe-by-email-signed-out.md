---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their email address in a publication's subscribe form
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
- text: The Product emails a subscription code to the address
  kind: product
  entities:
  - entity: subscription
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::public::publication
- text: The Visitor enters the code
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public::sign-in
- text: The Product signs them in to the account for that address, creating it if new, and confirms the email subscription
  kind: product
  entities:
  - entity: user
    effect: reads
    facts:
    - Email
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
      place: leaflet-web::public::sign-in
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

# Subscribe by email while signed out

## Trigger

A signed-out reader subscribes to a newsletter.

## Outcome

The address receives the publication's emails from its next post on, and the reader is signed in.

## Edge cases

- A publication's on-subscribe email, if it has one, is sent to the new subscriber.

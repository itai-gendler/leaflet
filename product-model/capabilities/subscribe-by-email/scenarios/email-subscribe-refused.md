---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor tries to subscribe an address that reported the publication's emails as spam, or the newsletter is off
  kind: actor
  actor: visitor
  entities:
  - entity: publication
    effect: reads
    facts:
    - Newsletter
  contexts:
    web:
      place: leaflet-web::public::publication
- text: The Product refuses and says why
  kind: condition
  entities: []
  contexts:
    web:
      place: leaflet-web::public::publication
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

# Email subscribing is refused

## Trigger

The address cannot receive the newsletter.

## Outcome

No subscription is made.

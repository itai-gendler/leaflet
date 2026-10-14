---
kind: primary
routes:
  web: Web
steps:
- text: The User cancels an email that has not gone out
  kind: actor
  actor: user
  entities:
  - entity: email-post
    effect: reads
    facts:
    - Send at
  contexts:
    web:
      place: leaflet-web::signed-in::email-post
- text: The Product drops it
  kind: product
  actor: user
  entities:
  - entity: email-post
    effect: removes
    from: Scheduled
  contexts:
    web:
      place: leaflet-web::signed-in::email-post
references:
- kind: code
  role: implementation
  target: actions/publications/emailPosts.ts
- kind: code
  role: implementation
  target: src/emailPosts/save.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/email/SendEmail.tsx
---

# Cancel an unsent email

## Trigger

A writer stops an email before it goes out.

## Outcome

Nothing is sent; the draft remains.

## Edge cases

- An email already sending or sent cannot be canceled.

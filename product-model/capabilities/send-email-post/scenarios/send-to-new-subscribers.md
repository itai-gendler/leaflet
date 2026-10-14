---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to send the email to each new subscriber
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: leaflet-web::signed-in::email-post
- text: The Product keeps the email as the publication's on-subscribe email
  kind: product
  actor: user
  entities:
  - entity: email-post
    effect: creates
    to: Active
    facts:
    - Title
    - Description
    - Send mode
    - Content
  - entity: publication
    effect: reads
    facts: []
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
- kind: code
  role: implementation
  target: src/emailPosts/onSubscribe.ts
---

# Send to each new subscriber

## Trigger

A writer wants a welcome email for new subscribers.

## Outcome

Every reader who confirms an email subscription from now on receives it.

## Edge cases

- A publication keeps one on-subscribe email.

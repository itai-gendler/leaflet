---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to send the email while the newsletter is off or the owner has no Leaflet Pro
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Newsletter
    - Pro features
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::email-post
- text: The Product refuses and says why
  kind: condition
  entities: []
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

# Email posts need the newsletter and Leaflet Pro

## Trigger

The publication does not qualify for email posts.

## Outcome

No email is queued.

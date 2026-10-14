---
kind: primary
routes:
  web: Web
steps:
- text: The User gives the email's subject and preview, chooses now or a time, and sends
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  - entity: publication
    effect: reads
    facts:
    - Newsletter
    - Pro features
  contexts:
    web:
      place: leaflet-web::signed-in::email-post
- text: The Product keeps a snapshot of the draft as the email to send
  kind: product
  actor: user
  entities:
  - entity: email-post
    effect: creates
    to: Scheduled
    facts:
    - Title
    - Description
    - Send mode
    - Send at
    - Content
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

# Send an email now or later

## Trigger

An owner or contributor wants to email subscribers something that is not a web post.

## Outcome

The email is queued to go out at the chosen time.

## Edge cases

- Saving again before it goes out replaces what will be sent.

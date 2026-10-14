---
kind: edge
routes:
  web: Web
steps:
- text: An email post is due but the newsletter is off or the owner no longer holds Leaflet Pro
  kind: condition
  unattended: true
  entities:
  - entity: publication
    effect: reads
    facts:
    - Newsletter
    - Pro features
  - entity: email-post
    effect: reads
    facts: []
  - entity: leaflet
    effect: reads
    facts: []
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product pauses it
  kind: product
  entities:
  - entity: email-post
    effect: changes
    from: Scheduled
    to: Paused
    facts:
    - Problem
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
references:
- kind: code
  role: implementation
  target: app/api/inngest/functions/send_email_post.ts
- kind: code
  role: implementation
  target: src/emailPosts/onSubscribe.ts
---

# An email post pauses when the publication stops qualifying

## Trigger

The publication no longer qualifies for email posts when one is due.

## Outcome

Nothing is sent; saving the email again once the publication qualifies resumes it.

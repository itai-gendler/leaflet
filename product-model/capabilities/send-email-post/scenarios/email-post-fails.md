---
kind: edge
routes:
  web: Web
steps:
- text: Sending a Scheduled email post goes wrong for good
  kind: condition
  unattended: true
  entities:
  - entity: email-post
    effect: reads
    facts:
    - Send at
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product marks it failed with the reason
  kind: product
  entities:
  - entity: email-post
    effect: changes
    from: Sending
    to: Failed
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

# An email post fails to send

## Trigger

Delivery to the subscribers keeps failing after retries.

## Outcome

The Emails list shows the email as failed.

---
kind: primary
routes:
  web: Web
steps:
- text: The send time of a Scheduled email post arrives
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
- text: The Product starts sending to the publication's confirmed email subscribers
  kind: product
  entities:
  - entity: email-subscription
    effect: reads
    facts:
    - Email
    - Unsubscribe link
  - entity: email-post
    effect: changes
    from: Scheduled
    to: Sending
    facts: []
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product records it as sent with the number of recipients
  kind: product
  entities:
  - entity: email-post
    effect: changes
    from: Sending
    to: Sent
    facts:
    - Recipients
    - Sent at
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

# An email post goes out

## Trigger

An email post's time comes.

## Outcome

Subscribers receive the email; the dashboard's Emails list shows it sent.

## Edge cases

- When sending fails for good the email post is marked failed.

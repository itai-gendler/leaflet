---
kind: edge
routes:
  web: Web
steps:
- text: The publish time arrives but Leaflet cannot act for the owner's Bluesky account
  kind: condition
  unattended: true
  entities:
  - entity: scheduled-post
    effect: reads
    facts:
    - Scheduled by
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product marks the post failed with the reason
  kind: product
  entities:
  - entity: scheduled-post
    effect: changes
    from: Scheduled
    to: Failed
    facts:
    - Problem
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
references:
- kind: code
  role: implementation
  target: app/api/inngest/functions/publish_scheduled_post.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/publish.ts
---

# A scheduled post fails when the owner is signed out

## Trigger

Publishing at the scheduled time cannot go through.

## Outcome

The post stays a draft, shown as failed and asking the owner to sign in again.

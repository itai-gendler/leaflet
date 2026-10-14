---
kind: edge
routes:
  web: Web
steps:
- text: The publish time arrives but the publication's owner no longer holds Leaflet Pro
  kind: condition
  unattended: true
  entities:
  - entity: publication
    effect: reads
    facts:
    - Pro features
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product pauses the post instead of publishing it
  kind: product
  entities:
  - entity: scheduled-post
    effect: changes
    from: Scheduled
    to: Paused
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

# A scheduled post pauses when Leaflet Pro has lapsed

## Trigger

The owner's Leaflet Pro ended before the post's time.

## Outcome

The post stays a draft, shown as paused with the reason, until rescheduled or canceled.

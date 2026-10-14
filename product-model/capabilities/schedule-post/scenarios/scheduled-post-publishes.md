---
kind: primary
routes:
  web: Web
steps:
- text: The publish time of a Scheduled post arrives while its owner holds Leaflet Pro
  kind: condition
  unattended: true
  entities:
  - entity: scheduled-post
    effect: reads
    facts:
    - Publish at
    - Sharing
    - Scheduled by
  - entity: publication
    effect: reads
    facts:
    - Pro features
  - entity: leaflet
    effect: reads
    facts: []
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product publishes the draft as it stands, as the person who scheduled it, then shares it as scheduled and drops the schedule
  kind: product
  entities:
  - entity: post
    effect: creates
    facts:
    - Title
    - Description
    - Tags
    - Published at
    - Content
    - Address
    - Show in Discover
    - Bluesky post
    - Byline
  - entity: leaflet
    effect: changes
    from: Publication draft
    to: Published
    facts: []
  - entity: scheduled-post
    effect: removes
    from: Scheduled
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

# A scheduled post publishes at its time

## Trigger

A scheduled post's time comes.

## Outcome

The post is live, dated at its scheduled time, and shared as chosen.

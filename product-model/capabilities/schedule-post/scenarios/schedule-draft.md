---
kind: primary
routes:
  web: Web
steps:
- text: The User sets a future publish date, chooses its sharing and schedules
  kind: actor
  actor: user
  entities:
  - entity: publication
    effect: reads
    facts:
    - Pro features
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product keeps the schedule, making a standalone Leaflet a draft of the publication first
  kind: product
  actor: user
  entities:
  - entity: scheduled-post
    effect: creates
    to: Scheduled
    facts:
    - Publish at
    - Sharing
    - Scheduled by
  - entity: publication
    effect: reads
    facts: []
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
references:
- kind: code
  role: implementation
  target: actions/publications/scheduledPosts.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/save.ts
- kind: code
  role: implementation
  target: src/scheduledPosts/eligibility.ts
---

# Schedule a draft

## Trigger

An owner or contributor wants a post out at a set time.

## Outcome

The post is listed as scheduled in the dashboard.

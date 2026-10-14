---
kind: primary
routes:
  web: Web
steps:
- text: The User sets a publish date in the past and publishes
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product publishes the post dated as chosen
  kind: product
  actor: user
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
    - Post settings
  - entity: leaflet
    effect: changes
    from: Draft
    to: Published
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/[leaflet_id]/publish/PublishPost.tsx
- kind: code
  role: implementation
  target: actions/publishToPublication.ts
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
- kind: code
  role: implementation
  target: actions/publishBskyPost.ts
---

# Publish with an earlier date

## Trigger

A writer moves an older piece onto Leaflet.

## Outcome

The post is live and sorted by its chosen date.

## Edge cases

- A date in the future on Publish publishes now; a future date schedules the post instead where scheduling is open.

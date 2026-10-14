---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Post Quietly and publishes
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product publishes the post hidden from Discover, without a Bluesky post or any email
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
    from: Publication draft
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

# Post quietly

## Trigger

A writer wants a post live without announcing it.

## Outcome

The post is reachable at its address and in its publication but not in Discover, on Bluesky or in subscribers' inboxes; updating it later never announces it.

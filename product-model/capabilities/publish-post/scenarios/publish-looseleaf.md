---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Publish as Looseleaf and gives a title, description, tags and cover image
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
    - Description
    - Post settings
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The User writes the Bluesky post that will share it and publishes
  kind: actor
  actor: user
  entities:
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product writes the post to the User's Bluesky account at its leaflet.pub address, marks the Leaflet published and, for a Leaflet with a Leaflet Pro owner, keeps a version of what was published
  kind: product
  actor: user
  entities:
  - entity: post
    effect: creates
    facts:
    - Title
    - Description
    - Tags
    - Cover image
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
  - entity: leaflet-version
    effect: creates
    facts:
    - Kind
    - Saved at
    - Saved by
    - Snapshot
  contexts:
    web:
      place: leaflet-web::signed-in::publish
- text: The Product posts the Bluesky post linking to it
  kind: product
  actor: user
  entities:
  - entity: post
    effect: changes
    facts:
    - Bluesky post
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

# Publish as a Looseleaf

## Trigger

A signed-in User with a Bluesky account publishes a standalone Leaflet.

## Outcome

The post is live on the User's profile and shared on Bluesky; people, publications and posts it mentions are notified.

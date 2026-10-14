---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Update! in the Leaflet of a published post
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
    - Pages
  - entity: post
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product rewrites the post with the Leaflet's current content, keeping its address, date and Discover choice, and keeps a version when the Leaflet has a Leaflet Pro owner
  kind: product
  actor: user
  entities:
  - entity: post
    effect: changes
    facts:
    - Title
    - Description
    - Content
    - Byline
  - entity: leaflet-version
    effect: creates
    facts:
    - Kind
    - Saved at
    - Saved by
    - Snapshot
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: app/(app)/(editor)/[leaflet_id]/actions/PublishButton.tsx
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
---

# Update a published post

## Trigger

A writer fixes or extends a published post.

## Outcome

Readers see the updated post; it is not emailed or shared again.

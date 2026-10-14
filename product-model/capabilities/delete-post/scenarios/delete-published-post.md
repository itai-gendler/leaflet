---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a published post and confirms
  kind: actor
  actor: user
  entities:
  - entity: post
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product deletes the post's record and its Leaflet
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: removes
    from: Published
  - entity: post
    effect: removes
    with: leaflet
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/deletePost.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/home/LeafletList/LeafletOptions.tsx
---

# Delete a post

## Trigger

A writer wants a post gone for good.

## Outcome

Neither the post nor its draft exists any longer.

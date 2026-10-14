---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Unpublish Post on their Looseleaf
  kind: actor
  actor: user
  entities:
  - entity: post
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: leaflet-web::signed-in::home
- text: The Product deletes the post's record and turns it back into a Leaflet
  kind: product
  actor: user
  entities:
  - entity: post
    effect: removes
  - entity: leaflet
    effect: changes
    from: Published
    to: Draft
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::home
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/deletePost.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/home/LeafletList/LeafletOptions.tsx
---

# Unpublish a Looseleaf

## Trigger

An author withdraws a standalone post.

## Outcome

The Leaflet is an unpublished Leaflet on Home again.

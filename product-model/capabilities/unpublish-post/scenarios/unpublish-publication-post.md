---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Unpublish Post on a post of a publication they own or contribute to
  kind: actor
  actor: user
  entities:
  - entity: post
    effect: reads
    facts:
    - Title
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product deletes the post's record and returns its Leaflet to the publication's drafts
  kind: product
  actor: user
  entities:
  - entity: post
    effect: removes
  - entity: leaflet
    effect: changes
    from: Published
    to: Publication draft
    facts: []
  - entity: publication
    effect: reads
    facts: []
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

# Unpublish a publication post

## Trigger

A writer wants a post off the web but not lost.

## Outcome

The post's address no longer shows it; its draft is back among the drafts.

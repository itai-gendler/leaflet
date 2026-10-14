---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to unpublish a post they neither wrote nor can publish in its publication
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
      place: leaflet-web::signed-in::home
- text: 'The Product refuses: they are not authorized to modify this post'
  kind: condition
  entities:
  - entity: post
    effect: reads
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

# Someone else's post cannot be unpublished

## Trigger

A person holding a published Leaflet's edit link tries to unpublish it.

## Outcome

The post stays published.

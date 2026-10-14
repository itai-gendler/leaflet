---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a Leaflet on Home and confirms
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  - entity: home-leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::home
- text: The Product deletes the Leaflet with its pages, blocks and images, and its links stop working
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: removes
    from: Draft
  - entity: home-leaflet
    effect: removes
    from: On Home
    with: leaflet
  - entity: block
    effect: reads
    facts: []
  - entity: page
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::home
references:
- kind: code
  role: implementation
  target: actions/deleteLeaflet.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/home/LeafletList/LeafletOptions.tsx
---

# Delete a Leaflet

## Trigger

A User no longer wants an unpublished Leaflet.

## Outcome

The Leaflet is gone for everyone; its edit and view links open nothing.

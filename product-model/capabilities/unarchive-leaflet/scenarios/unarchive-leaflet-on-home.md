---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Unarchive on an archived Leaflet, or Undo right after archiving
  kind: actor
  actor: user
  entities:
  - entity: home-leaflet
    effect: reads
    facts: []
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::home
- text: The Product returns it to Home and to the publication's drafts
  kind: product
  actor: user
  entities:
  - entity: home-leaflet
    effect: changes
    from: Archived
    to: On Home
    facts: []
  - entity: leaflet
    effect: changes
    facts:
    - Archived in publication
  - entity: publication
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

# Unarchive a Leaflet

## Trigger

A User wants an archived Leaflet back.

## Outcome

The Leaflet is listed on Home again.

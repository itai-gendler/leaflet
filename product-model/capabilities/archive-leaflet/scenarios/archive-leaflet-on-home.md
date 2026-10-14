---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Archive on a Leaflet on Home
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
- text: The Product archives it on the User's Home and, for a draft of a publication the User belongs to, in the publication's drafts
  kind: product
  actor: user
  entities:
  - entity: home-leaflet
    effect: changes
    from: On Home
    to: Archived
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

# Archive a Leaflet

## Trigger

A User wants a Leaflet out of their way without deleting it.

## Outcome

The Leaflet is in the User's archive, with an undo offered right away.

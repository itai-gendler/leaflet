---
kind: validation
routes:
  web: Web
steps:
- text: The User chooses Delete on a draft whose publication they neither own nor write for
  kind: actor
  actor: user
  entities:
  - entity: leaflet
    effect: reads
    facts:
    - Title
  - entity: publication
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::home
- text: The Product refuses and the draft stays
  kind: condition
  entities: []
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

# Someone outside the publication cannot delete its draft

## Trigger

A person holding a publication draft's edit link tries to delete it.

## Outcome

The draft is unchanged and the User sees it could not be deleted.

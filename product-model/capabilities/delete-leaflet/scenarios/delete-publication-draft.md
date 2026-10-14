---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a draft of a publication they own or contribute to, and confirms
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
      place: leaflet-web::signed-in::publication-dashboard
- text: The Product deletes the draft
  kind: product
  actor: user
  entities:
  - entity: leaflet
    effect: removes
    from: Publication draft
  contexts:
    web:
      place: leaflet-web::signed-in::publication-dashboard
references:
- kind: code
  role: implementation
  target: actions/deleteLeaflet.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/(home-pages)/(writer)/home/LeafletList/LeafletOptions.tsx
---

# Delete a publication draft

## Trigger

An owner or contributor removes a draft from a publication.

## Outcome

The draft no longer exists.

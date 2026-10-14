---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens a template link
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: leaflet-web::public
- text: The Product creates a new Leaflet holding a copy of the template's pages and blocks, and opens it
  kind: product
  actor: visitor
  entities:
  - entity: leaflet
    as: template
    effect: reads
    facts:
    - Pages
  - entity: leaflet
    as: copy
    effect: creates
    to: Draft
    facts:
    - Title
    - Pages
    - Theme
    - Edit link
  - entity: block
    effect: reads
    facts: []
  - entity: page
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::public::leaflet
references:
- kind: code
  role: implementation
  target: actions/createNewLeafletFromTemplate.ts
- kind: code
  role: implementation
  target: app/template/[template_id]/route.ts
---

# Copy a template Leaflet

## Trigger

Someone opens a link to start from a template Leaflet.

## Outcome

A new Leaflet with the template's content is open for editing; the template is unchanged.

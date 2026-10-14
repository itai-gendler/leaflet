---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The Visitor opens the new-Leaflet link
  kind: actor
  actor: visitor
  entities:
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::public
  capability: create-leaflet
- text: The Product creates the Leaflet and opens it with its title block focused
  kind: product
  actor: visitor
  entities:
  - entity: leaflet
    effect: creates
    to: Draft
    facts:
    - Title
    - Pages
    - Theme
    - Edit link
  - entity: page
    effect: creates
    facts:
    - Kind
    - Blocks
    with: leaflet
  - entity: block
    effect: creates
    facts:
    - Type
    - Position
    with: page
  contexts:
    web:
      place: leaflet-web::public::leaflet
  capability: create-leaflet
- text: The Visitor types a title into the focused block
  kind: actor
  actor: visitor
  entities:
  - entity: block
    effect: changes
    facts:
    - Content
  contexts:
    web:
      place: leaflet-web::public::leaflet
  capability: edit-block
references:
- kind: code
  role: implementation
  target: actions/createNewLeaflet.ts
---

# Open a new Leaflet and start writing

## Trigger

Someone opens leaflet.pub/new.

## Outcome

The Leaflet has its first words, saved for everyone with the link.

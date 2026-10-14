---
kind: primary
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
- text: The Product creates a Leaflet with one document page whose first block is a title heading, and opens it with that block focused
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
references:
- kind: code
  role: implementation
  target: actions/createNewLeaflet.ts
- kind: code
  role: implementation
  target: src/utils/createLeaflet.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/new/route.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/new-canvas/route.ts
---

# Create a Leaflet without an account

## Trigger

Someone without an account wants a new Leaflet.

## Outcome

A new Draft Leaflet is open for editing at its edit link, which is the only way back to it.

## Edge cases

- The Leaflet is remembered on this browser's Home, which is kept in the browser and not by Leaflet.

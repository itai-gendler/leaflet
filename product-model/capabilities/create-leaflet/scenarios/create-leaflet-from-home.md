---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to create a new document or a new canvas
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::home
- text: The Product creates the Leaflet, adds it to the User's Home and opens it
  kind: product
  actor: user
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
  - entity: home-leaflet
    effect: creates
    to: On Home
    facts:
    - Added at
    with: leaflet
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
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

# Create a document or canvas from Home

## Trigger

A signed-in User starts a new Leaflet from Home.

## Outcome

The new Leaflet is on the User's Home and open for editing; a canvas opens with one text block placed on it.

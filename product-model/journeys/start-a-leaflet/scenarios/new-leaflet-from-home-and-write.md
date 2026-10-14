---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User chooses to create a new document on Home
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::home
  capability: create-leaflet
- text: The Product creates the Leaflet on the User's Home and opens it
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
  capability: create-leaflet
- text: The User writes in the first block
  kind: actor
  actor: user
  entities:
  - entity: block
    effect: changes
    facts:
    - Content
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
  capability: edit-block
references:
- kind: code
  role: implementation
  target: actions/createNewLeaflet.ts
---

# Create a Leaflet from Home and start writing

## Trigger

A signed-in User starts a Leaflet from Home.

## Outcome

The new Leaflet is on Home with its first words.

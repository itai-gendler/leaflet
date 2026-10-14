---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor chooses New Page, New Canvas or Drawing
  kind: actor
  actor: visitor
  entities:
  - entity: page
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::public::leaflet
- text: The Product creates the new page with its first block
  kind: product
  actor: visitor
  entities:
  - entity: page
    effect: creates
    facts:
    - Kind
    - Blocks
  - entity: block
    as: first-block
    effect: creates
    facts:
    - Type
    - Position
    with: page
  contexts:
    web:
      place: leaflet-web::public::leaflet
- text: The Product adds a page-link block pointing to it and opens it beside the current one
  kind: product
  actor: visitor
  entities:
  - entity: block
    as: page-link
    effect: creates
    facts:
    - Type
    - Content
    - Position
  - entity: page
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::public::leaflet
references:
- kind: code
  role: implementation
  target: components/Blocks/BlockCommands.tsx
- kind: code
  role: implementation
  target: components/Blocks/PageLinkBlock.tsx
---

# Add a sub-page

## Trigger

A writer wants more room, a canvas or a drawing inside the Leaflet.

## Outcome

The new page opens beside the page that links to it.

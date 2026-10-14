---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses a block type at a place on the page
  kind: actor
  actor: user
  entities:
  - entity: page
    effect: reads
    facts:
    - Kind
  - entity: block
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product adds a block of that type there and focuses it
  kind: product
  actor: user
  entities:
  - entity: block
    effect: creates
    facts:
    - Type
    - Content
    - Position
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: components/Blocks/BlockCommands.tsx
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
---

# Add a block from the block menu while signed in

## Trigger

A writer wants something new on a page.

## Outcome

The new block is on the page for everyone editing the Leaflet, in real time.

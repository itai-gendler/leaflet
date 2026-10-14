---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a block
  kind: actor
  actor: user
  entities:
  - entity: block
    effect: reads
    facts:
    - Type
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product removes the block from the page
  kind: product
  actor: user
  entities:
  - entity: block
    effect: removes
  - entity: page
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: components/Blocks/DeleteBlock.tsx
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
---

# Delete a block while signed in

## Trigger

A writer no longer wants a block.

## Outcome

The block is gone for everyone; undo brings it back.

---
kind: primary
routes:
  web: Web
steps:
- text: The User drags a block, or moves it up or down
  kind: actor
  actor: user
  entities:
  - entity: block
    effect: reads
    facts:
    - Position
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product puts the block in its new place
  kind: product
  actor: user
  entities:
  - entity: block
    effect: changes
    facts:
    - Position
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
- kind: code
  role: implementation
  target: components/Blocks/ListDnd.tsx
---

# Move a block while signed in

## Trigger

A writer rearranges a page.

## Outcome

The block sits in its new place for everyone; one undo puts it back.

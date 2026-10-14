---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor drags a block, or moves it up or down
  kind: actor
  actor: visitor
  entities:
  - entity: block
    effect: reads
    facts:
    - Position
  contexts:
    web:
      place: leaflet-web::public::leaflet
- text: The Product puts the block in its new place
  kind: product
  actor: visitor
  entities:
  - entity: block
    effect: changes
    facts:
    - Position
  contexts:
    web:
      place: leaflet-web::public::leaflet
references:
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
- kind: code
  role: implementation
  target: components/Blocks/ListDnd.tsx
---

# Move a block

## Trigger

A writer rearranges a page.

## Outcome

The block sits in its new place for everyone; one undo puts it back.

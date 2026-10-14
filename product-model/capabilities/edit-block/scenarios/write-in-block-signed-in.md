---
kind: primary
routes:
  web: Web
steps:
- text: The User types, formats, links or mentions in a block
  kind: actor
  actor: user
  entities:
  - entity: block
    effect: reads
    facts:
    - Content
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product saves the change and shows it to everyone with the Leaflet open
  kind: product
  actor: user
  entities:
  - entity: block
    effect: changes
    facts:
    - Content
  - entity: leaflet
    effect: reads
    facts: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
references:
- kind: code
  role: implementation
  target: components/Blocks/TextBlock/index.tsx
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
- kind: code
  role: implementation
  target: docs/editor-behaviors.md
---

# Write in a block while signed in

## Trigger

A writer changes what a block says or holds.

## Outcome

The change is kept and appears for every collaborator; undo and redo step through it by typing runs.

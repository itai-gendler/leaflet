---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor chooses a block type at a place on the page
  kind: actor
  actor: visitor
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
      place: leaflet-web::public::leaflet
- text: The Product adds a block of that type there and focuses it
  kind: product
  actor: visitor
  entities:
  - entity: block
    effect: creates
    facts:
    - Type
    - Content
    - Position
  contexts:
    web:
      place: leaflet-web::public::leaflet
references:
- kind: code
  role: implementation
  target: components/Blocks/BlockCommands.tsx
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
---

# Add a block from the block menu

## Trigger

A writer wants something new on a page.

## Outcome

The new block is on the page for everyone editing the Leaflet, in real time.

## Edge cases

- Pasting a link to a website, a Bluesky post or a Leaflet post makes a link, Bluesky post or post block.
- Publication-only blocks are offered only in a publication's drafts and pages.

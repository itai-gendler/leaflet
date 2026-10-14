---
relations:
- entity: block
  verb: holds
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/utils/createLeaflet.ts
- kind: code
  role: implementation
  target: components/Blocks/BlockCommands.tsx
- kind: code
  role: implementation
  target: components/Canvas.tsx
---

# Page

One page of a Leaflet: the first page, or a sub-page opened beside it from a page link. A page is a document, whose blocks run in a column, or a canvas, whose blocks sit anywhere and can be zoomed.

## Information kept

- **Kind** — Document or Canvas
- **Blocks** — its blocks, in order on a document or placed and layered on a canvas

---
availability:
- place: leaflet-web::public
- place: leaflet-web::signed-in
references:
- kind: code
  role: implementation
  target: components/Blocks/DeleteBlock.tsx
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
---

# Delete a block

Remove a block from a page; removing a page link removes the sub-page it opens.

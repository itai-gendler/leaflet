---
appliesTo:
- type: entity
  id: leaflet-comment
  effect: changes
  facts:
  - Text
permits:
- related:
  - verb: authors
    entity: user
references:
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
- kind: code
  role: implementation
  target: src/replicache/attributes.ts
---

# Comments on Leaflets are written by signed-in writers with a Bluesky account, and edited only by their author

A comment and its replies carry their author's Bluesky identity; edits by anyone else are ignored.

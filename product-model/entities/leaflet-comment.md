---
domain: comments-on-leaflets
references:
- kind: code
  role: implementation
  target: src/replicache/attributes.ts
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
- kind: code
  role: implementation
  target: components/EditorComments/EditorCommentThread.tsx
---

# Comment on a Leaflet

A comment a signed-in writer anchors to a passage of a Leaflet's text, with its thread of replies. Comments live in the Leaflet beside its content.

## Information kept

- **Text** — what the comment says
- **Author** — the Bluesky account that wrote it
- **Quoted passage** — the text it is anchored to, which moves with edits
- **Replies** — the replies in its thread, each with its own text and author
- **Written at** — when it was written

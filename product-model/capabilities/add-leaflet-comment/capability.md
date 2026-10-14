---
availability:
- place: leaflet-web::signed-in
domain: comments-on-leaflets
references:
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
- kind: code
  role: implementation
  target: components/EditorComments/EditorCommentComposer.tsx
- kind: code
  role: implementation
  target: components/EditorComments/editorCommentDraftActions.ts
---

# Comment on a Leaflet

Anchor a comment to a passage of a Leaflet's text, as a signed-in writer with a Bluesky account.

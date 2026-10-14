---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Resolve comment
  kind: actor
  actor: user
  entities:
  - entity: leaflet-comment
    effect: reads
    facts:
    - Text
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product removes the comment and its replies
  kind: product
  actor: user
  entities:
  - entity: leaflet-comment
    effect: removes
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
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

# Resolve a comment thread

## Trigger

A discussion is settled.

## Outcome

The thread is gone from the Leaflet for everyone.

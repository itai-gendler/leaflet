---
kind: primary
routes:
  web: Web
steps:
- text: The User writes a reply under a comment and submits it
  kind: actor
  actor: user
  entities:
  - entity: leaflet-comment
    effect: reads
    facts:
    - Text
    - Author
    - Replies
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product adds the reply to the thread
  kind: product
  actor: user
  entities:
  - entity: leaflet-comment
    effect: changes
    facts:
    - Replies
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

# Reply in a comment thread

## Trigger

A writer answers a comment.

## Outcome

The reply shows in the thread, credited to the User.

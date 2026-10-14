---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete comment on a reply
  kind: actor
  actor: user
  entities:
  - entity: leaflet-comment
    effect: reads
    facts:
    - Replies
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product removes the reply from the thread
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

# Delete a reply

## Trigger

A writer removes a reply.

## Outcome

The thread no longer shows the reply.

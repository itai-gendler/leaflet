---
kind: primary
routes:
  web: Web
steps:
- text: The User selects a passage, or places the cursor in a word, and chooses Comment
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
- text: The User writes the comment and submits it
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product keeps the comment on the Leaflet, anchored to the passage, with the User as its author
  kind: product
  actor: user
  entities:
  - entity: leaflet-comment
    effect: creates
    facts:
    - Text
    - Author
    - Quoted passage
    - Written at
  - entity: leaflet
    effect: reads
    facts: []
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

# Comment on a passage

## Trigger

A writer wants to discuss part of a Leaflet with its other writers.

## Outcome

Everyone editing the Leaflet sees the comment beside the passage it is anchored to.

## Edge cases

- Signed-out writers are asked to log in before commenting.
- Deleting the commented text removes the comment and its replies.

---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Edit comment on a comment they wrote and saves new text
  kind: actor
  actor: user
  entities:
  - entity: leaflet-comment
    effect: reads
    facts:
    - Text
    - Author
  contexts:
    web:
      place: leaflet-web::signed-in::leaflet
- text: The Product replaces the comment's text
  kind: product
  actor: user
  entities:
  - entity: leaflet-comment
    effect: changes
    facts:
    - Text
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

# Edit one's own comment

## Trigger

A writer corrects something they commented.

## Outcome

The comment shows its new text.

## Edge cases

- Edits to someone else's comment or reply are ignored.

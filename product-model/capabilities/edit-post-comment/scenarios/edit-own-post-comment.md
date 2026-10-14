---
kind: primary
routes:
  web: Web
steps:
- text: The User edits a comment they wrote
  kind: actor
  actor: user
  entities:
  - entity: post-comment
    effect: reads
    facts:
    - Text
  contexts:
    web:
      place: leaflet-web::signed-in::post
- text: The Product saves the new text
  kind: product
  actor: user
  entities:
  - entity: post-comment
    effect: changes
    facts:
    - Text
  contexts:
    web:
      place: leaflet-web::signed-in::post
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/Interactions/Comments/commentAction.ts
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/Interactions/Comments/CommentBox.tsx
---

# Edit one's comment

## Trigger

A reader corrects their comment.

## Outcome

The comment shows its new text.

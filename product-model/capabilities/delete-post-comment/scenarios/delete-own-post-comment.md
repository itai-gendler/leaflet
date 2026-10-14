---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a comment they wrote
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
- text: The Product deletes it; replies keep their place under a placeholder
  kind: product
  actor: user
  entities:
  - entity: post-comment
    effect: removes
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
- kind: code
  role: implementation
  target: src/comments/tombstoneComment.ts
---

# Delete one's comment

## Trigger

A reader withdraws a comment.

## Outcome

The comment no longer counts or shows; its replies remain.

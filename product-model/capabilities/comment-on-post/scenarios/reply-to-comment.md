---
kind: primary
routes:
  web: Web
steps:
- text: The User replies to a comment
  kind: actor
  actor: user
  entities:
  - entity: post-comment
    as: parent
    effect: reads
    facts:
    - Text
  contexts:
    web:
      place: leaflet-web::signed-in::post
- text: The Product saves the reply under it and notifies the comment's author
  kind: product
  actor: user
  entities:
  - entity: post-comment
    as: reply
    effect: creates
    facts:
    - Text
    - In reply to
    - Posted at
  - entity: notification
    effect: creates
    to: Unread
    facts:
    - Kind
    - Subject
    - Created at
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

# Reply to a comment

## Trigger

A reader answers another reader.

## Outcome

The reply is threaded under the comment.

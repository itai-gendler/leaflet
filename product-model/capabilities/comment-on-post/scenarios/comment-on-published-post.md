---
kind: primary
routes:
  web: Web
steps:
- text: The User writes a comment, optionally quoting a highlighted passage, and posts it
  kind: actor
  actor: user
  entities:
  - entity: post
    effect: reads
    facts:
    - Post settings
  contexts:
    web:
      place: leaflet-web::signed-in::post
- text: The Product saves the comment in the User's Bluesky account, shows it on the post and notifies the post's author and anyone mentioned
  kind: product
  actor: user
  entities:
  - entity: post-comment
    effect: creates
    facts:
    - Text
    - Quoted passage
    - Posted at
  - entity: notification
    effect: creates
    to: Unread
    facts:
    - Kind
    - Subject
    - Created at
  - entity: post
    effect: reads
    facts: []
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

# Comment on a post

## Trigger

A reader responds to a post.

## Outcome

The comment appears in the post's discussion.

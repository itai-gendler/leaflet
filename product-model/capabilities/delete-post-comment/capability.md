---
availability:
- place: leaflet-web::signed-in
domain: reader
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

# Delete a comment

Delete one's own comment on a post; replies to it stay under a placeholder.

---
appliesTo:
- type: entity
  id: post-comment
  effect: removes
permits:
- related:
  - verb: writes
    entity: user
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/Interactions/Comments/commentAction.ts
- kind: code
  role: implementation
  target: src/comments/tombstoneComment.ts
---

# Only a comment's author deletes it

A deleted comment leaves a placeholder that keeps its replies threaded.

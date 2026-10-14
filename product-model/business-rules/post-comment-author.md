---
appliesTo:
- type: entity
  id: post-comment
  effect: changes
permits:
- related:
  - verb: writes
    entity: user
references:
- kind: code
  role: implementation
  target: app/(app)/(published)/lish/[did]/[publication]/[rkey]/Interactions/Comments/commentAction.ts
---

# Only a comment's author edits or deletes it

Comments live in their author's Bluesky account; only the author changes or removes them.

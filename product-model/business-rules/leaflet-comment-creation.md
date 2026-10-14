---
appliesTo:
- type: entity
  id: leaflet-comment
  effect: creates
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Bluesky account
    present: true
references:
- kind: code
  role: implementation
  target: src/replicache/mutations.ts
- kind: code
  role: implementation
  target: components/EditorComments/EditorCommentLoginPrompt.tsx
---

# Signed-in writers with a Bluesky account comment on Leaflets

Writers who are signed out, or signed in by email only, are asked to log in with Bluesky to comment.

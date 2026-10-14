---
appliesTo:
- type: entity
  id: post-comment
  effect: creates
- type: capability
  id: recommend-post
- type: capability
  id: vote-in-post-poll
references:
- kind: code
  role: implementation
  target: actions/recommendAction.ts
---

# Commenting, recommending and voting on published posts need a Bluesky account

Comments, recommends and published poll votes are records in the reader's own Bluesky account.

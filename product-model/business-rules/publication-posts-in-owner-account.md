---
appliesTo:
- type: capability
  id: publish-post
- type: capability
  id: update-post
- type: capability
  id: unpublish-post
- type: entity
  id: post
references:
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
- kind: code
  role: implementation
  target: src/atproto-oauth.ts
---

# A publication's posts live in its owner's Bluesky account

Contributors publish, update and delete posts through the owner's account; when the owner's Bluesky sign-in has expired, nobody can publish until the owner signs in again.

---
appliesTo:
- type: entity
  id: publication
  effect: removes
permits:
- related:
  - verb: owns
    entity: user
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/settings/deletePublication.ts
---

# Only a publication's owner deletes it

Deleting removes the publication, its posts and its drafts; only the owner may.

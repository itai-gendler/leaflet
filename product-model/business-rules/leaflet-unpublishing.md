---
appliesTo:
- type: entity
  id: leaflet
  effect: changes
  from: Published
permits:
- related:
  - verb: is published as
    entity: post
  - verb: publishes
    entity: user
- related:
  - verb: holds draft
    entity: publication
  - verb: owns
    entity: user
- related:
  - verb: holds draft
    entity: publication
  - verb: has
    entity: contributor
  - verb: holds
    entity: user
  when:
  - entity: contributor
    fact: Accepted
    is: true
references:
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/deletePost.ts
---

# A published Leaflet returns to a draft only by its author or its publication's owner and accepted contributors

Unpublishing turns a Looseleaf back into a Leaflet and a publication post back into a draft.

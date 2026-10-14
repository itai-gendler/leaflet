---
appliesTo:
- type: entity
  id: post
  effect: creates
permits:
- related:
  - verb: publishes
    entity: user
  when:
  - entity: user
    fact: Bluesky account
    present: true
- related:
  - verb: has
    entity: publication
  - verb: owns
    entity: user
- related:
  - verb: has
    entity: publication
  - verb: has
    entity: contributor
  - verb: holds
    entity: user
  when:
  - entity: contributor
    fact: Accepted
    is: true
- unattended: true
  when:
  - entity: publication
    fact: Pro features
    is: true
references:
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
- kind: code
  role: implementation
  target: app/(app)/(identity)/lish/[did]/[publication]/dashboard/deletePost.ts
- kind: code
  role: implementation
  target: src/contributorPermissions.ts
---

# Posts are published by their author, or in a publication by its owner and accepted contributors

A Looseleaf is published by its author with their Bluesky account. A publication's posts are published by its owner or an accepted contributor — always into the owner's Bluesky account — or by the Product when a scheduled post's time comes while the owner holds Leaflet Pro.

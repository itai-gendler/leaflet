---
appliesTo:
- type: entity
  id: post
  effect: removes
permits:
- related:
  - verb: publishes
    entity: user
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

# A post's author, its publication's owner and accepted contributors unpublish or delete it

Anyone else, even holding the draft's edit link, is told they are not authorized to modify the post.

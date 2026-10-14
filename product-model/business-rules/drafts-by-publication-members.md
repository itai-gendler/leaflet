---
appliesTo:
- type: entity
  id: leaflet
  effect: creates
  to: Publication draft
permits:
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
  target: actions/createPublicationDraft.ts
- kind: code
  role: implementation
  target: actions/publications/moveLeafletToPublication.ts
---

# A publication's owner and accepted contributors create its drafts

Drafts are started in a publication, or moved into it, by its owner or by contributors who have accepted.

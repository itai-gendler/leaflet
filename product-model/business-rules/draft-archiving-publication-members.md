---
appliesTo:
- type: entity
  id: leaflet
  effect: changes
  facts:
  - Archived in publication
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
  target: actions/deleteLeaflet.ts
---

# A publication's owner and accepted contributors archive its drafts

Archiving a draft from Home also archives it in the publication's drafts only for its owner and accepted contributors.

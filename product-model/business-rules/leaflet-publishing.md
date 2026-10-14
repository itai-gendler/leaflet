---
appliesTo:
- type: entity
  id: leaflet
  effect: changes
  to: Published
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Bluesky account
    present: true
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
- unattended: true
references:
- kind: code
  role: implementation
  target: src/utils/publishLeaflet.ts
- kind: code
  role: implementation
  target: actions/publishToPublication.ts
---

# A Leaflet is published by its author, or as a publication draft by the publication's owner and accepted contributors

A standalone Leaflet is published as a Looseleaf by the signed-in person publishing it, with their Bluesky account; a publication draft by the publication's owner or an accepted contributor, or by the Product when its scheduled time comes.

---
appliesTo:
- type: entity
  id: leaflet
  effect: removes
permits:
- actors:
  - visitor
  - user
  when:
  - state: Draft
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
- related:
  - verb: is published as
    entity: post
  - verb: publishes
    entity: user
references:
- kind: code
  role: implementation
  target: actions/deleteLeaflet.ts
---

# Unpublished Leaflets are deleted by anyone with the edit link; drafts and published Leaflets by their publication's members or author

A standalone Leaflet that was never published is deleted by whoever holds its edit link. A publication's draft is deleted by its owner or an accepted contributor. A published Looseleaf's Leaflet is deleted only by its author.

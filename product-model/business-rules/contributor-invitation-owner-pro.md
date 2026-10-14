---
appliesTo:
- type: entity
  id: contributor
  effect: creates
permits:
- related:
  - verb: has
    entity: publication
  - verb: owns
    entity: user
  when:
  - entity: user
    fact: Leaflet Pro
    is: true
references:
- kind: code
  role: implementation
  target: actions/publications/contributors.ts
- kind: code
  role: implementation
  target: src/contributorPermissions.ts
---

# Only a publication's owner with Leaflet Pro invites contributors

Group publications are a Leaflet Pro feature of the owner; invitees never need Leaflet Pro to accept.

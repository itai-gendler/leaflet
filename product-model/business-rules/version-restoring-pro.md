---
appliesTo:
- type: entity
  id: leaflet
  effect: changes
  facts:
  - Pages
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Leaflet Pro
    is: true
references:
- kind: code
  role: implementation
  target: actions/versions.ts
- kind: code
  role: implementation
  target: src/versioning/versionAccess.ts
- kind: code
  role: implementation
  target: src/versioning/cutPublishVersion.ts
---

# Only writers holding Leaflet Pro restore a version into a Leaflet

Restoring replaces the Leaflet's pages with a version's and is a Leaflet Pro feature of the person restoring.

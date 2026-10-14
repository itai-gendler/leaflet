---
appliesTo:
- type: entity
  id: leaflet-version
  effect: creates
  facts:
  - Name
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

# Only writers holding Leaflet Pro save named versions

Saving a version is a Leaflet Pro feature of the person saving.
